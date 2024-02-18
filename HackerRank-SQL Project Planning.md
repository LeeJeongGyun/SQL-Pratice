2024-02-18  
HackerRank Link: https://www.hackerrank.com/challenges/sql-projects/problem

### Language: MSSQL
### Category: JOIN, SUBQUERY
```sql
SELECT A.start_date, B.end_date
FROM 
(
    SELECT  start_date,
        ROW_NUMBER() OVER (ORDER BY start_date) RK
    FROM Projects
    WHERE start_date NOT IN ( SELECT DISTINCT end_date FROM Projects)
) A
INNER JOIN 
(
    SELECT  end_date,
        ROW_NUMBER() OVER (ORDER BY end_date) RK
    FROM Projects
    WHERE end_date NOT IN ( SELECT DISTINCT start_date FROM Projects)
) B
ON A.RK = B.RK
ORDER BY DATEDIFF(DAY, A.start_date, B.end_date), A.start_date
