2024-02-18  
HackerRank Link: https://www.hackerrank.com/challenges/the-company/problem

### Language: MSSQL
### Category: SELECT SUBQUERY
```sql

SELECT  A.company_code,
        A.founder,
        (
            SELECT COUNT(DISTINCT lead_manager_code) 
            FROM Lead_Manager 
            WHERE company_code = A.company_code
        ),
        (
            SELECT COUNT(DISTINCT senior_manager_code) 
            FROM Senior_Manager 
            WHERE company_code = A.company_code
        ),
        (
            SELECT COUNT(DISTINCT manager_code) 
            FROM Manager 
            WHERE company_code = A.company_code
        ),
        (
            SELECT COUNT(DISTINCT employee_code) 
            FROM Employee 
            WHERE company_code = A.company_code
        )
FROM Company A
ORDER BY A.company_code
