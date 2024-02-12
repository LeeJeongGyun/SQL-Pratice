2024-02-12  
HackerRank Link: https://www.hackerrank.com/challenges/asian-population/problem

### INNER JOIN
```sql
SELECT SUM(A.POPULATION)
FROM CITY A
    INNER JOIN COUNTRY B
    ON A.COUNTRYCODE = B.CODE
WHERE B.CONTINENT = 'Asia'
