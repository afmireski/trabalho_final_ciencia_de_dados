# Entrega 2 - Integração com fontes externas

## Inmet

A primeira fonte de integração externa a ser utilizada será o INMET, que fornecerá dados acerca das condições climáticas no momento do acidente.

Os datasets do INMET, tem algumas peculiaridades que dificultam sua integração:

**Cabeçalho nos CSVs:**

```txt
REGIAO:;CO
UF:;DF
ESTACAO:;BRASILIA
CODIGO (WMO):;A001
LATITUDE:;-15,78944444
LONGITUDE:;-47,92583332
ALTITUDE:;1160,96
DATA DE FUNDACAO:;07/05/00
<Colunas>
```

Todo csv do INMET apresenta seus dados da estação nas 8 primeiras linhas do dataset, então, não se pode simplesmente só ler o arquivo e extrair as informações úteis. A partir da 9ª linha, começam os dados históricos da estação naquele no ano em escolhido.

**Grande quantidade de arquivos**

Para cada estação existe um arquivo, totalizando mais de quinhentos arquivos. Mesmo com um grande volume de acidentes, eles ocorreram em rodovias federais, então, é altamente improvável que todas as estações sejam usadas para complementar os dados de acidentes.


---

Para resolver esses problemas, é necessário realizar alguns pré-processamentos:
1. Extrair todos os dados das estações em um arquivo separado
2. Com as estações, identificar quais são efetivamente viáveis para complementar o dataset de acidentes, descartando as que forem desnecessárias.
3. Das estações úteis, condensar todo o histórico dessas estações em um único CSV.
4. O objetivo é transfor