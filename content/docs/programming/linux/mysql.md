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
### 时间
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

## 插入
## 删除
## 修改
## 查询
