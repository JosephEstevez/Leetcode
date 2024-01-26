# Exercício 184 leetcode - Department Highest Salary (SQL - Médio)

## Seleciona as tabelas
```
SELECT Department.name AS 'Department', Employee.name AS 'Employee', Employee.salary as 'Salary' 
FROM Employee JOIN Department ON Employee.departmentId = Department.id 
```
## Encontra o funcionário com salário e departamento compatíveis ao maior salário de cada departamento
```
WHERE (Employee.departmentId, Employee.salary) IN
(
```
## Seleciona o maior salário de cada departamento
```
SELECT departmentId, MAX(salary)
FROM Employee
GROUP BY departmentId
)
```
## Código completo
```
SELECT Department.name AS 'Department', Employee.name AS 'Employee', Employee.salary as 'Salary'
FROM Employee JOIN Department ON Employee.departmentId = Department.id
WHERE (Employee.departmentId, Employee.salary) IN
(
 SELECT departmentId, MAX(salary)
FROM Employee
GROUP BY departmentId
)
```
