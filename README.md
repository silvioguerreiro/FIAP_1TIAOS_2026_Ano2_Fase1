# FIAP - Faculdade de Informática e Administração Paulista

<p align="center">
<a href= "https://www.fiap.com.br/"><img src="assets/logo-fiap.png" alt="FIAP - Faculdade de Informática e Admnistração Paulista" border="0" width=40% height=40%></a>
</p>

<br>

# CardioIA — Fase 1: Batimentos de Dados 🫀

## Grupo 50

## 👨‍🎓 Integrantes:
- <a href="https://www.linkedin.com/in/silvio-guerreiro">Silvio Prestes Guerreiro Junior — RM567958</a>

## 👩‍🏫 Professores
- **Tutor(a):** [Sabrina Otoni](https://www.linkedin.com/company/inova-fusca)
- **Coordenador(a):** [André Godoi Chiovato](https://www.linkedin.com/company/inova-fusca)

## 📜 Descrição

O **CardioIA** é um projeto acadêmico que simula o ecossistema de uma cardiologia moderna: uma plataforma digital inteligente que integra dados clínicos, modelos de Machine Learning, Visão Computacional, IoT e agentes inteligentes para triagem, diagnóstico, monitoramento, assistência remota e previsão de eventos cardíacos. O contexto justifica o esforço: as doenças cardiovasculares são a principal causa de morte no mundo — cerca de **17,9 milhões de óbitos anuais** — e boa parte desses desfechos é evitável com diagnóstico precoce, frente em que a Inteligência Artificial tem potencial transformador.

Esta **Fase 1 — "Batimentos de Dados: Mapeando o Coração Moderno"** assume o papel de cientista de dados hospitalar e constrói a base de todo o ecossistema: levantar, organizar, documentar e entender os três tipos de dados que alimentarão os módulos inteligentes das fases seguintes — **numéricos (IoT)**, **textuais (NLP)** e **visuais (Visão Computacional)** — sempre sob os princípios de **Governança de Dados e LGPD**.

Cada conjunto foi selecionado já pensando na jornada completa do projeto. Os **dados numéricos** são reais, provenientes do dataset *Heart Disease* (subconjunto Cleveland) do UCI Machine Learning Repository: 303 pacientes com variáveis de anamnese, exame físico e teste de esforço, com colunas traduzidas para português técnico e dicionário de dados completo — insumo direto para os classificadores de risco da Fase 2 e análogo aos sinais que os wearables da Fase 3 capturarão. Os **dados textuais** são dois artigos científicos brasileiros de acesso aberto, um sobre doenças cardiovasculares e outro sobre arritmias, ricos em sintomas, exames e tratamentos — vocabulário clínico essencial ao assistente virtual da Fase 5. Os **dados visuais** são 120 angiogramas coronarianos do dataset ARCADE (desafio MICCAI 2023), anonimizados e anotados por cardiologistas, que sustentam a detecção de estenoses da Fase 4.

Um princípio orientou toda a curadoria: **rastreabilidade e licenciamento verificados**. Todo dado incorporado tem fonte, DOI, data de acesso e licença conferida na origem (CC BY 4.0, CC BY e CC0), com verificação de integridade por hash e critério de seleção documentado. Coerente com isso, quatro documentos coletados durante a pesquisa foram deliberadamente **não redistribuídos** por não apresentarem licença explícita — decisão registrada na seção de Governança. Nenhum dado pessoal identificável de paciente real é utilizado: todos os conjuntos são públicos e anonimizados na origem, conforme exige o tratamento de dados sensíveis de saúde previsto na LGPD.

### Resumo da entrega

| Item | Exigência mínima do enunciado | Entregue | Localização |
|---|---|---|---|
| Parte 1 — Dados numéricos (IoT) | Dataset com ≥ 100 linhas, formato .csv ou .xlsx | **303 pacientes × 15 variáveis**, .csv UTF-8, dados reais (UCI, CC BY 4.0) | [`data/`](data/) — Seção "Parte 1" |
| Parte 2 — Dados textuais (NLP) | ≥ 2 textos .txt em subpasta `docs` ou `assets` | **2 artigos científicos** de acesso aberto (CC BY) em .txt, com proveniência | [`docs/`](docs/) — Seção "Parte 2" |
| Parte 3 — Dados visuais (VC) | ≥ 100 imagens .jpg/.png de um tipo de exame | **120 angiogramas** .png 512×512 (ARCADE, CC0) | [`images/acervo_angiogramas/`](images/acervo_angiogramas/) — Seção "Parte 3" |
| Documento-resumo | README.md detalhado, claro e estruturado | **Este documento** | raiz do repositório |
| Governança de Dados e viés | Conceitos de governança e viés aplicados aos dados | Seção dedicada + matriz de proveniência | [`docs/proveniencia_e_licencas.md`](docs/proveniencia_e_licencas.md) |
| Notebooks futuros (dica) | Pasta reservada para Colab/Jupyter | Criada | [`notebooks/`](notebooks/) |

### 🔗 Links públicos da entrega (OneDrive, acesso somente exibição)

- **Conjunto completo de dados:** [pasta `cardioia-fase1`](https://1drv.ms/f/c/a655986124216a70/IgCkUuM5o4JfRY_NNLsD8aptAfYoPid-hPTF5rJcJUy6owk?e=gaRjyU)
- **Dados numéricos (Parte 1):** [pasta `data`](https://1drv.ms/f/c/a655986124216a70/IgAU5LQqEtMfTr-a4dDLN3chAXBdb6R1mbrNvFhW20KK4Kk?e=hZBFzG)
- **Dados visuais (Parte 3):** [pasta `images`](https://1drv.ms/f/c/a655986124216a70/IgCFUMdnwJGPQL5s6l-CK7b4AdgMfkNIBHMLjAg_UnQU1IQ?e=JEvC2c)

---

## 🩺 Parte 1 — Dados Numéricos (IoT)

- **Arquivo:** [`data/dataset_cardiaco.csv`](data/dataset_cardiaco.csv) — **303 pacientes × 15 variáveis** (mínimo exigido: 100 linhas), CSV UTF-8.
- **Origem: dados REAIS** — UCI Machine Learning Repository, dataset *Heart Disease*, subconjunto Cleveland Clinic Foundation. Licença **CC BY 4.0**, DOI [10.24432/C52P4X](https://doi.org/10.24432/C52P4X). A verificação de integridade da fonte (12 checagens canônicas + hashes SHA-256) está documentada em [`docs/proveniencia_e_licencas.md`](docs/proveniencia_e_licencas.md).
- **Dicionário de dados completo:** [`docs/dicionario_de_dados.md`](docs/dicionario_de_dados.md) — tipo, unidade, faixa e significado clínico de cada variável, além da rastreabilidade de todas as transformações (tradução de colunas, `id_paciente`, tratamento de ausentes sem imputação).

### Variáveis de maior relevância clínica (justificativa)

1. **`tipo_dor_toracica`** — a caracterização da dor torácica (típica, atípica, não anginosa, assintomática) é o ponto de partida das diretrizes para estimar a probabilidade pré-teste de doença arterial coronariana (DAC). Para o sistema de **triagem digital** do CardioIA, é a variável de anamnese com maior poder discriminativo isolado.
2. **`depressao_st_exercicio` (com `inclinacao_st`)** — a depressão do segmento ST induzida por esforço é o marcador eletrocardiográfico clássico de isquemia miocárdica; quanto maior (0,0–6,2 mm no dataset), maior a suspeita de DAC obstrutiva. Informação de alto valor para os modelos de **diagnóstico assistido** da Fase 2.
3. **`freq_cardiaca_maxima`** — a resposta cronotrópica ao esforço resume a reserva funcional cardiovascular; valores reduzidos associam-se a doença mais grave. Com `angina_induzida_exercicio`, descreve o comportamento do coração sob estresse — exatamente o tipo de sinal que os sensores vestíveis da **Fase 3 (IoT)** capturarão em tempo real.
4. **`pressao_arterial_repouso` e `colesterol_serico`** — os dois grandes fatores de risco **modificáveis** da aterosclerose, base de escores populacionais (ex.: Framingham); permitem à plataforma gerar alertas preventivos e recomendações personalizadas.
5. **`idade` e `sexo`** — estratificam o risco basal em qualquer escore cardiovascular e são indispensáveis à **análise de viés e representatividade** dos modelos (seção de Governança).

A variável-alvo **`diagnostico_dac`** (0 = sem estenose ≥ 50%; 1–4 = DAC em gradação crescente) permite treinar tanto classificadores binários de triagem quanto modelos ordinais de gravidade.

## 📚 Parte 2 — Dados Textuais (NLP)

Dois artigos científicos **em acesso aberto com licença Creative Commons Attribution verificada**, extraídos para `.txt` (UTF-8) com cabeçalho interno de proveniência (título, autoria, fonte, URL, DOI, datas e licença):

| Arquivo | Conteúdo | Fonte |
|---|---|---|
| [`docs/texto_01_doencas_cardiovasculares_revisao.txt`](docs/texto_01_doencas_cardiovasculares_revisao.txt) | Revisão narrativa das DCVs: fatores de risco, fisiopatologia (aterosclerose, IAM), prevenção, diagnóstico e tratamento (~3.100 palavras) | RCMOS (ISSN 2675-9128), 2026, CC BY |
| [`docs/texto_02_arritmias_cardiacas.txt`](docs/texto_02_arritmias_cardiacas.txt) | Revisão sobre arritmias: diagnóstico (ECG, Holter), tratamento (ablação, antiarrítmicos), prevenção e tecnologias (wearables, telemedicina) (~4.000 palavras) | BJIHS, v. 6, n. 2, 2024, CC BY 4.0 |

**Nota de governança:** outros quatro documentos coletados na pesquisa (dois TCCs e dois capítulos/artigos) **não** foram redistribuídos neste repositório por não apresentarem licença explícita de redistribuição — decisão registrada em [`docs/proveniencia_e_licencas.md`](docs/proveniencia_e_licencas.md).

### Potencial de exploração por NLP (justificativa)

- **Extração de entidades clínicas (NER):** os dois textos são ricos em doenças (IAM, insuficiência cardíaca, fibrilação atrial), sintomas (dor torácica, palpitações, síncope, dispneia), exames (ECG, Holter, ecocardiograma) e tratamentos (ablação por cateter, antiarrítmicos, anti-hipertensivos) — vocabulário essencial para o **assistente cardiológico virtual da Fase 5** reconhecer queixas de pacientes e responder com terminologia correta.
- **Classificação de tópicos:** as seções naturais dos artigos (fatores de risco → diagnóstico → tratamento → prevenção) fornecem material rotulável para classificar mensagens de pacientes por intenção (dúvida sobre sintoma × medicação × prevenção), roteando o atendimento na plataforma.
- **Sumarização e base de conhecimento (RAG):** os textos podem ancorar respostas do chatbot em conteúdo científico citável, reduzindo alucinação — prática recomendada em IA responsável para saúde.
- **Análise de sentimentos:** a técnica, exemplificada no enunciado, será aplicável na Fase 5 aos **relatos de pacientes** coletados pela plataforma; o corpus atual fornece o vocabulário clínico de referência para calibrar esse pipeline.
- **Mineração de relações sintoma–doença–tratamento:** o texto de arritmias conecta explicitamente achados de exame a condutas — insumo para grafos de conhecimento que apoiam a **previsão de crises da Fase 6**.

## 🫀 Parte 3 — Dados Visuais (Visão Computacional)

- **Tipo de exame escolhido: angiograma coronariano (cineangiocoronariografia)** — exame padrão-ouro para diagnóstico de DAC.
- **Acervo:** **120 imagens** `.png` (512 × 512 px, mínimo exigido: 100) em [`images/acervo_angiogramas/`](images/acervo_angiogramas/), nomeadas `img_0001.png` … `img_0120.png`; amostra de 8 imagens em [`images/amostra/`](images/amostra/). Rastreabilidade completa nome novo ↔ nome original em [`docs/mapeamento_imagens.csv`](docs/mapeamento_imagens.csv).
- **Origem:** dataset **ARCADE** (desafio MICCAI 2023) — 3.000 angiografias coronarianas anonimizadas, anotadas e validadas por cardiologistas experientes (ferramenta CVAT), de pacientes de 19–90 anos do Research Institute of Cardiology and Internal Diseases (Almaty, Cazaquistão), adquiridas em equipamentos Philips Azurion 3 e Siemens Artis Zee. **Licença CC0 1.0 (domínio público)**, Zenodo DOI [10.5281/zenodo.8386059](https://doi.org/10.5281/zenodo.8386059); artigo de referência na *Scientific Data* (Nature). **Critério de seleção determinístico e reprodutível:** as 120 primeiras imagens (ordem numérica do identificador original) da partição `train` da tarefa de **detecção de estenose**.

### Potencial de análise por Visão Computacional (justificativa)

- **Detecção de padrões e anomalias:** identificar automaticamente **estenoses** (estreitamentos luminais por placas ateroscleróticas) — a tarefa para a qual o ARCADE fornece anotações profissionais, viabilizando detecção supervisionada de objetos (ex.: YOLO/Faster R-CNN) já na **Fase 4**.
- **Identificação de bordas e segmentação:** os contornos dos vasos contrastados são ideais para técnicas de realce e detecção de bordas (Canny, filtros de Frangi) e para segmentação da árvore coronária com redes convolucionais (U-Net), passo prévio à quantificação automática de estenose (QCA).
- **Classificação por CNNs:** classificar frames quanto à presença/gravidade de lesão e ao segmento anatômico acometido (metodologia do escore SYNTAX, disponível no dataset-fonte para expansão futura).
- **Importância clínica:** a leitura de angiogramas é operador-dependente; algoritmos de VC reduzem variabilidade inter-observador, priorizam casos graves na fila de laudo e apoiam decisões de revascularização — núcleo do **diagnóstico assistido por imagem (Fase 4)** e da plataforma integrada (Fase 7).

## 🛡️ Governança de Dados, Viés e LGPD

**Enquadramento LGPD (Lei nº 13.709/2018).** Dados de saúde são **dados pessoais sensíveis** (art. 5º, II). Este projeto utiliza exclusivamente dados **públicos e anonimizados na origem**, sem qualquer identificador direto ou indireto de pacientes reais: o dataset numérico não contém nomes/documentos (o `id_paciente` é um sequencial criado na curadoria); as imagens ARCADE foram anonimizadas pela instituição de origem; os textos são publicações científicas. Não há, portanto, tratamento de dados pessoais identificáveis — ainda assim, o projeto adota os princípios da LGPD (finalidade acadêmica explícita, minimização, transparência e documentação).

**Proveniência e rastreabilidade.** Todo conjunto tem fonte, versão/DOI, data de acesso, licença e método de obtenção registrados em [`docs/proveniencia_e_licencas.md`](docs/proveniencia_e_licencas.md), com verificação de integridade por hash (Parte 1) e mapeamento nome-a-nome (Parte 3). Nenhum dado foi alterado em seu conteúdo; transformações restringem-se a renomeação, conversão de formato e remoção de boilerplate, todas documentadas.

**Licenças.** CC BY 4.0 (dataset numérico), CC BY/CC BY 4.0 (textos — atribuição feita nos cabeçalhos e nas Referências) e CC0 1.0 (imagens). Documentos sem licença explícita de redistribuição **não** foram incluídos.

**Vieses e limitações conhecidos (e impacto nas fases futuras):**

| Conjunto | Viés/limitação | Impacto potencial | Mitigação adotada/planejada |
|---|---|---|---|
| Numérico (Cleveland) | Centro único (EUA), coorte dos anos 1980; 68% homens; pacientes encaminhados a angiografia (viés de espectro) | Modelos da Fase 2 podem ter pior desempenho em mulheres e não generalizar para a população brasileira atual | Documentação explícita; avaliação estratificada por sexo/idade; validação local antes de qualquer uso além do didático |
| Textual | Dois artigos de revisão em português, sem relatos de pacientes; recorte temático (DCV geral + arritmias) | Vocabulário de NLP pode não cobrir linguagem leiga dos usuários do chatbot (Fase 5) | Ampliar corpus nas próximas fases (SciELO/BVS/SUS, literatura de domínio público) e coletar relatos simulados |
| Visual (ARCADE) | Centro único (Cazaquistão), 2 modelos de angiógrafo; frames de 512×512; anotações focadas em estenose | Modelos da Fase 4 podem sofrer *domain shift* em equipamentos/protocolos diferentes | Seleção determinística documentada; futura combinação com outros acervos públicos e *data augmentation* |

## 📁 Estrutura de pastas

Dentre os arquivos e pastas presentes na raiz do projeto, definem-se:

- <b>assets</b>: arquivos relacionados a elementos não-estruturados deste repositório, como imagens institucionais (logo FIAP).

- <b>data</b>: conjunto de dados numéricos da Parte 1 — `dataset_cardiaco.csv` (303 pacientes × 15 variáveis, UTF-8).

- <b>docs</b>: documentos do projeto — os dois textos da Parte 2 (`texto_01_*.txt` e `texto_02_*.txt`), o dicionário de dados (`dicionario_de_dados.md`), a matriz de proveniência e licenças (`proveniencia_e_licencas.md`) e a rastreabilidade das imagens (`mapeamento_imagens.csv`).

- <b>images</b>: dados visuais da Parte 3 — `acervo_angiogramas/` com as 120 imagens do acervo e `amostra/` com 8 imagens para visualização rápida.

- <b>notebooks</b>: pasta reservada para os notebooks (Colab/Jupyter) das fases futuras que consumirão estes dados.

- <b>README.md</b>: arquivo que serve como guia e explicação geral sobre o projeto (o mesmo que você está lendo agora).

## 🔧 Como executar o código

Esta fase é de **curadoria e documentação de dados** — não há aplicação a ser executada. O que se "executa" aqui é o **consumo dos dados**, preparado para os notebooks das fases seguintes.

**Pré-requisitos:** Python 3.11+ com `pandas` e `pillow` (ou qualquer ambiente Colab/Jupyter, onde ambos já vêm instalados).

```bash
# 1. Clonar o repositório
git clone https://github.com/silvioguerreiro/FIAP_1TIAOS_2026_Ano2_Fase1.git
cd FIAP_1TIAOS_2026_Ano2_Fase1

# 2. Instalar as dependências mínimas
pip install pandas pillow
```

```python
# 3. Carregar o dataset numérico (Parte 1)
import pandas as pd
df = pd.read_csv("data/dataset_cardiaco.csv")
print(df.shape)            # (303, 15)
print(df.describe())

# 4. Ler os textos do corpus (Parte 2)
texto = open("docs/texto_01_doencas_cardiovasculares_revisao.txt", encoding="utf-8").read()
print(texto[:800])         # o cabeçalho traz fonte, DOI, data de acesso e licença

# 5. Abrir uma imagem do acervo (Parte 3)
from PIL import Image
img = Image.open("images/acervo_angiogramas/img_0001.png")
print(img.size, img.mode)  # (512, 512)
```

> O acervo completo de imagens e o dataset também estão disponíveis pelos **links públicos do OneDrive** listados na seção de Descrição, caso se prefira o download direto sem clonar o repositório.

## 🗃 Histórico de lançamentos

* 0.2.0 - 27/08/2026
    * README reestruturado no modelo oficial FIAP (Grupo 50, professores, logo institucional em `assets/`) e ajustes finais de identificação dos integrantes.
* 0.1.0 - 15/08/2026
    * Entrega da Fase 1 — Batimentos de Dados: dataset numérico (UCI Heart Disease/Cleveland, 303 × 15), corpus textual (2 artigos CC BY), acervo visual (120 angiogramas ARCADE), dicionário de dados, matriz de proveniência e licenças, e seção de Governança de Dados, viés e LGPD.

## 📚 Referências (ABNT NBR 6023)

- JANOSI, A.; STEINBRUNN, W.; PFISTERER, M.; DETRANO, R. **Heart Disease** [conjunto de dados]. Irvine: UCI Machine Learning Repository, 1989. DOI: 10.24432/C52P4X. Licença: CC BY 4.0. Disponível em: https://archive.ics.uci.edu/dataset/45/heart+disease. Acesso em: 15 ago. 2026.
- ASSUNÇÃO, B. A. F. Doenças cardiovasculares: uma revisão narrativa. **RCMOS — Revista Científica Multidisciplinar O Saber**, São Paulo, ano VII, v. 1, 2026. DOI: 10.51473/rcmos.v1i1.2026.2623. Licença: CC BY. Disponível em: https://submissoesrevistarcmos.com.br/rcmos/article/view/2623. Acesso em: 15 ago. 2026.
- COSTA, A. C.; FRANCO, A. C. L.; PEREIRA, R. F.; GONÇALVES, M. V. V.; NUBILE, E. S. A. Arritmias cardíacas: diagnóstico, tratamento e prevenção. **Brazilian Journal of Implantology and Health Sciences**, v. 6, n. 2, p. 348-360, 2024. DOI: 10.36557/2674-8169.2024v6n2p348-360. Licença: CC BY 4.0. Disponível em: https://bjihs.emnuvens.com.br/bjihs/article/view/1374. Acesso em: 15 ago. 2026.
- POPOV, M. et al. **ARCADE: Automatic Region-based Coronary Artery Disease diagnostics using x-ray angiography imagEs Dataset** [conjunto de dados]. Zenodo, 2023. DOI: 10.5281/zenodo.8386059. Licença: CC0 1.0 (domínio público). Acesso em: 15 ago. 2026.
- POPOV, M. et al. Dataset for Automatic Region-based Coronary Artery Disease Diagnostics Using X-Ray Angiography Images. **Scientific Data**, v. 11, art. 20, 2024. DOI: 10.1038/s41597-023-02871-z. Disponível em: https://www.nature.com/articles/s41597-023-02871-z. Acesso em: 15 ago. 2026.
- BRASIL. **Lei nº 13.709, de 14 de agosto de 2018** (Lei Geral de Proteção de Dados Pessoais — LGPD). Diário Oficial da União: Brasília, DF, 15 ago. 2018.

## 📋 Licença

<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1"><p xmlns:cc="http://creativecommons.org/ns#" xmlns:dct="http://purl.org/dc/terms/"><a property="dct:title" rel="cc:attributionURL" href="https://github.com/agodoi/template">MODELO GIT FIAP</a> por <a rel="cc:attributionURL dct:creator" property="cc:attributionName" href="https://fiap.com.br">Fiap</a> está licenciado sobre <a href="http://creativecommons.org/licenses/by/4.0/?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">Attribution 4.0 International</a>.</p>
