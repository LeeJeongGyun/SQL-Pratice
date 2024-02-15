2024-02-15  
leetcode Link: https://leetcode.com/problems/department-highest-salary/description/

### Language: MSSQL
### Category: SUBQUERY

```sql
SELECT C.name As Department, B.name AS Employee, A.max_salary AS Salary
FROM 
(
    SELECT  departmentId,
            MAX(salary) AS max_salary
    FROM Employee
    GROUP BY departmentId
) AS A
    INNER JOIN Employee B
    ON A.max_salary = B.salary AND A.departmentId = B.departmentId
    INNER JOIN Department C
    ON A.departmentId = C.id
