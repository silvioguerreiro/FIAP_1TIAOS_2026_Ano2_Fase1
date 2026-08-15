# Proveniência e Licenças — CardioIA Fase 1

Registro de proveniência, licenciamento e integridade de todos os dados incorporados ao projeto, conforme boas práticas de governança de dados em IA e LGPD (Lei nº 13.709/2018). Curadoria realizada em **15/08/2026**.

## Matriz consolidada

| Conjunto | Parte | Fonte original | Versão / DOI | Data de acesso | Licença (verificada) | Status |
|---|---|---|---|---|---|---|
| `data/dataset_cardiaco.csv` (303×15) | 1 — Numéricos | UCI ML Repository — *Heart Disease* (Cleveland) | DOI 10.24432/C52P4X (doado em 30/06/1988) | 15/08/2026 | **CC BY 4.0** — confirmada na página oficial da UCI | ✔ Incorporado |
| `docs/texto_01_doencas_cardiovasculares_revisao.txt` | 2 — Textuais | RCMOS — Revista Científica Multidisciplinar O Saber (ISSN 2675-9128), ano VII, v. 1, 2026 | DOI 10.51473/rcmos.v1i1.2026.2623 | 15/08/2026 | **CC BY** — declarada no PDF oficial e na página do periódico | ✔ Incorporado |
| `docs/texto_02_arritmias_cardiacas.txt` | 2 — Textuais | Brazilian Journal of Implantology and Health Sciences, v. 6, n. 2, p. 348-360, 2024 | DOI 10.36557/2674-8169.2024v6n2p348-360 | 15/08/2026 | **CC BY 4.0** — confirmada na página oficial do artigo | ✔ Incorporado |
| `images/acervo_angiogramas/` (120 png) | 3 — Visuais | Dataset ARCADE (desafio MICCAI 2023) | Zenodo DOI 10.5281/zenodo.8386059; artigo: DOI 10.1038/s41597-023-02871-z | 15/08/2026 | **CC0 1.0** (domínio público) — confirmada no registro Zenodo | ✔ Incorporado |

## Parte 1 — Dataset numérico (detalhamento)

- **Dataset:** Heart Disease — subconjunto *processed.cleveland.data* (Cleveland Clinic Foundation). **Repositório:** UCI Machine Learning Repository — https://archive.ics.uci.edu/dataset/45/heart+disease · DOI https://doi.org/10.24432/C52P4X (doado em 30/06/1988).
- **Criadores:** Andras Janosi (Hungarian Institute of Cardiology), William Steinbrunn (University Hospital Zurich), Matthias Pfisterer (University Hospital Basel), Robert Detrano (Cleveland Clinic Foundation / V.A. Medical Center Long Beach).
- **Licença:** CC BY 4.0 — licença e nº de instâncias (303) confirmados na página oficial da UCI em 15/08/2026.
- **Método de obtenção e integridade:** o acesso HTTP direto ao servidor da UCI não estava disponível no ambiente de execução; o arquivo foi obtido de espelho público (GitHub: `reinaldoq/processing-heart-disease-dataset`, acesso em 15/08/2026) e **validado contra 12 características canônicas publicadas** — todas confirmadas: 303 registros × 14 atributos; exatamente 6 ausentes (`?`): 4 em `ca`, 2 em `thal`; distribuição do alvo `num` 0:164/1:55/2:36/3:35/4:13; sexo 206M/97F; idade 29–77; PA 94–200 mmHg; colesterol 126–564 mg/dL; FC máx. 71–202 bpm; oldpeak máx. 6,2.
- **Hashes SHA-256:** arquivo-fonte original (*processed.cleveland.data*, EOL normalizado; cópia preservada na pasta local de apoio do projeto, fora do repositório público) `511ffcd8893a233084ebd79e950be9b1b07b1357bdde77bd0ab39d1064082641`; curado (`dataset_cardiaco.csv`) `a57734d3308aff216f87903a331cd56572c62ff19cb638830183a6e7331a9c5d`.
- **Transformações:** documentadas integralmente em `dicionario_de_dados.md` (renomeação EN→PT, `id_paciente`, `?`→vazio sem imputação, tipagem). Nenhum valor clínico alterado.

## Parte 2 — Corpus textual (detalhamento)

**Textos incorporados (2):** extração automática de texto (pdftotext/UTF-8) a partir dos PDFs oficiais de acesso aberto, com remoção apenas de cabeçalhos/rodapés repetidos de página e números de página; conteúdo integral preservado; cabeçalho interno de proveniência em cada `.txt` (título, autoria, fonte, URL, DOI, data de publicação, data de acesso/extração, licença).

**Documentos avaliados e NÃO redistribuídos (decisão de governança):** quatro documentos coletados na fase de pesquisa não apresentam declaração explícita de licença de redistribuição e, por integridade acadêmica e respeito a direitos autorais, **não** foram convertidos nem incluídos no repositório:

1. SANTOS, L. P. R. dos — *Acesso à saúde como direito social e a mortalidade cardiovascular no mundo* (monografia de especialização, USP);
2. KOGA, G. J. V. et al. — *Doenças Cardíacas Principais* (capítulo de livro, DOI 10.59290/1302281202);
3. LIMA, K. M. de — *Doenças cardiovasculares: prevenção e controle da hipertensão arterial sistêmica* (TCC, 2025);
4. SANTOS-FILHO, S. D. — *Interesse Científico em Saúde Cardiovascular e Reabilitação Cardíaca* (Revista de Saúde de Vassouras, 2010).

Esses materiais permanecem apenas como leitura de apoio na pasta local de pesquisa, fora do repositório público.

## Parte 3 — Acervo de imagens (detalhamento)

- **Dataset-fonte:** ARCADE — *Automatic Region-based Coronary Artery Disease diagnostics using x-ray angiography imagEs* (desafio MICCAI 2023). 3.000 frames de angiografia coronariana por raios X, 512×512 px, anonimizados na origem; anotações de segmentação de vasos (metodologia SYNTAX) e de detecção de estenose criadas e validadas de forma cruzada por cardiologistas experientes (ferramenta CVAT). Pacientes de 19–90 anos do Research Institute of Cardiology and Internal Diseases (Almaty, Cazaquistão); angiógrafos Philips Azurion 3 e Siemens Artis Zee.
- **Licença:** **CC0 1.0 Universal (domínio público)** — confirmada no registro Zenodo (DOI 10.5281/zenodo.8386059) em 15/08/2026. Artigo de referência: Popov et al., *Scientific Data*, v. 11, art. 20, 2024 (DOI 10.1038/s41597-023-02871-z).
- **Cópia utilizada:** download prévio do espelho público do dataset (pacote com partições stenosis/syntax — train/val/test, 3.000 png no total), conferido localmente contra a descrição oficial (contagens e resolução).
- **Curadoria (critério de seleção):** **determinístico e reprodutível** — as 120 primeiras imagens, em ordem numérica do identificador original, da partição `train` da tarefa **stenosis**; renomeadas `img_0001.png`–`img_0120.png`. Rastreabilidade completa em `docs/mapeamento_imagens.csv` (novo nome ↔ nome original ↔ subconjunto/partição), preservando o vínculo com as anotações oficiais do dataset-fonte para uso na Fase 4. Amostra de 8 imagens em `images/amostra/`.
- **Verificação técnica local:** PNG, 512 × 512 px, 8-bit RGB (conferido por inspeção de arquivo).

## Enquadramento LGPD (todos os conjuntos)

- Dados de saúde são **dados pessoais sensíveis** (art. 5º, II, LGPD). O projeto utiliza exclusivamente dados **públicos e anonimizados na origem** — sem nomes, documentos, datas de nascimento ou identificadores diretos/indiretos de pacientes reais. `id_paciente` (Parte 1) é sequencial sintético criado na curadoria.
- Finalidade: exclusivamente acadêmica (FIAP/PBL — Projeto CardioIA), com minimização (somente os campos/arquivos necessários), transparência (este registro público de proveniência) e atribuição conforme cada licença.
