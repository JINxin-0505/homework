# 第三次作业
## 两个query 用 join 表示
### 1.select * from t_employee WHERE sal > (select sal from t_employee WHERE ename='SMITH');使用inner join 表示

```sql
select * from t_employee2;
```

```sql
select * from t_employee2 WHERE sal > (select sal from t_employee2 WHERE ename='SMITH');
```

```sql
select t1.deptno,t1.ename,t1.job,t1.mgr,t1.hiredate,t1.sal,t1.comm
    ->  from t_employee2 t1 inner join t_employee2 t2
    ->  on t1.sal>t2.sal and (t2.ename='SMITH');
 ```
 
### 2.select * from t_employee WHERE (sal, job) = (select sal,job from t_employee where ename = 'smith');用 inner join表示

```sql
 select * from t_employee2 where (sal,job) = (select sal,job from t_employee2 where ename = 'SMITH');
```

```sql
select t1.deptno,t1.empno,t1.ename,t1.job,t1.mgr,t1.hiredate,t1.sal,t1.comm
    -> from t_employee2 t1 inner join  t_employee2 t2
    -> on (t1.sal = t2.sal and (t2.ename='smith')) and (t1.job = t2.job and (t2.ename='smith'));
``` 

