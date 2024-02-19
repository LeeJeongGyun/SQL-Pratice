2024-02-20  
HackerRank Link: https://www.hackerrank.com/challenges/weather-observation-station-20/problem

### Language: MSSQL
### Category: WHERE 절 CASE WHEN
```sql
SELECT CAST(ROUND(AVG(LAT_N), 4) AS DECIMAL(10,4)) 
FROM (
    SELECT 
        ROW_NUMBER() OVER(ORDER BY LAT_N) row_num,
        COUNT(*) OVER() n,
        LAT_N
    FROM station
) sub
WHERE 
    CASE
        WHEN n % 2 = 1 THEN 
            CASE 
                WHEN row_num = (n+1)/2 THEN 1
                ELSE 0
            END
        ELSE 
            CASE
                WHEN row_num IN (n/2, (n/2)+1) THEN 1
                ELSE 0
            END
    END = 1;
