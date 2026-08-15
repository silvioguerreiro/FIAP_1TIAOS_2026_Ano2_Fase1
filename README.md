# CardioIA — Fase 1: Batimentos de Dados 🫀

Repositório da **Fase 1 — "Batimentos de Dados: Mapeando o Coração Moderno"** do Projeto **CardioIA**, com a curadoria documentada dos três tipos de dados que alimentarão as fases seguintes do projeto: numéricos (IoT), textuais (NLP) e visuais (Visão Computacional).

> **Este README.md é o documento-resumo da entrega**, conforme exigido no enunciado: explica o projeto, descreve cada uma das três partes, indica objetivos, fontes dos dados e links públicos, e consolida a governança de dados da Fase 1.

**Resumo da entrega:**

| Item | Exigência mínima do enunciado | Entregue | Localização |
|---|---|---|---|
| Parte 1 — Dados numéricos (IoT) | Dataset com ≥ 100 linhas, formato .csv ou .xlsx | **303 pacientes × 15 variáveis**, .csv UTF-8, dados reais (UCI, CC BY 4.0) | [`data/`](data/) + link OneDrive (Seção 3) |
| Parte 2 — Dados textuais (NLP) | ≥ 2 textos .txt em subpasta `docs` ou `assets` | **2 artigos científicos** de acesso aberto (CC BY) em .txt, com proveniência | [`docs/`](docs/) (Seção 4) |
| Parte 3 — Dados visuais (VC) | ≥ 100 imagens .jpg/.png de um tipo de exame | **120 angiogramas** .png 512×512 (ARCADE, CC0) | [`images/acervo_angiogramas/`](images/acervo_angiogramas/) + link OneDrive (Seção 5) |
| Documento-resumo | README.md detalhado, claro e estruturado | **Este documento** (Seções 1–8) | raiz do repositório |
| Governança de Dados e viés | Conceitos de governança e viés aplicados aos dados | Seção dedicada + matriz de proveniência e licenças | Seção 6 + [`docs/proveniencia_e_licencas.md`](docs/proveniencia_e_licencas.md) |
| Notebooks futuros (dica) | Pasta reservada para Colab/Jupyter | Criada | [`notebooks/`](notebooks/) |

**Links públicos da entrega (OneDrive, acesso somente exibição):** [conjunto completo — pasta `cardioia-fase1`](https://1drv.ms/f/c/a655986124216a70/IgCkUuM5o4JfRY_NNLsD8aptAfYoPid-hPTF5rJcJUy6owk?e=gaRjyU) · [dados numéricos — `data`](https://1drv.ms/f/c/a655986124216a70/IgAU5LQqEtMfTr-a4dDLN3chAXBdb6R1mbrNvFhW20KK4Kk?e=hZBFzG) · [dados visuais — `images`](https://1drv.ms/f/c/a655986124216a70/IgCFUMdnwJGPQL5s6l-CK7b4AdgMfkNIBHMLjAg_UnQU1IQ?e=JEvC2c)

## 1. Identificação

| Campo | Valor |
|---|---|
| Projeto | CardioIA — A Nova Era da Cardiologia Inteligente |
| Fase | Fase 1 — Batimentos de Dados: Mapeando o Coração Moderno |
| Instituição / Curso | FIAP — Inteligência Artificial (2º ano, método PBL) |
| Aluno | **Silvio Prestes Guerreiro Junior — RM567958** (grupo individual) |
| Data | Agosto/2026 |

## 2. Visão geral do projeto e objetivo da Fase 1

O **CardioIA** é um projeto acadêmico que simula o ecossistema de uma cardiologia moderna: uma plataforma digital inteligente que integra dados clínicos, modelos de Machine Learning, Visão Computacional, IoT e agentes inteligentes para triagem, diagnóstico, monitoramento, assistência remota e previsão de eventos cardíacos. As doenças cardiovasculares são a principal causa de morte no mundo — cerca de **17,9 milhões de óbitos anuais** — e grande parte desses desfechos é evitável com diagnóstico precoce, frente em que a IA tem potencial transformador.

A Fase 1 constrói a **base de dados** do ecossistema. Cada conjunto foi escolhido já pensando nas fases seguintes do mapa mental do projeto: modelos de risco (**Fase 2**), monitoramento IoT com wearables (**Fase 3**), diagnóstico por imagem com Visão Computacional (**Fase 4**), assistente virtual com NLP (**Fase 5**), previsão de crises com séries temporais (**Fase 6**) e a plataforma integrada final (**Fase 7**) — tudo sob os princípios de **Governança de Dados e LGPD** (Seção 6).

## 3. Parte 1 — Dados Numéricos (IoT)

- **Arquivo:** [`data/dataset_cardiaco.csv`](data/dataset_cardiaco.csv) — **303 pacientes × 15 variáveis** (mínimo exigido: 100 linhas), CSV UTF-8.
- **Origem: dados REAIS** — UCI Machine Learning Repository, dataset *Heart Disease*, subconjunto Cleveland Clinic Foundation. Licença **CC BY 4.0**, DOI [10.24432/C52P4X](https://doi.org/10.24432/C52P4X). A verificação de integridade da fonte (12 checagens canônicas + hashes SHA-256) está documentada em [`docs/proveniencia_e_licencas.md`](docs/proveniencia_e_licencas.md).
- **Dicionário de dados completo:** [`docs/dicionario_de_dados.md`](docs/dicionario_de_dados.md) — tipo, unidade, faixa e significado clínico de cada variável, além da rastreabilidade de todas as transformações (tradução de colunas, `id_paciente`, tratamento de ausentes sem imputação).
- **Link público (OneDrive) — dados numéricos:** [pasta `data` no OneDrive](https://1drv.ms/f/c/a655986124216a70/IgAU5LQqEtMfTr-a4dDLN3chAXBdb6R1mbrNvFhW20KK4Kk?e=hZBFzG)

### Variáveis de maior relevância clínica (justificativa)

1. **`tipo_dor_toracica`** — a caracterização da dor torácica (típica, atípica, não anginosa, assintomática) é o ponto de partida das diretrizes para estimar a probabilidade pré-teste de doença arterial coronariana (DAC). Para o sistema de **triagem digital** do CardioIA, é a variável de anamnese com maior poder discriminativo isolado.
2. **`depressao_st_exercicio` (com `inclinacao_st`)** — a depressão do segmento ST induzida por esforço é o marcador eletrocardiográfico clássico de isquemia miocárdica; quanto maior (0,0–6,2 mm no dataset), maior a suspeita de DAC obstrutiva. Informação de alto valor para os modelos de **diagnóstico assistido** da Fase 2.
3. **`freq_cardiaca_maxima`** — a resposta cronotrópica ao esforço resume a reserva funcional cardiovascular; valores reduzidos associam-se a doença mais grave. Com `angina_induzida_exercicio`, descreve o comportamento do coração sob estresse — exatamente o tipo de sinal que os sensores vestíveis da **Fase 3 (IoT)** capturarão em tempo real.
4. **`pressao_arterial_repouso` e `colesterol_serico`** — os dois grandes fatores de risco **modificáveis** da aterosclerose, base de escores populacionais (ex.: Framingham); permitem à plataforma gerar alertas preventivos e recomendações personalizadas.
5. **`idade` e `sexo`** — estratificam o risco basal em qualquer escore cardiovascular e são indispensáveis à **análise de viés e representatividade** dos modelos (Governança, Seção 6).

A variável-alvo **`diagnostico_dac`** (0 = sem estenose ≥ 50%; 1–4 = DAC em gradação crescente) permite treinar tanto classificadores binários de triagem quanto modelos ordinais de gravidade.

## 4. Parte 2 — Dados Textuais (NLP)

Dois artigos científicos **em acesso aberto com licença Creative Commons Attribution verificada**, extraídos para `.txt` (UTF-8) com cabeçalho interno de proveniência (título, autoria, fonte, URL, DOI, datas e licença):

| Arquivo | Conteúdo | Fonte |
|---|---|---|
| [`docs/texto_01_doencas_cardiovasculares_revisao.txt`](docs/texto_01_doencas_cardiovasculares_revisao.txt) | Revisão narrativa das DCVs: fatores de risco, fisiopatologia (aterosclerose, IAM), prevenção, diagnóstico e tratamento (~3.100 palavras) | RCMOS (ISSN 2675-9128), 2026, CC BY |
| [`docs/texto_02_arritmias_cardiacas.txt`](docs/texto_02_arritmias_cardiacas.txt) | Revisão sobre arritmias: diagnóstico (ECG, Holter), tratamento (ablação, antiarrítmicos), prevenção e tecnologias (wearables, telemedicina) (~4.000 palavras) | BJIHS, v. 6, n. 2, 2024, CC BY 4.0 |

- **Link público (OneDrive):** os textos integram o próprio repositório ([`docs/`](docs/)) e o [espelho completo da entrega no OneDrive](https://1drv.ms/f/c/a655986124216a70/IgCkUuM5o4JfRY_NNLsD8aptAfYoPid-hPTF5rJcJUy6owk?e=gaRjyU).

**Nota de governança:** outros quatro documentos coletados na pesquisa (dois TCCs e dois capítulos/artigos) **não** foram redistribuídos neste repositório por não apresentarem licença explícita de redistribuição — decisão registrada em `docs/proveniencia_e_licencas.md`.

### Potencial de exploração por NLP (justificativa)

- **Extração de entidades clínicas (NER):** os dois textos são ricos em doenças (IAM, insuficiência cardíaca, fibrilação atrial), sintomas (dor torácica, palpitações, síncope, dispneia), exames (ECG, Holter, ecocardiograma) e tratamentos (ablação por cateter, antiarrítmicos, anti-hipertensivos) — vocabulário essencial para o **assistente cardiológico virtual da Fase 5** reconhecer queixas de pacientes e responder com terminologia correta.
- **Classificação de tópicos:** as seções naturais dos artigos (fatores de risco → diagnóstico → tratamento → prevenção) fornecem material rotulável para classificar mensagens de pacientes por intenção (dúvida sobre sintoma × medicação × prevenção), roteando o atendimento na plataforma.
- **Sumarização e base de conhecimento (RAG):** os textos podem ancorar respostas do chatbot em conteúdo científico citável, reduzindo alucinação — prática recomendada em IA responsável para saúde.
- **Análise de sentimentos:** a técnica, exemplificada no enunciado, será aplicável na Fase 5 aos **relatos de pacientes** coletados pela plataforma; o corpus atual fornece o vocabulário clínico de referência para calibrar esse pipeline.
- **Mineração de relações sintoma–doença–tratamento:** o texto de arritmias conecta explicitamente achados de exame a condutas — insumo para grafos de conhecimento que apoiam a **previsão de crises da Fase 6** (ex.: arritmias como eventos-alvo).

## 5. Parte 3 — Dados Visuais (Visão Computacional)

- **Tipo de exame escolhido: angiograma coronariano (cineangiocoronariografia)** — exame padrão-ouro para diagnóstico de DAC.
- **Acervo:** **120 imagens** `.png` (512 × 512 px, mínimo exigido: 100) em `images/acervo_angiogramas/`, nomeadas `img_0001.png` … `img_0120.png`; amostra de 8 imagens em [`images/amostra/`](images/amostra/). Rastreabilidade completa nome novo ↔ nome original em [`docs/mapeamento_imagens.csv`](docs/mapeamento_imagens.csv).
- **Origem:** dataset **ARCADE** (desafio MICCAI 2023) — 3.000 angiografias coronarianas anonimizadas, anotadas e validadas por cardiologistas experientes (ferramenta CVAT), de pacientes de 19–90 anos do Research Institute of Cardiology and Internal Diseases (Almaty, Cazaquistão), adquiridas em equipamentos Philips Azurion 3 e Siemens Artis Zee. **Licença CC0 1.0 (domínio público)**, Zenodo DOI [10.5281/zenodo.8386059](https://doi.org/10.5281/zenodo.8386059); artigo de referência na *Scientific Data* (Nature). **Critério de seleção determinístico e reprodutível:** as 120 primeiras imagens (ordem numérica do identificador original) da partição `train` da tarefa de **detecção de estenose**.
- **Link público (OneDrive) — acervo de imagens:** [pasta `images` no OneDrive](https://1drv.ms/f/c/a655986124216a70/IgCFUMdnwJGPQL5s6l-CK7b4AdgMfkNIBHMLjAg_UnQU1IQ?e=JEvC2c)

### Potencial de análise por Visão Computacional (justificativa)

- **Detecção de padrões e anomalias:** identificar automaticamente **estenoses** (estreitamentos luminais por placas ateroscleróticas) — a tarefa para a qual o ARCADE fornece anotações profissionais, viabilizando detecção supervisionada de objetos (ex.: YOLO/Faster R-CNN) já na **Fase 4**.
- **Identificação de bordas e segmentação:** os contornos dos vasos contrastados são ideais para técnicas de realce e detecção de bordas (Canny, filtros de Frangi) e para segmentação da árvore coronária com redes convolucionais (U-Net), passo prévio à quantificação automática de estenose (QCA).
- **Classificação por CNNs:** classificar frames quanto à presença/gravidade de lesão e ao segmento anatômico acometido (metodologia do escore SYNTAX, disponível no dataset-fonte para expansão futura).
- **Importância clínica:** a leitura de angiogramas é operador-dependente; algoritmos de VC reduzem variabilidade inter-observador, priorizam casos graves na fila de laudo e apoiam decisões de revascularização — núcleo do **diagnóstico assistido por imagem (Fase 4)** e da plataforma integrada (Fase 7).

## 6. Governança de Dados, Viés e LGPD

**Enquadramento LGPD (Lei nº 13.709/2018).** Dados de saúde são **dados pessoais sensíveis** (art. 5º, II). Este projeto utiliza exclusivamente dados **públicos e anonimizados na origem**, sem qualquer identificador direto ou indireto de pacientes reais: o dataset numérico não contém nomes/documentos (o `id_paciente` é um sequencial criado na curadoria); as imagens ARCADE foram anonimizadas pela instituição de origem; os textos são publicações científicas. Não há, portanto, tratamento de dados pessoais identificáveis — ainda assim, o projeto adota os princípios da LGPD (finalidade acadêmica explícita, minimização, transparência e documentação).

**Proveniência e rastreabilidade.** Todo conjunto tem fonte, versão/DOI, data de acesso, licença e método de obtenção registrados em [`docs/proveniencia_e_licencas.md`](docs/proveniencia_e_licencas.md), com verificação de integridade por hash (Parte 1) e mapeamento nome-a-nome (Parte 3). Nenhum dado foi alterado em seu conteúdo; transformações restringem-se a renomeação, conversão de formato e remoção de boilerplate, todas documentadas.

**Licenças.** CC BY 4.0 (dataset numérico), CC BY/CC BY 4.0 (textos — atribuição feita nos cabeçalhos e nas Referências) e CC0 1.0 (imagens). Documentos sem licença explícita de redistribuição **não** foram incluídos.

**Vieses e limitações conhecidos (e impacto nas fases futuras):**

| Conjunto | Viés/limitação | Impacto potencial | Mitigação adotada/planejada |
|---|---|---|---|
| Numérico (Cleveland) | Centro único (EUA), coorte dos anos 1980; 68% homens; pacientes encaminhados a angiografia (viés de espectro) | Modelos da Fase 2 podem ter pior desempenho em mulheres e não generalizar para a população brasileira atual | Documentação explícita; avaliação estratificada por sexo/idade; validação local antes de qualquer uso além do didático |
| Textual | Dois artigos de revisão em português, sem relatos de pacientes; recorte temático (DCV geral + arritmias) | Vocabulário de NLP pode não cobrir linguagem leiga dos usuários do chatbot (Fase 5) | Ampliar corpus nas próximas fases (SciELO/BVS/SUS, literatura de domínio público) e coletar relatos simulados |
| Visual (ARCADE) | Centro único (Cazaquistão), 2 modelos de angiógrafo; frames de 512×512; anotações focadas em estenose | Modelos da Fase 4 podem sofrer *domain shift* em equipamentos/protocolos diferentes | Seleção determinística documentada; futura combinação com outros acervos públicos e *data augmentation* |

## 7. Estrutura do repositório

```
cardioia-fase1/
├── README.md
├── data/
│   └── dataset_cardiaco.csv                      # Parte 1 — 303 × 15, UTF-8
├── docs/
│   ├── texto_01_doencas_cardiovasculares_revisao.txt   # Parte 2
│   ├── texto_02_arritmias_cardiacas.txt                # Parte 2
│   ├── dicionario_de_dados.md                    # dicionário de dados da Parte 1
│   ├── proveniencia_e_licencas.md                # governança: fontes, licenças, integridade
│   └── mapeamento_imagens.csv                    # rastreabilidade da Parte 3
├── images/
│   ├── amostra/                                  # 8 imagens de amostra (visualização rápida)
│   └── acervo_angiogramas/                       # Parte 3 — 120 imagens .png 512×512
└── notebooks/                                    # reservado para Colab/Jupyter das fases futuras
    └── .gitkeep
```

## 8. Referências (ABNT NBR 6023) e licenças

- JANOSI, A.; STEINBRUNN, W.; PFISTERER, M.; DETRANO, R. **Heart Disease** [conjunto de dados]. Irvine: UCI Machine Learning Repository, 1989. DOI: 10.24432/C52P4X. Licença: CC BY 4.0. Disponível em: https://archive.ics.uci.edu/dataset/45/heart+disease. Acesso em: 15 ago. 2026.
- ASSUNÇÃO, B. A. F. Doenças cardiovasculares: uma revisão narrativa. **RCMOS — Revista Científica Multidisciplinar O Saber**, São Paulo, ano VII, v. 1, 2026. DOI: 10.51473/rcmos.v1i1.2026.2623. Licença: CC BY. Disponível em: https://submissoesrevistarcmos.com.br/rcmos/article/view/2623. Acesso em: 15 ago. 2026.
- COSTA, A. C.; FRANCO, A. C. L.; PEREIRA, R. F.; GONÇALVES, M. V. V.; NUBILE, E. S. A. Arritmias cardíacas: diagnóstico, tratamento e prevenção. **Brazilian Journal of Implantology and Health Sciences**, v. 6, n. 2, p. 348-360, 2024. DOI: 10.36557/2674-8169.2024v6n2p348-360. Licença: CC BY 4.0. Disponível em: https://bjihs.emnuvens.com.br/bjihs/article/view/1374. Acesso em: 15 ago. 2026.
- POPOV, M. et al. **ARCADE: Automatic Region-based Coronary Artery Disease diagnostics using x-ray angiography imagEs Dataset** [conjunto de dados]. Zenodo, 2023. DOI: 10.5281/zenodo.8386059. Licença: CC0 1.0 (domínio público). Acesso em: 15 ago. 2026.
- POPOV, M. et al. Dataset for Automatic Region-based Coronary Artery Disease Diagnostics Using X-Ray Angiography Images. **Scientific Data**, v. 11, art. 20, 2024. DOI: 10.1038/s41597-023-02871-z. Disponível em: https://www.nature.com/articles/s41597-023-02871-z. Acesso em: 15 ago. 2026.
- BRASIL. **Lei nº 13.709, de 14 de agosto de 2018** (Lei Geral de Proteção de Dados Pessoais — LGPD). Diário Oficial da União: Brasília, DF, 15 ago. 2018.
