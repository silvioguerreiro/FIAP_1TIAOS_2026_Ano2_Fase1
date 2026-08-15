# Dicionário de Dados — `data/dataset_cardiaco.csv`

**Projeto CardioIA — Fase 1 "Batimentos de Dados" | Parte 1 — Dados Numéricos (IoT)**

| Característica | Valor |
|---|---|
| Registros (linhas) | **303 pacientes** (atende ao mínimo de 100 exigido pelo enunciado) |
| Variáveis (colunas) | 15 (14 originais + `id_paciente` adicionado na curadoria) |
| Formato | `.csv`, codificação UTF-8, separador vírgula, decimal ponto |
| Origem | **Real** — UCI Machine Learning Repository, *Heart Disease* (subconjunto Cleveland Clinic Foundation), DOI [10.24432/C52P4X](https://doi.org/10.24432/C52P4X), licença CC BY 4.0 |
| Valores ausentes | 6 células em 6 pacientes: 4 em `num_vasos_principais`, 2 em `talassemia` (células vazias no CSV) |

## 1. Variáveis

| # | Variável | Tipo | Unidade / Codificação | Faixa observada | Significado clínico |
|---|---|---|---|---|---|
| 1 | `id_paciente` | inteiro | identificador sequencial (1–303) | 1–303 | Chave de referência criada na curadoria; **não** é identificador real de paciente (dados anonimizados na origem) |
| 2 | `idade` | inteiro | anos | 29–77 (média 54,4) | Idade do paciente; fator de risco cardiovascular não modificável |
| 3 | `sexo` | categórica binária | 1 = masculino; 0 = feminino | 0–1 (206 M / 97 F) | Sexo biológico; homens têm risco coronariano mais precoce |
| 4 | `tipo_dor_toracica` | categórica | 1 = angina típica; 2 = angina atípica; 3 = dor não anginosa; 4 = assintomático | 1–4 | Caracterização do sintoma de apresentação; central na probabilidade pré-teste de doença arterial coronariana (DAC) |
| 5 | `pressao_arterial_repouso` | inteiro | mmHg (sistólica, em repouso, na admissão) | 94–200 (média 131,7) | Hipertensão arterial é o principal fator de risco modificável para DAC e AVC |
| 6 | `colesterol_serico` | inteiro | mg/dL | 126–564 (média 246,7) | Colesterol total; dislipidemia associa-se à aterosclerose coronariana |
| 7 | `glicemia_jejum_maior_120` | categórica binária | 1 = glicemia de jejum > 120 mg/dL; 0 = ≤ 120 | 0–1 | Proxy de disglicemia/diabetes, fator de risco cardiovascular relevante |
| 8 | `ecg_repouso` | categórica | 0 = normal; 1 = anormalidade de onda ST-T; 2 = hipertrofia ventricular esquerda provável/definitiva (critérios de Estes) | 0–2 | Alterações elétricas basais do miocárdio em repouso |
| 9 | `freq_cardiaca_maxima` | inteiro | bpm (máxima atingida no teste de esforço) | 71–202 (média 149,6) | Resposta cronotrópica ao exercício; valores baixos associam-se a pior prognóstico |
| 10 | `angina_induzida_exercicio` | categórica binária | 1 = sim; 0 = não | 0–1 | Angina desencadeada pelo esforço sugere isquemia miocárdica |
| 11 | `depressao_st_exercicio` | decimal | mm (depressão do segmento ST no esforço em relação ao repouso; "oldpeak") | 0,0–6,2 (média 1,0) | Magnitude da alteração isquêmica ao esforço; quanto maior, mais sugestiva de DAC obstrutiva |
| 12 | `inclinacao_st` | categórica | 1 = ascendente; 2 = plana; 3 = descendente | 1–3 | Morfologia do segmento ST no pico do esforço; padrões plano/descendente são mais patológicos |
| 13 | `num_vasos_principais` | inteiro | 0–3 vasos principais visualizados por fluoroscopia | 0–3 (4 ausentes) | Extensão anatômica do acometimento coronariano |
| 14 | `talassemia` | categórica | 3 = normal; 6 = defeito fixo; 7 = defeito reversível | 3, 6, 7 (2 ausentes) | Resultado da cintilografia de perfusão com tálio: defeito reversível sugere isquemia; fixo sugere fibrose/infarto prévio |
| 15 | `diagnostico_dac` | categórica ordinal (alvo) | 0 = ausência de estenose ≥ 50%; 1–4 = presença de DAC angiográfica em gradação crescente de extensão/gravidade | 0–4 (0: 164; 1: 55; 2: 36; 3: 35; 4: 13) | **Variável-alvo**: diagnóstico angiográfico de DAC; na literatura é frequentemente binarizada (0 = sem doença; ≥ 1 = com doença) |

## 2. Transformações aplicadas na curadoria (rastreabilidade)

1. Renomeação das colunas originais (inglês → português técnico, minúsculas, sem acentos):

   `age→idade`, `sex→sexo`, `cp→tipo_dor_toracica`, `trestbps→pressao_arterial_repouso`, `chol→colesterol_serico`, `fbs→glicemia_jejum_maior_120`, `restecg→ecg_repouso`, `thalach→freq_cardiaca_maxima`, `exang→angina_induzida_exercicio`, `oldpeak→depressao_st_exercicio`, `slope→inclinacao_st`, `ca→num_vasos_principais`, `thal→talassemia`, `num→diagnostico_dac`.
2. Inclusão da coluna `id_paciente` (1–303, preservando a ordem original dos registros).
3. Valores ausentes originais (`?`) convertidos em células vazias; nenhuma imputação foi realizada (a decisão de tratamento fica para a fase de modelagem — Fase 2 do CardioIA).
4. Conversão de tipos: variáveis de valores inteiros armazenadas como inteiros; `depressao_st_exercicio` mantida como decimal.
5. Nenhuma linha foi removida, adicionada ou alterada em seus valores clínicos; o arquivo-fonte original (*processed.cleveland.data*) é preservado na pasta local de apoio do projeto, fora do repositório público, com hash SHA-256 registrado em `proveniencia_e_licencas.md`.

## 3. Variáveis de maior relevância clínica (síntese)

Justificativa detalhada no `README.md`. Em síntese, as variáveis de maior valor para um sistema de triagem/diagnóstico assistido por IA neste dataset são: **tipo_dor_toracica** (probabilidade pré-teste de DAC), **depressao_st_exercicio** e **freq_cardiaca_maxima** (resposta isquêmica ao esforço), **colesterol_serico** e **pressao_arterial_repouso** (fatores de risco modificáveis), além de **idade** e **sexo** (base de qualquer escore de risco cardiovascular).

## 4. Limitações e vieses conhecidos (síntese)

Coorte de um único centro (Cleveland Clinic Foundation, EUA, década de 1980), com predomínio masculino (68%) e sem representação de população brasileira; detalhes e mitigações na seção de Governança do `README.md` e em `docs/proveniencia_e_licencas.md`.
