# 第一次作业
## 创建一个数据库
 
```sql
create database b_dept;
Query OK, 1 row affected (0.02 sec)
```

## 查看数据库

```sql
 show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| b_dept             |
| company            |
| db_test            |
| mysql              |
| new_student        |
| performance_schema |
| sys                |
| test_database      |
| view               |
+--------------------+
10 rows in set (0.00 sec)
```
![](https://github.com/JINxin-0505/homework/blob/master/picture/m1.png)

## 选择数据库

```sql
use b_dept;
Database changed
```

## 删除数据库

```sql
drop database b_dept;
Query OK, 0 rows affected (0.03 sec)
```
![](https://github.com/JINxin-0505/homework/blob/master/picture/m2.png)
