2024-02-12  
leetcode Link: https://leetcode.com/problems/customers-who-never-order/description/

### Language: MSSQL
### Category: LEFTJOIN
```sql
SELECT A.name as Customers
FROM Customers A
    LEFT JOIN Orders B
    ON A.id = B.customerId
WHERE B.id IS NULL
