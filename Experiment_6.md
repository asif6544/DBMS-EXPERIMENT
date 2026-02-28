```1️⃣ Display empno, ename, department name (Using CASE)
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
