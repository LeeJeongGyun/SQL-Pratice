2024-02-15  
leetcode Link: https://leetcode.com/problems/employees-earning-more-than-their-managers/description/

### Language: MSSQL
### Category: SELFJOIN
```sql
SELECT A.name AS Employee
FROM Employee A
    LEFT JOIN Employee B ON A.managerId = B.id
WHERE A.salary > B.salary
