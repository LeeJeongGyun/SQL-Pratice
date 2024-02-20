2024-02-20  
leetcode Link: https://leetcode.com/problems/big-countries/description/

### Language: MSSQL
### Category: WHERE
```sql
SELECT name, population, area
FROM World
WHERE [area] >= 3000000 OR [population] >= 25000000
