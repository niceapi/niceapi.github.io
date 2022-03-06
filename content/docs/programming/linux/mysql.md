---
title: "Mysql"
weight: 3
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---
## 启动Mariadb

测试启动：
```bash
mariadbd
# or mysqld
mysqladmin --version
```

相关命令：
```bash
systemctl start mariadb  #启动MariaDB
systemctl stop mariadb  #停止MariaDB
systemctl restart mariadb  #重启MariaDB
systemctl enable mariadb  #设置开机启动
```

打开mysql客户端：
```bash
# 无密码登陆
mysql
# 指定账户密码登陆
mysql -h [host] -u [user] -p
```

## 创建、删除数据库

```sql
CREATE DATABASE [NAME];
DROP DATABASE [NAME];
USE [NAME];
SHOW DATABASES;
```

## 数据类型

### 数值

|类型|范围都是一样，，有符号要减一半分去负数那边|
|-|-|
|TINYINT|无符号：0~255, 有符号：-128~127|
|SMALLINT|65535|
|MEDIUMINT|16777215|
|INT|4294967295|
|BIGINT|18446744073709551615|
|FLOAT|别管了，精度低用这个速度快|
|DOUBLE|总之你用不完，精度高用这个数度快|
|DECIMAL|

### 时间

|类型|格式|用途|
|-|-|-|
|DATE|YYYY-MM-DD|日期值|
|TIME|HH:MM:SS|时间值|
|YEAR|YYYY|年值（1901~2155）|
|DATETIME|YYYY-MM-DD HH:MM:SS|混合日期和时间值|
|DATESTAMP|YYYYMMDD HHMMSS|时间戳|


### 字符串

|类型|大小（单位：bytes）|用途|
|-|-|-|
|CHAR|0-255|定长字符串|
|VARCHAR|0-65535|变长字符串|
|TINYBLOB|0-255|不超过 255 个字符的二进制字符串|
|TINYTEXT|0-255|短文本字符串|
|BLOB|0-65535|二进制形式的长文本数据|
|TEXT|0-65535|长文本数据|
|MEDIUMBLOB|0-16777|二进制形式的中等长度文本数据|
|MEDIUMTEXT|0-16777|中等长度文本数据|
|LONGBLOB|0-4294967295|二进制形式的极大文本数据|
|LONGTEXT|0-4294967295|极大文本数据|

## 创建、删除表

创建表语法：
```sql
CREATE TABLE table_name (column_name column_type);
```

创建表示例：
```sql
CREATE TABLE IF NOT EXISTS 'runoob_tbl'(
   'runoob_id' INT UNSIGNED AUTO_INCREMENT,
   'runoob_title' VARCHAR(100) NOT NULL,
   'runoob_author' VARCHAR(40) NOT NULL,
   'submission_date' DATE,
   PRIMARY KEY ( 'runoob_id' )
)ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

删除表语法：
```sql
DROP TABLE table_name ;
```

## 增删改查

###  插入

```sql
INSERT INTO table_name 
( field1, field2,...fieldN )
VALUES
( value1, value2,...valueN );
```

###  删除

```sql
DELETE FROM table_name [WHERE Clause]
```

###  修改

```sql
UPDATE table_name SET
field1=new-value1,
field2=new-value2
[WHERE Clause]
```

### 查询

```sql
SELECT column_name,column_name
FROM table_name
[WHERE Clause] -- 条件
[LIMIT N] -- 数量
[OFFSET M] -- 偏移量
```

## 导出数据

### 导出文本格式数据

```sql
mysql> SELECT * FROM runoob_tbl 
    -> INTO OUTFILE '/tmp/runoob.txt';
```

### 导出SQL格式的数据

```bash
$ mysqldump -u root -p RUNOOB runoob_tbl > dump.txt
password ******
```

## 导入数据

### `mysql`命令导入

```bash
# mysql -uroot -p123456 < bak.sql
```


### 使用`LOAD DATA`导入数据

```sql
mysql> LOAD DATA LOCAL INFILE 'dump.txt' INTO TABLE mytbl;
```

### 使用`mysqlimport`导入数据

```bash
$ mysqlimport -u root -p --local mytbl dump.txt
password *****
```
