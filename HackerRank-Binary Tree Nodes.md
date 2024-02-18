2024-02-18  
HackerRank Link: https://www.hackerrank.com/challenges/binary-search-tree-1/problem

### Language: MSSQL
### Category: JOIN or CASE SUBQUERY

```sql
-- 이렇게 조건을 잡으면 오류 발생, 아래의 조건이라면 높이가 4 이상이면 Inner도 Leaf가 된다.
SELECT DISTINCT A.N, CASE
                WHEN B.N IS NOT NULL AND B.P IS NOT NULL THEN 'Leaf'
                WHEN B.N IS NULL THEN 'Root'
                ELSE 'Inner'
            END
    FROM BST A
    LEFT JOIN BST B ON A. = B.N
ORDER BY A.N


-- 따라서 아래와 leaf, root를 제외한 나머지를 inner로 해야된다.
SELECT DISTINCT A.N, 
            CASE
                WHEN A.P IS NULL THEN 'Root'
                WHEN B.N IS NULL AND B.P IS NULL THEN 'Leaf'
                ELSE 'Inner'
            END
    FROM BST A
    LEFT JOIN BST B ON A.N = B.P
ORDER BY A.N

-- 조인을 사용하지 않고 풀이
SELECT DISTINCT N,
        CASE 
            WHEN P IS NULL THEN 'Root'
            WHEN N IN (SELECT DISTINCT P FROM BST) THEN 'Inner'
            ELSE 'Leaf'
        END
FROM BST
ORDER BY N
