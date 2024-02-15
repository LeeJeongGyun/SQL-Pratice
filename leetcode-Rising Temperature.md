2024-02-15  
leetcode Link: https://leetcode.com/problems/rising-temperature/description/

### Language: MSSQL
### Category: JOIN
```
SELECT B.id AS id
FROM Weather A
    INNER JOIN Weather B 
    ON DATEADD(day, 1, A.recordDate) = B.recordDate
WHERE A.temperature < B.temperature
