# Apresentação

## Etapa 1

- [x] Dataset escolhido: Acidentes da PRF
- [x] Perguntas
    - [x] `Como fatores climáticos influenciam nas fatalidades dos acidentes em rodovias federais?`
    - [x] `Como fatores temporais, como proximidade com feriados, fins de semana, influenciam nas fatalidades dos acidentes em rodovias federais?`
- [x] Hipóteses:
    - [x] *H1: A presença de chuvas aumenta a quantidade de fatalidades em acidentes*
    - [x] *H2: Fatores climáticos contribuem mais para o aumento de acidentes do que outros fatores, tais como, época do ano e fins de semana*
    - [ ] *H3: Feriados, normais e prolongados, aumentam a quantidade de fatalidades em acidentes*

## Etapa 2 - Pré-Processamento

- [x] Criação de colunas boolenas para provisionar noção rápida de se o acidente:
    - [x] Teve mortos (Target)
    - [x] Teve feridos
    - [x] Foi no fim de semana
    - [x] etc
- [x] Integração com dados metereológicos do INMET
    - [x] Obtenção das estações metereológicas mais próximas dos locais dos acidentes
    - [x] Obtenção da precipitação no momento do acidente
    - [x] Integração com a lib holydays para descobrir quais acidentes ocorreram durante feriados e feriados prolongados.
- [x] Falta as médias móveis

### Etapa 3 - Dados e SQL

- [x] Dados em formato tidy
- [x] Exportação/Importação do dataset final usando parquet
    - [x] Posso exportar as estações e históricos em parquet também.
- [ ] Consultas SQL
- [ ] Análise univariadas
- [ ] Análise bivariadas
- [x] Visualizações interpretadas
- [x] Testes de Hipótese

### Etapa 4 - ML

- [x] Baseline com tuning
    - [x] Temos o que melhorar, recall
    - [x] Mover para depois do pré-processamento
    - [x] Escolher +1 algoritmo, provavelmente vai ser SVM se não demorar demais.
- [ ] Validação cruzada
- [ ] Com tuning e validação cruzada

