# Entrega 1 - Escolha e Definição do Problema

O dataset que escolhi é o [SINISTROS DE TRÂNSITO - PRF](https://dados.gov.br/dados/conjuntos-dados/sinistros-de-transito-agrupados-por-ocorrencia), um dataset que contém "Dados de sinistros de trânsito, registrados pela Polícia Rodoviária Federal, com dados desde 01/01/2007".  

O escopo completo dependerá de alinhamento com o professor, mas, pretendo focar, inicialmente, em analisar os dados das ocorrências do ano de 2025. Nesse ano, segundo o [analyse_csv.ipynb](../analyse_csv.ipynb) o dataset conta com:
- 72529 Registros
- 30 colunas base, com a seguinte distribuição de tipos:
    - booleano: 1
    - data/hora: 1
    - numérico: 10
    - texto: 18

Esses números atendem aos requisitos mínimos de linhas e colunas e o dataset, por contar com a coordenada do local do acidente, torna possível a integração externa com dados [meteorológicos do INMET](https://portal.inmet.gov.br/dadoshistoricos), que permitem obter informações mais detalhadas acerca do tempo, segundo a estação mais próxima daquele local. Minha linha de abordagem será guiada pelas seguintes perguntas:
> [!NOTE]
> Como fatores climáticos influenciam nas fatalidades dos acidentes em rodovias federais?
> Como fatores temporais, como proximidade com feriados, fins de semana, influenciam nas fatalidades dos acidentes em rodovias federais?

Minha ideia é treinar um classificador para identificar padrões, com base nos fatores climáticos e de período (feriados, feriados prolongados, fim de semana), nos dados de acidentes, principalmente aqueles em que ocorrem fatalidades. Esse modelo, poderia ser utilizado para analisar as ocorrências e gerar um panorama geral de quais rodovias estão em situação mais crítica, apresentando mais fatalidades por conta dos fatores climáticos, o que ajudaria a direcionar serviços de alerta e prevenção de acidentes, a fim de indicar quais estradas precisariam de mais atenção do poder público a fim de tentar mitigar esses acidentes.

De início irei trabalhar com as seguintes hipóteses:
* *H1: A presença de chuvas aumenta a quantidade de fatalidades em acidentes*
* *H2: Fatores climáticos contribuem mais para o aumento de acidentes do que outros fatores, tais como, época do ano e fins de semana*

> [!NOTE]
> Observação: Acredito que minha máquina aguente trabalhar com todos os dados, mas, se eu sentir que enfrento dificuldades, escolherei um recorte menor, como região SUL, ou Paraná. De acordo com as limitações de hardware e tempo, também poderei optar por analisar somente um ano, ou múltiplos anos.