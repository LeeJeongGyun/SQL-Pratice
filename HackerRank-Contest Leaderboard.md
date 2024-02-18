2024-02-18  
HackerRank Link: https://www.hackerrank.com/challenges/contest-leaderboard/problem

### Language: MSSQL
```sql
SELECT B.hacker_id, B.name, SUM(A.max_score) AS sum_score
FROM 
(
    SELECT hacker_id, MAX(score) AS max_score
    FROM Submissions
    WHERE score <> 0
    GROUP BY hacker_id, challenge_id
) A
INNER JOIN Hackers B ON A.hacker_id = B.hacker_id
GROUP BY B.hacker_id, B.name
ORDER BY sum_score desc, B.hacker_id
