2024-02-12  
HackerRank Link: https://www.hackerrank.com/challenges/average-population-of-each-continent/problem

### Language: MSSQL
### Category: INNERJOIN
```sql
SELECT B.CONTINENT, FLOOR(AVG(A.POPULATION))
FROM CITY A
    INNER JOIN COUNTRY B
    ON A.COUNTRYCODE = B.CODE
GROUP BY B.CONTINENT
