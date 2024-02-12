2024-02-12  
HackerRank Link: https://www.hackerrank.com/challenges/african-cities/problem

### INNER JOIN

```sql
SELECT A.name
FROM CITY A
    INNER JOIN COUNTRY B
    ON A.COUNTRYCODE = B.CODE
WHERE B.CONTINENT = 'Africa'
