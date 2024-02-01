# Exercício 184 leetcode - Department Highest Salary (SQL - Médio)

## Seleção das tabelas
Esta parte do código faz um `JOIN` entre as tabelas Employee e Department usando a condição de igualdade `Employee.departmentId = Department.id`. Ele seleciona o nome do departamento `Department.name`, o nome do funcionário `Employee.name`, e o salário do funcionário `Employee.salary`.
```
SELECT Department.name AS 'Department', Employee.name AS 'Employee', Employee.salary as 'Salary' 
FROM Employee JOIN Department ON Employee.departmentId = Department.id 
```
## Encontrando o funcionário com o maior salário em cada departamento
Nesta parte, o código filtra os resultados para incluir apenas os funcionários cujo par (ID do departamento, salário) está presente na subconsulta. A subconsulta, por sua vez, utiliza a cláusula `GROUP BY departmentId` para encontrar o maior salário `MAX(salary)` em cada departamento.
```
WHERE (Employee.departmentId, Employee.salary) IN
(
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
#### Link do exercício: <https://leetcode.com/problems/department-highest-salary>
