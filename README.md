# trabalho_final_ciencia_de_dados

Repositório do trabalho final da disciplina de ciência de dados

## Resumo

Nesse trabalho foi criado um classificador de acidentes fatais nas rodovias federais brasileiras que tinha como intuito, utilizar atributos de contexto do acidente, como precipitação do momento, presença de feriados, fins de semana, condições climáticas, de pista, dentre outras características, para treinar modelos LSVM, SGD e Random Forest, com o intuito de identificar com esse contexto padrões que ajudassem na classificação e que direcionassem os órgãos competentes para tomarem ações de mitigação. Porém, os testes estatísticos de hipótese, as análises dos dados e resultados dos classificadores demonstraram que, com exceção de atributos relacionados à presença e quantidade de feridos, o conjunto de dados não apresentou nenhum outro tipo de atributo que fornecesse um contexto mais discriminativo para a separação entre as classes do problema, acabando por favorecer modelos que dependiam fortemente de uma boa separabilidade linear dos dados, como o LSVM e SGD, que foram os melhores.

## Entregas

As entregas desse trabalho estarão disponíveis numa sessão a parte:

* [Entrega 1](./entregaveis/etapa1.entrega.md)
* [Relatório Final](./entregaveis/relatorio_final_cd_afmireski.pdf)
* [Apresentação](./entregaveis/apresentacao_trabalho_final_cd_afmireski.pdf)

## Setup e Execução

Este projeto utiliza o gerenciador de pacotes e ambientes virtuais **[uv](https://github.com/astral-sh/uv)**. Siga os passos abaixo para clonar o repositório, instalar as dependências e executar o projeto.

### 1. Como clonar o repositório

Abra o terminal e execute um dos seguintes comandos para clonar o repositório e acessar a pasta do projeto:

**Via HTTPS:**
```bash
git clone https://github.com/afmireski/trabalho_final_ciencia_de_dados.git
cd trabalho_final_ciencia_de_dados
```

**Via SSH:**
```bash
git clone git@github.com:afmireski/trabalho_final_ciencia_de_dados.git
cd trabalho_final_ciencia_de_dados
```

### 2. Como instalar o `uv`

O `uv` é um gerenciador de pacotes extremamente rápido escrito em Rust. Você pode instalá-lo utilizando os seguintes métodos:

#### Linux e macOS
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

#### Windows (PowerShell)
```powershell
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
```

#### Via pip
Se preferir instalar globalmente usando o pip:
```bash
pip install uv
```

> [!NOTE]
> Para outras opções de instalação, consulte a [documentação oficial do uv](https://docs.astral.sh/uv/getting-started/installation/).

### 3. Como executar o projeto via VSCode

Como o projeto é baseado em Jupyter Notebooks, siga os passos abaixo para configurá-lo e executá-lo no VSCode:

1. **Instalar as dependências do projeto**:
   No terminal, dentro do diretório do projeto, execute o comando abaixo. Ele criará um ambiente virtual local `.venv` e instalará de forma extremamente rápida todas as dependências listadas no [pyproject.toml](./pyproject.toml):
   ```bash
   uv sync
   ```

2. **Abrir o projeto no VSCode**:
   ```bash
   code .
   ```

3. **Garantir a instalação das extensões necessárias**:
   Certifique-se de que as seguintes extensões estão instaladas e ativas no seu VSCode:
   * **Python** (da Microsoft)
   * **Jupyter** (da Microsoft)

4. **Configurar o Kernel do Jupyter**:
   * Abra um dos notebooks do projeto, por exemplo, o notebook principal [trabalho_final_afmireski.ipynb](./trabalho_final_afmireski.ipynb) ou o notebook auxiliar [analyse_csv.ipynb](./analyse_csv.ipynb).
   * No canto superior direito do editor do notebook, clique no botão **Select Kernel** (ou **Selecionar Kernel**).
   * Selecione **Python Environments...** (ou **Ambientes Python...**).
   * Escolha o interpretador contido no ambiente virtual `.venv` criado pelo `uv` (ex: `.venv/bin/python` ou `.venv\Scripts\python.exe`).

5. **Executar**:
   * Com o kernel selecionado, você poderá rodar as células do notebook individualmente ou clicar em **Run All** (Executar Tudo) no topo do arquivo.

## Estrutura de Dados e Resultados (Pasta data)

A pasta [data](./data) é dividida em diretórios para organizar os conjuntos de dados pré-processados, os dados brutos e os resultados obtidos.

### 1. Pasta `datasets`

A subpasta [datasets](./data/datasets) contém os dados processados e serve de destino para os dados brutos necessários para reconstruir o pipeline.

#### Dados Pré-processados (Agregados)
Dentro da subpasta `inmet_aggregated`, estão armazenados os dados resultantes do pré-processamento das estações do INMET e da vinculação dos sinistros:
* [estacoes.csv](./data/datasets/inmet_aggregated/estacoes.csv) e [estacoes_finais.csv](./data/datasets/inmet_aggregated/estacoes_finais.csv): Contêm as informações cadastrais e de localização das estações meteorológicas do INMET.
* [inmet_historico.parquet](./data/datasets/inmet_aggregated/inmet_historico.parquet): Contém os dados meteorológicos coletados por essas estações hora a hora durante os anos de 2024 e 2025.
* [sinistro_estacao_mais_proxima.csv](./data/datasets/inmet_aggregated/sinistro_estacao_mais_proxima.csv): Contém a relação de cada sinistro mapeado com a sua respectiva estação meteorológica mais próxima.

#### Dataset Final Consolidado
* [dataset_final.parquet](./data/datasets/dataset_final.parquet): É o conjunto de dados consolidado após todas as etapas de pré-processamento utilizadas no trabalho. Ele é fundamental para a execução direta dos classificadores; **sem ele, é obrigatório realizar o download dos dados brutos novamente e rodar todo o pipeline de pré-processamento**.

#### Origem dos Dados Brutos (Download Manual)
Caso queira reconstruir o pipeline a partir do zero, os dados brutos devem ser baixados e organizados da seguinte forma (estas pastas estão no `.gitignore`):
* **Dados da PRF (datatran)**: Devem ser obtidos através do link [SINISTROS DE TRÂNSITO - PRF](https://dados.gov.br/dados/conjuntos-dados/sinistros-de-transito-agrupados-por-ocorrencia) (conforme detalhado no arquivo [etapa1.entrega.md](./entregaveis/etapa1.entrega.md)) e colocados na pasta `/data/datasets/sinistros/`.
* **Dados do INMET**: Devem ser obtidos através do link [Dados Históricos do INMET](https://portal.inmet.gov.br/dadoshistoricos) e colocados na pasta `/data/datasets/inmet_raw/YYYY` (onde `YYYY` representa o ano correspondente, ex: `2023`, `2024`, `2025`).

### 2. Pasta `results`

A subpasta [results](./data/results) é destinada ao armazenamento das saídas e métricas geradas pelos classificadores. Por padrão, os resultados obtidos nas execuções originais ficam salvos nesta pasta.



