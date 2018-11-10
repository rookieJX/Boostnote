## MySQL语句初体验

#### 1.概念

数据库 -> 文件
数据库表 -> 文件
数据行 -> 文件中的一行数据


``` sequence
Title: 数据库概念
数据库 -> 文件夹 : 对应
数据库表 -> 文件: 对应
数据行 - > 文件中的一行数据: 对应
```
#### 2.初始化

- show databases;

> 查看当前MySQL都有哪些数据，根据目录都有哪些文件夹
> 
- create database 数据库名;

> 创建文件夹
> 
- use 数据库名;

> 使用选中数据库，进入目录
> 
- show tables;

> 查看当前数据库下都有哪些表
> 
- create table 表名(nid int, name varchar(20),pwd varchar(64));

> 创建数据库表