2024-02-15  
leetcode Link: https://leetcode.com/problems/nth-highest-salary/description/

### Language: MSSQL
### Category: FUNCTION
```sql
-- 풀이 1)
-- DENSE_RANK 사용
CREATE FUNCTION getNthHighestSalary(@N INT)
RETURNS INT
BEGIN
    DECLARE @SALARY INT
    SELECT @SALARY = A.salary
    FROM 
    (
        SELECT salary,
        DENSE_RANK() OVER(ORDER BY salary desc) AS rank    
        FROM Employee
    ) AS A
    WHERE A.rank = @N
    IF @@ROWCOUNT = 0
    BEGIN
        RETURN NULL
    END
    
    RETURN @SALARY
END

-- 풀이 2)
-- ORDER BY, CASE WHEN, SUBQUERY 사
-- 주의 점: TOP 변수 사용법 및 DISTINCT 어떻게 사용하는 지 확인
CREATE FUNCTION getNthHighestSalary(@N INT)
RETURNS INT
BEGIN
    IF @N < 1 
    BEGIN
        RETURN NULL
    END

    RETURN (
        SELECT CASE 
                    WHEN COUNT(A.salary) < @N THEN NULL
                    ELSE MIN(A.salary)
                END
        FROM
        (
            SELECT DISTINCT TOP (@N) salary
            FROM Employee
            ORDER BY salary DESC
        ) AS A
    )
END

-- 풀이 3)
-- 풀이 2의 CASE WHEN 구문을 IIF 구문으로 교체
-- IIF (SQL SERVER 2012 버전에 추가)
CREATE FUNCTION getNthHighestSalary(@N INT)
RETURNS INT
BEGIN
    IF @N < 1 
    BEGIN
        RETURN NULL
    END

    RETURN (
        SELECT IIF(COUNT(A.salary) < @N, NULL, MIN(A.salary))
        FROM
        (
            SELECT DISTINCT TOP (@N) salary
            FROM Employee
            ORDER BY salary DESC
        ) AS A
    )
END

-- 풀이 4
-- OFFSET, FETCH 사용해보기
-- SUBQUERY 사용안해도 되는 장점 존재
CREATE FUNCTION getNthHighestSalary(@N INT)
RETURNS INT
BEGIN
    IF @N < 1
    BEGIN
        RETURN NULL
    END

    RETURN (
        SELECT DISTINCT salary
        FROM Employee
        ORDER BY salary DESC
                OFFSET @N - 1 ROWS  -- OFFSET N ROWS : ORDER BY로 정렬된 내용 중에서 N 개를 지우고 그 다음부터 출력
            FETCH NEXT 1 ROWS ONLY  -- NEXT M ROWS ONLY : N번째 행부터 M개를 출력하겠다.
    )
END





