# 第五次作业
## 运行存储过程和函数
### 1.存储过程

```sql
DELIMITER $$
mysql> CREATE PROCEDURE proce_employee_sal()
    -> BEGIN
    ->     SELECT sal
    -> FROM t_employee2;
    -> END$$
Query OK, 0 rows affected (0.00 sec)

mysql> DELIMITER ;
mysql>
mysql> CALL proce_employee_sal();
```

### 2.函数

```sql
 DELIMITER $$
mysql> CREATE FUNCTION func_employee_sal1 (empno INT)
    -> RETURNS DOUBLE
    -> BEGIN
    ->     RETURN (SELECT sal FROM t_employee2 WHERE t_employee2.empno = empno);
    -> END$$
Query OK, 0 rows affected (0.00 sec)

mysql> DELIMITER ;
mysql>
mysql> SELECT func_employee_sal1 (7369);
```
