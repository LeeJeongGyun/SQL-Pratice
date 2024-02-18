2024-02-18  
HackerRank Link: https://www.hackerrank.com/challenges/occupations/problem

### Language: MSSQL
### Category: Pivot

```sql
SELECT  MAX(CASE WHEN Occupation = 'Doctor' THEN Name ELSE NULL END),
        MAX(CASE WHEN Occupation = 'Professor' THEN Name ELSE NULL END),
        MAX(CASE WHEN Occupation = 'Singer' THEN Name ELSE NULL END),
        MAX(CASE WHEN Occupation = 'Actor' THEN Name ELSE NULL END)
FROM 
(
    SELECT  Name,
            Occupation,
            ROW_NUMBER() OVER (PARTITION BY Occupation ORDER BY Name) AS RK
    FROM OCCUPATIONS
) AS A
GROUP BY A.RK
ORDER BY A.RK
