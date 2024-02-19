2024-02-19  
leetcode Link: https://leetcode.com/problems/rank-scores/description/

### Language: MSSQL
### Category: Rank
```sql
SELECT  score, 
        DENSE_RANK() OVER(ORDER BY score desc) AS 'RANK'
FROM Scores
