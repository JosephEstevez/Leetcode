# Exercício 178 leetcode - Rank Scores (SQL - Médio)

## Cria um sistema de rank para os scores e cria uma relação decresente entre score e posição no rank (quanto maior o score menor a posição no rank)
`SELECT score`: Seleciona a coluna "score" da tabela "scores"
`DENSE_RANK() OVER (ORDER BY score DESC) AS "rank"`: Utiliza a função de janela (OVER) para calcular o rank denso `DENSE_RANK()` dos scores ordenados de forma decrescente `(ORDER BY score DESC)`
O resultado é apelidado de "rank".
```
SELECT score,DENSE_RANK() OVER (ORDER BY score DESC) AS "rank" FROM scores
```
#### Link do exercício: <https://leetcode.com/problems/rank-scores>
