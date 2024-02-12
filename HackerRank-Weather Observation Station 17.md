2024-02-12  
HackerRank Link: https://www.hackerrank.com/challenges/weather-observation-station-17/problem

### Language: MSSQL
```sql
SELECT TOP 1 CONVERT(NUMERIC(10, 4), ROUND(LONG_W, 4)) AS ROUND_LONG_W
FROM STATION
WHERE LAT_N > 38.7780
ORDER BY LAT_N
