# **MySQL**

這篇文章協助大家學習 MySQL 這套資料庫管理系統，並利用 MySQL Workbench 練習如何儲存、搜尋、排序及檢索資料。

# Introduction

MySQL 是一套快速、功能強大的資料庫管理系統。所謂資料庫管理系統（Database Management System, 簡稱為 DBMS），它是透過一組程式模組來組織、管理、儲存和讀取資料庫的資料，任何使用者在操作資料庫時，都需要透過資料庫管理系統來處理。

# 重點整理

```sql
# key1:連線到資料庫
=>mysql -h 127.0.0.1 -u root -p;

# key2:建立資料庫　CREATE DATABASE `資料庫名`;
=>CREATE DATABASE `rdpapashop`;

# key3:查詢目前有那些資料庫
=>show databases;

# key4:查詢目前預設的資料庫
=>SELECT DATABASE();

# key5:使用資料庫　USE `資料庫名`;
=>use `rdpapashop`;

# key6:刪除資料庫　DROP DATABASE 資料庫名;
=>DROP DATABASE `rdpapashop`;

# key7:顯示目前資料庫支持的CHARACTER SET;
=>SHOW CHARACTER SET;

# key8:顯示目前資料庫支持的COLLATION;
=>SHOW COLLATION;

# key9:顯示目前資料庫資料庫版本;
=>select version();

# key10:顯示目前登入使用者;
=> select user();

# key11:顯示目前資料庫支援的儲存引擎;
=>  show engines;
```

# Usage

建立/刪除 test1 資料庫
```sql
create database test1;
use test1;
show tables;
drop database test1;
```

建立/刪除 mytable 資料表
```sql
create table mytable(school char(5),name char(10),id int);
show tables;
describe mytable;
drop table mytable;
```

## 常用語法

資料表查詢
```sql
select * from mytable ;
```

新增資料
```sql
insert into mytable(school, name, id) values ('NCTU','Jerry','123');
insert into mytable values ('NCTU','Jerry','123');
```

更新資料
```sql
update mytable set name = 'HaHa' where id = '123';
```

刪除資料
```sql
delete from mytable where name = 'HaHa';
```

資料表查詢+條件+排序 (DESC 代表由大到小排序)
```sql
select * from mytable where id = '123' order by name DESC;
```

改變資料欄位 (加入時間記錄)
```sql
alter table mytable add column recordtime TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP;
```

# Reference

[MYSQL 8 教學–DAY01–資料庫 | 操作分享 | 學習筆記](https://rdpapa.tw/2020/09/01/mysql-8-traning-day01-database/)

[簡單的 MySQL 使用教學](https://jerrynest.io/mysql-tutorial/)