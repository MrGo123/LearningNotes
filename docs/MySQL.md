
### 认识三大概念
1. DB
DB是数据库(database)的缩写，数据库是存储数据的“仓库”，它保存了一系列有组织的数据。

2. DBMS
DBMS是数据库管理系统(Database Management System)的缩写，用于对数据库(DB)进行操作。

3. SQL
SQL是结构化查询语言(Structure Query Language)的缩写，专门用来与数据库进行通信的语言。

三者关系：使用SQL通过DBMS管理DB。

### 数据库相关基础知识
1. 表
![表](https://img.vim-cn.com/87/2a88a9718453e9b82f1570789eb7ccf1d20b65.png)

tips：
* 主键（primary key） ①一一列（或一组列），其值能够唯一区分表 中每个行。


### 命令行启动关闭MySQL

```shell
# 启动
net start mysql-name #后面部分为数据库名
# 关闭
net stop mysql-name #后面部分为数据库名
```

win命令行下登录MySQL

```shell
mysql -h localhost -P 端口 -u root -p"密码"  #localhost可修改为对应主机名。命令后部分可直接输入登录密码，紧挨-p。也可暂时不输入密码只要-p,执行后会进行隐藏式的密码输入
```

tips：另外可通过MySQL自带的客户端登录，但该客户端仅限root用户。

### 常用SQL命令
注意：命令结尾要加结束符 `;`或 `\g`。
```shell
# 显示所有数据库
show databases;

# 使用数据库
use 库名;

# 显示该数据库下的表
show tables;

# 查看当前所在库
select database();

# 在某库下查看别的库的表
show tables from 库名;

# 创建表
create table 表名 (
    列名 列类型,   #中间划分用逗号
    列名 列类型,
    ……
);

# 查看表结构
desc 表名;

```

### MySQL语法规范

1. 不区分大小写
建议关键字大写，表名、列名小写

2. 命令用分号 `;` 结尾

3. 注释
* 单行注释 用`#`
* 多行注释 用`/*注释文字*/`