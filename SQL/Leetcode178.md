# Exercício 178 leetcode - Rank Scores (SQL - Médio)

## Cria um sistema de rank para os scores e cria uma relação decresente entre score e posição no rank (quanto maior o score menor a posição no rank)

```
SELECT score,DENSE_RANK() OVER (ORDER BY score DESC) AS "rank" FROM scores
```
