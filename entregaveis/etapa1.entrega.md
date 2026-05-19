# Entrega 1 - Escolha e Definição do Problema

O dataset que escolhi é o [SINISTROS DE TRÂNSITO - PRF](https://dados.gov.br/dados/conjuntos-dados/sinistros-de-transito-agrupados-por-ocorrencia), um dataset que contém "Dados de sinistros de trânsito, registrados pela Polícia Rodoviária Federal, com dados desde 01/01/2007".  

O escopo completo dependerá de alinhamento com o professor, mas, pretendo focar, inicialmente, em analisar os dados das ocorrências do ano de 2025. Nesse ano, segundo o [analyse_csv.ipynb](../analyse_csv.ipynb) o dataset conta com:
- 72529 Registros
- 30 colunas base, com a seguinte distribuição de tipos:
    - booleano: 1
    - data/hora: 1
    - numérico: 10
    - texto: 18

Esses números atendem aos requisitos mínimos de linhas e colunas e o dataset, por contar com a coordenada do local do acidente, torna possível a integração externa com dados [meteorológicos do INMET](https://portal.inmet.gov.br/dadoshistoricos), que permitem obter informações mais detalhadas acerca do tempo, segundo a estação mais próxima daquele local. Minha linha de abordagem será guiada pela seguinte pergunta:
> [!NOTE]
> Como fatores climáticos influenciam nas fatalidades dos acidentes em rodovias federais?

Minha ideia é utilizar o dataset para realizar uma regressão nos dados históricos, criando um modelo que permita predizer sob dadas condições climáticas, quais os riscos de se ocorrer um acidente fatal na rodovia. Esse modelo, combinado com dados meteorológicos em tempo real, poderia ser utilizado para direcionar serviços de alerta e prevenção de acidente, a fim de indicar quais estradas precisariam de mais atenção do poder público e disparar avisos para motoristas que trafegassem por essas regiões.

De início irei trabalhar com as seguintes hipóteses:
* *H1: A presença de chuvas aumenta a quantidade de fatalidades em acidentes*
* *H2: Fatores climáticos contribuem mais para o aumento de acidentes do que outros fatores, tais como, época do ano e fins de semana*

> [!NOTE]
> Observação: Acredito que minha máquina aguente trabalhar com todos os dados, mas, se eu sentir que enfrento dificuldades, escolherei um recorte menor, como região SUL, ou Paraná.