# Exercício 185 leetcode - Department Top Three Salaries (SQL - Difícil)

## Seleciona as tabelas
```
SELECT d.Name AS Department, e.Name AS Employee, e.Salary AS Salary FROM
(
```
## Cria um rank de todos os pagamentos
```
SELECT e.*, DENSE_RANK() over (PARTITION BY DepartmentId ORDER BY Departmentid, Salary DESC) AS `rank`
FROM Employee e 
) e 
```
## Limita a busca para que apareçam apenas os 3 maiores pagamentos de cada departamento
```
JOIN Department d
ON e.DepartmentId = d.Id 
WHERE `rank` <=3
```
## Código completo
```
SELECT d.Name AS Department, e.Name AS Employee, e.Salary FROM
(
SELECT e.*, DENSE_RANK() over (PARTITION BY DepartmentId ORDER BY Departmentid, Salary DESC) AS `rank`
FROM Employee e
) e
JOIN Department d
ON e.DepartmentId = d.Id 
WHERE `rank` <=3
```
