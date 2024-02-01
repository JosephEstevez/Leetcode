# Exercício 185 leetcode - Department Top Three Salaries (SQL - Difícil)

## Seleção das tabelas
A primeira parte do código inicia com a seleção das colunas `Name` da tabela `Department` (renomeada como `d`) e `Name` e `Salary` da tabela `Employee` (renomeada como `e`).
```
SELECT d.Name AS Department, e.Name AS Employee, e.Salary AS Salary FROM
(
```
## Criação de um rank para todos os salários por departamento
A subconsulta dentro dos parênteses `( ... )` cria um rank usando a função `DENSE_RANK()`. `O PARTITION BY DepartmentId` garante que o rank seja calculado separadamente para cada departamento. A ordenação é feita por `DepartmentId` e `Salary DESC` (em ordem decrescente).
```
SELECT e.*, DENSE_RANK() over (PARTITION BY DepartmentId ORDER BY Departmentid, Salary DESC) AS `rank`
FROM Employee e 
) e 
```
## Limitação para os três maiores salários de cada departamento
A parte final do código junta as tabelas `Employee` e `Department` usando um JOIN com base na igualdade `e.DepartmentId = d.Id.` A condição `WHERE rank <= 3` é usada para limitar os resultados aos três maiores salários de cada departamento.
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
#### Link do exercício: <https://leetcode.com/problems/department-top-three-salaries>
