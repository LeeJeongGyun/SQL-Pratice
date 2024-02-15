2024-02-15  
HackerRank Link: https://www.hackerrank.com/challenges/earnings-of-employees/problem

### Language: MSSQL
### Category: GROUP BY, SUBQUERY

```sql
-- 풀이 1)
-- GROUP BY
SELECT TOP 1 months * salary AS earnings, COUNT(*)
FROM Employee
GROUP BY months * salary
ORDER BY earnings DESC

-- 풀이 2)
-- SUBQUERY 사용
SELECT months * salary, COUNT(*)
FROM Employee
WHERE months * salary = ( SELECT MAX(months * salary) FROM Employee )
GROUP BY months * salary
