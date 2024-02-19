2024-02-19  
leetcode Link: https://leetcode.com/problems/exchange-seats/description/

### Language: MSSQL
### Category: COUNT(*) OVER, CASE
```sql
SELECT  CASE
            WHEN sub.id = sub.total_rows AND sub.total_rows % 2 != 0 THEN sub.id
            WHEN sub.id % 2 = 0 THEN sub.id - 1
            ELSE sub.id + 1
        END AS id,
        student
FROM
(
    SELECT  id,
            student,
            COUNT(*) OVER () AS total_rows
    FROM Seat
) AS sub
ORDER BY id
