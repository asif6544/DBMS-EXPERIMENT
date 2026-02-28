-- =====================================================
-- 1. Display empno, ename, department name
-- =====================================================
```
SELECT empno,
       ename,
       CASE deptno
            WHEN 10 THEN 'ACCOUNTING'
            WHEN 20 THEN 'RESEARCH'
            WHEN 30 THEN 'SALES'
            WHEN 40 THEN 'OPERATIONS'
            ELSE 'UNKNOWN'
       END AS dept_name
FROM emp;
```


-- =====================================================
-- 2. Display your age in days
-- =====================================================

```SELECT DATEDIFF(CURDATE(), '2000-08-15') AS age_in_days; ```


-- =====================================================
-- 3. Display your age in months
-- =====================================================
 ```SELECT TIMESTAMPDIFF(MONTH, '2000-08-15', CURDATE()) AS age_in_months;```


-- =====================================================
-- 4. Display current date like 15th August Friday 1997
-- =====================================================
```
SELECT CONCAT(
       DATE_FORMAT(CURDATE(), '%D %M %W '),
       DATE_FORMAT(CURDATE(), '%Y')
) AS formatted_date;
```


-- =====================================================
-- 5. Display: Scott has joined the company on Wednesday 13th August 1990
-- =====================================================
```
SELECT CONCAT(ename,
       ' has joined the company on ',
       DATE_FORMAT(hiredate, '%W %D %M %Y')) AS joining_details
FROM emp;
```


-- =====================================================
-- 6. Find nearest Saturday after current date
-- =====================================================
```
SELECT DATE_ADD(CURDATE(),
       INTERVAL (6 - WEEKDAY(CURDATE()) + 7) % 7 DAY) AS nearest_saturday;
```


-- =====================================================
-- 7. Display current time
-- =====================================================
```
SELECT CURTIME() AS current_time;
```


-- =====================================================
-- 8. Display date three months before current date
-- =====================================================
```
SELECT DATE_SUB(CURDATE(), INTERVAL 3 MONTH) AS three_months_before;
```


-- =====================================================
-- 9. Display employees who joined in December
-- =====================================================
```
SELECT *
FROM emp
WHERE MONTH(hiredate) = 12;
```


-- =====================================================
-- 10. Employees whose first 2 characters of hiredate
--     match last 2 characters of salary
-- =====================================================
```
SELECT *
FROM emp
WHERE LEFT(DATE_FORMAT(hiredate, '%d%m%Y'), 2) =
      RIGHT(sal, 2);
```


-- =====================================================
-- 11. Employees whose 10% salary equals year of joining
-- =====================================================
```
SELECT *
FROM emp
WHERE sal * 0.10 = YEAR(hiredate);
```


-- =====================================================
-- 12. Employees who joined before 15 months
-- =====================================================
```
SELECT *
FROM emp
WHERE TIMESTAMPDIFF(MONTH, hiredate, CURDATE()) > 15;
```


-- =====================================================
-- 13. Employees who joined before 15th of the month
-- =====================================================
```
SELECT *
FROM emp
WHERE DAY(hiredate) < 15;
```

-- =====================================================
-- 14. Employees whose joining day equals deptno
-- =====================================================
```
SELECT *
FROM emp
WHERE DAY(hiredate) = deptno;
```
