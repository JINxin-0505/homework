# 第二次作业
## 1.查看数据库中的存储引擎

```sql
show engines;
+--------------------+---------+----------------------------------------------------------------+--------------+------+------------+
| Engine             | Support | Comment                                                        | Transactions | XA   | Savepoints |
+--------------------+---------+----------------------------------------------------------------+--------------+------+------------+
| InnoDB             | DEFAULT | Supports transactions, row-level locking, and foreign keys     | YES          | YES  | YES        |
| MRG_MYISAM         | YES     | Collection of identical MyISAM tables                          | NO           | NO   | NO         |
| MEMORY             | YES     | Hash based, stored in memory, useful for temporary tables      | NO           | NO   | NO         |
| BLACKHOLE          | YES     | /dev/null storage engine (anything you write to it disappears) | NO           | NO   | NO         |
| MyISAM             | YES     | MyISAM storage engine                                          | NO           | NO   | NO         |
| CSV                | YES     | CSV storage engine                                             | NO           | NO   | NO         |
| ARCHIVE            | YES     | Archive storage engine                                         | NO           | NO   | NO         |
| PERFORMANCE_SCHEMA | YES     | Performance Schema                                             | NO           | NO   | NO         |
| FEDERATED          | NO      | Federated MySQL storage engine                                 | NULL         | NULL | NULL       |
+--------------------+---------+----------------------------------------------------------------+--------------+------+------------+
9 rows in set (0.01 sec)
```
![](https://github.com/JINxin-0505/homework/blob/master/picture/m3.png)

## 2.创建一个新的表

```sql
use db_test;
Database changed
mysql> create table stu_dept(
    -> id int,
    -> name varchar(20),
    -> loc varchar(40)
    -> );
Query OK, 0 rows affected (0.06 sec)
```

## 3.describe table 操作
 
```sql
describe stu_dept;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | int(11)     | YES  |     | NULL    |       |
| name  | varchar(20) | YES  |     | NULL    |       |
| loc   | varchar(40) | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
3 rows in set (0.01 sec)
```
![](https://github.com/JINxin-0505/homework/blob/master/picture/m4.png)

## 4.show tables 操作

```sql
show tables;
+-------------------+
| Tables_in_db_test |
+-------------------+
| a_dept            |
| stu_dept          |
| table_test        |
+-------------------+
3 rows in set (0.00 sec)
```
## 5.alter table 操作
### （1）修改表名

```sql
alter table stu_dept rename student_dept;
Query OK, 0 rows affected (0.03 sec)
```
![](https://github.com/JINxin-0505/homework/blob/master/picture/m5.png)

### （2）在表的最后一个位置增加字段

```sql
alter table student_dept
    -> add sex varchar(20);
Query OK, 0 rows affected (0.07 sec)
Records: 0  Duplicates: 0  Warnings: 0
```
![](https://github.com/JINxin-0505/homework/blob/master/picture/m6.png)

### （3）在表的第一个位置增加字段

```sql
alter table student_dept
    -> add age int first;
Query OK, 0 rows affected (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 0
```
![](https://github.com/JINxin-0505/homework/blob/master/picture/m7.png)

### （4）在表的第一个位置增加字段

```sql
 alter table student_dept
    -> add birth int
    -> after name;
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0
```
![](https://github.com/JINxin-0505/homework/blob/master/picture/m8.png)

### （5）删除字段

```sql
alter table student_dept
    -> drop age;
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0
```
![](https://github.com/JINxin-0505/homework/blob/master/picture/m9.png)

### （6）修改字段的数据类型

```sql
alter table student_dept
    -> modify birth varchar(20);
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0
```
![](https://github.com/JINxin-0505/homework/blob/master/picture/m10.png)

### （7）修改字段名字

```sql
alter table student_dept
    ->  change name dname varchar(20);
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0
```
![](https://github.com/JINxin-0505/homework/blob/master/picture/m11.png)

### （8）同时修改字段名字和属性

```sql
alter table student_dept
    -> change id number varchar(20);
Query OK, 0 rows affected (0.06 sec)
Records: 0  Duplicates: 0  Warnings: 0
```
![](https://github.com/JINxin-0505/homework/blob/master/picture/m12.png)

### （9）修改字段顺序

```sql
alter table student_dept
    -> modify number varchar(20) after loc;
Query OK, 0 rows affected (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 0
```
![](https://github.com/JINxin-0505/homework/blob/master/picture/m13.png)

## 6.drop删除表

```sql
drop table student_dept;
Query OK, 0 rows affected (0.01 sec)
```
![](https://github.com/JINxin-0505/homework/blob/master/picture/m14.png)

## 7.NOT NULL 操作
 
```sql
create table stu_dept(
    -> id int not null,
    -> name varchar(20),
    -> loc varchar(20)
    -> );
Query OK, 0 rows affected (0.03 sec)
```
![](https://github.com/JINxin-0505/homework/blob/master/picture/m15.png)

## 8.UNIQUE 操作

```sql
create table st_dept(
    -> id int unique,
    -> name varchar(20),
    -> loc varchar(20)
    -> );
Query OK, 0 rows affected (0.03 sec)
```
![](https://github.com/JINxin-0505/homework/blob/master/picture/m16.png)

## 9.PRIMARY KEY操作
### （1）单字段主键

```sql
 create table s_dept(
    -> id int primary key,
    -> name varchar(20),
    -> loc varchar(20)
    -> );
Query OK, 0 rows affected (0.03 sec)
```
![](https://github.com/JINxin-0505/homework/blob/master/picture/m17.png)

### （2）多字段主键

```sql
create table d_dept(
    -> id int,
    -> name varchar(20),
    -> loc varchar(20),
    -> constraint pk_id_name primary key(id,name)
    -> );
Query OK, 0 rows affected (0.03 sec)
```
![](https://github.com/JINxin-0505/homework/blob/master/picture/m18.png)
