2024-02-20  

### Language: MSSQL

Name: Japan Population  
Link: https://www.hackerrank.com/challenges/japan-population/problem
```sql
SELECT SUM(POPULATION)
FROM CITY
WHERE COUNTRYCODE = 'JPN'
```


Name: Weather Observation Station 2  
Link: https://www.hackerrank.com/challenges/weather-observation-station-2/problem
```sql
SELECT  CONVERT(NUMERIC(10, 2), SUM(LAT_N)),
        CONVERT(NUMERIC(10, 2), SUM(LONG_W))
FROM STATION
```

Name: Weather Observation Station 18  
Link: https://www.hackerrank.com/challenges/weather-observation-station-18/problem
```sql
SELECT CONVERT(NUMERIC(10,4), 
              ABS(MIN(LAT_N) - MAX(LAT_N)) + ABS(MIN(LONG_W) - MAX(LONG_W))
               )
FROM STATION
```
