# 第三次作业 
## 输出 我，我的老板，我老板的老板

```sql
 use company;
Database changed
mysql> DROP TABLE IF EXISTS t_employee;
Query OK, 0 rows affected, 1 warning (0.00 sec)

mysql>
mysql> CREATE TABLE t_employee2 (
    ->     deptno INT NOT NULL,
    -> empno INT  PRIMARY KEY,
    -> ename VARCHAR(20),
    -> job  VARCHAR(20),
    ->     MGR  INT,
    -> Hiredate Date,
    -> sal    float,
    -> comm   float
    -> );
Query OK, 0 rows affected (0.02 sec)

mysql>
mysql>
mysql>
mysql> INSERT INTO t_employee2 (empno, ename, job, MGR, Hiredate, sal, comm, deptno) VALUES
    ->     (7369, "SMITH", "CLERK", 7902, "1981-03-12", 800.00, NULL, 20),
    -> (7499, "ALLEN", "SALESMAN", 7698, "1982-03-12", 1600, 300, 30),
    -> (7521, "WARD", "SALESMAN", 7698, "1838-03-12", 1250, 500, 30),
    -> (7566, "JONES", "MANAGER", 7839, "1981-03-12", 2975, NULL, 20),
    -> (7654, "MARTIN", "SALESMAN", 7698, "1981-01-12", 1250, 1400, 30),
    -> (7698, "BLAKE", "MANAGER", 7839, "1985-03-12", 2450, NULL, 10),
    -> (7788, "SCOTT", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
    -> (7839, "KING", "PRESIDENT", NULL, "1981-03-12", 5000, NULL, 10),
    -> (7844, "TURNER", "SALESMAN", 7689, "1981-03-12", 1500, 0, 30),
    -> (7878, "ADAMS", "CLERK", 7788, "1981-03-12", 1100, NULL,20),
    -> (7900, "JAMES", "CLERK", 7698,"1981-03-12",  950, NULL, 30),
    -> (7902, "FORD", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
    -> (7934, "MILLER", "CLERK", 7782, "1981-03-12", 1300, NULL, 10)
    -> ;
Query OK, 13 rows affected (0.01 sec)
Records: 13  Duplicates: 0  Warnings: 0

mysql>
mysql> DROP TABLE IF EXISTS t_dept;
Query OK, 0 rows affected (0.02 sec)

mysql>
mysql> CREATE TABLE t_dept (
    ->     deptno INT PRIMARY KEY,
    -> dname VARCHAR(30),
    -> loc VARCHAR(50)
    -> );
Query OK, 0 rows affected (0.02 sec)

mysql>
mysql> INSERT INTO t_dept VALUES
    -> (10, "ACCOUNTING", "NEW YORK"),
    -> (20, "RESEARCH", "DALLAS"),
    -> (30, "SALES", "CHICAGO"),
    -> (40, "OPERATIONS", "BOSTON")
    -> ;
Query OK, 4 rows affected (0.01 sec)
Records: 4  Duplicates: 0  Warnings: 0
```

```sql
select * from t_employee2;
```
![](https://github.com/JINxin-0505/homework/blob/master/picture/m19.png)

```sql
 select t1.ename '我',t2.ename '我的老板',t3.ename '我老板的老板'
    ->  from t_employee2 t1 inner join t_employee2 t2 on t1.mgr= t2.empno
    ->  inner join t_employee2 t3 on t2.mgr= t3.empno;
```
![](https://github.com/JINxin-0505/homework/blob/master/picture/m20.png)

