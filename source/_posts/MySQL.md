---
title: MySQL
date: 2017-01-17 10:24:00
tags: 数据库  
---

# [MySQL安装](http://www.yiibai.com/mysql/mysql_installation.html) 
## 下载MySQL:
不同版本的下载链接：[官网MySQL下载](https://dev.mysql.com/downloads/mysql/)
![](http://ojifsovoq.bkt.clouddn.com/image/jpg/MySQL/MySQL%E5%AE%98%E7%BD%91%E4%B8%8B%E8%BD%BD.jpg)
## 安装MySQL在Linux/UNIX上
### 安装包
MySQL - MySQL数据库服务器，管理数据库和表，控制用户的访问，并处理SQL查询。
MySQL-client - MySQL客户端程序，这使得它可以连接到服务器并进行交互。
MySQL-devel - 库和头文件在编译使用MySQL的其他程序时使用。
MySQL-shared - 共享库的MySQL客户端。
MySQL-bench - MySQL数据库服务器的基准测试和性能测试工具。
### 步骤：
①：使用 root 用户登录系统。
②：切换到包含RPM的目录
③：执行以下命令来安装MySQL数据库服务器。 请使用 RPM 文件的名称替换文件名。
```bash
[root@host]# rpm -i MySQL-5.0.9-0.i386.rpm
```
## 安装MySQL在Windows上
### 步骤
①：在任何版本的 Windows 默认安装是现在比以前要容易得多，MySQL巧妙地打包安装程序。只需下载安装包，随地把它解压缩，并运行 mysql.exe.
![](http://ojifsovoq.bkt.clouddn.com/image/jpg/MySQL/Windows_MySQL%E5%AE%89%E8%A3%851.jpg)
![](http://ojifsovoq.bkt.clouddn.com/image/jpg/MySQL/Windows_MySQL%E5%AE%89%E8%A3%852.jpg)
②：提示下载保存文件，下载完成后（下载完成的文件是：mysql-5.6.25-winx64.zip）解压文件放到目录：D:\software 下，这是一个免安装包，这里不需要安装步骤。  
③：进入 D:\software\mysql-5.6.25-winx64\bin，然后输入mysqld.exe
![](http://ojifsovoq.bkt.clouddn.com/image/jpg/MySQL/Windows_MySQL%E5%AE%89%E8%A3%853.jpg)

## 验证MySQL安装
## 使用中mysqladmin工具程序来获取服务器状态
## 使用MySQL客户端执行简单的SQL命令
## 安装后的步骤：
## 在启动时运行MySQL的设置


# [MySQL管理](http://www.yiibai.com/mysql/mysql_administration.html)
## 运行和关闭MySQL服务器
## 设置MySQL用户帐户
## /etc/my.cnf 文件配置
## 管理 mysql 命令


# [MySQL数据类型](http://www.yiibai.com/mysql/mysql_data_types.html)
## 数字数据类型
## 日期和时间类型
## 字符串类型


## [MySQL创建数据库](http://www.yiibai.com/mysql/mysql_create_database.html)
#### 4.1.使用 mysqladmin创建数据库

# [MySQL删除数据库](http://www.yiibai.com/mysql/mysql_drop_database.html)
## 使用mysqladmin删除数据库

# [MySQL Use选择数据库](http://www.yiibai.com/mysql/mysql_select_database.html)
## 从命令提示符选择MySQL数据库

# [MySQL Create Table创建表](http://www.yiibai.com/mysql/mysql_create_tables.html)
## 语法
## 通过命令提示符来创建表


# [MySQL Drop Table删除表](http://www.yiibai.com/mysql/mysql_drop_tables.html)
## 语法
## 从命令行提示符删除表

# [MySQL Insert插入数据](http://www.yiibai.com/mysql/mysql_insert_query.html)
## 语法
## 从命令提示符插入数据

# [MySQL Select查询](http://www.yiibai.com/mysql/mysql_select_query.html)
## 语法
## 从命令提示符读取数据


# [MySQL Where子句](http://www.yiibai.com/mysql/mysql_where_clause.html)
## 语法
## 从命令行提示符读取数据


# [MySQL Update查询](http://www.yiibai.com/mysql/mysql_update_query.html)
## 语法
## 从命令提示符更新数据


# [MySQL Delete查询](http://www.yiibai.com/mysql/mysql_delete_query.html)
## 语法
## 从命令提示符删除数据

# [MySQL Like子句](http://www.yiibai.com/mysql/mysql_like_clause.html)
## 语法
## 在命令提示符使用LIKE子句

# [MySQL Order By排序结果](http://www.yiibai.com/mysql/mysql_sorting_results.html)
## 语法
## 在命令提示符使用ORDER BY子句

# [MySQL Join联接](http://www.yiibai.com/mysql/mysql_using_joins.html)
## 在命令提示符中使用联接

# [MySQL NULL值](http://www.yiibai.com/mysql/mysql_null_values.html)
## 在命令提示符，使用NULL值


# [MySQL正则表达式](http://www.yiibai.com/mysql/mysql_regexps.html)
## 格式


# [MySQL事务](http://www.yiibai.com/mysql/mysql_transactions.html)
## 事务性质
## 提交和回滚
## 关于事务通用示例
## 在MySQL的事务安全表类型


# [MySQL Alter命令](http://www.yiibai.com/mysql/mysql_alter_command.html)
## 删除，添加或重新定义列
## 更改列定义或名称
## ALTER TABLE影响Null和缺省值属性
## 更改列的默认值
## 更改表类型
## 重命名表


# [MySQL索引](http://www.yiibai.com/mysql/mysql_indexes.html)
## 简单和唯一索引
## 使用ALTER命令来添加和删除索引
## 使用ALTER命令来添加和删除PRIMARY KEY
## 显示索引信息

# [MySQL临时表](http://www.yiibai.com/mysql/mysql_temporary_tables.html)  
## 示例
## 删除临时表


# [MySQL复制表](http://www.yiibai.com/mysql/mysql-clone-tables.html)
## 示例
## 步骤


# [MySQL数据库信息](http://www.yiibai.com/mysql/mysql-database-info.html)
## 获取服务器元数据


# [MySQL序列的使用](http://www.yiibai.com/mysql/mysql-using-sequences.html)
## 使用AUTO_INCREMENT列
## 获取AUTO_INCREMENT值
## 重新编号序列
## 开始一个顺序在一个特定的值


# [MySQL重复处理](http://www.yiibai.com/mysql/mysql_handling_duplicates.html)
## 防止在一个表发生重复记录
## 统计和标识重复
## 从查询结果消除重记录
## 使用表的更换删除重复


# [MySQL SQL注入](http://www.yiibai.com/mysql/mysql-sql-injection.html)
## 防止SQL注入
## LIKE的困境


# [MySQL数据库导出（备份方法）](http://www.yiibai.com/mysql/mysql_database_export.html)
## 使用SELECT... INTO OUTFILE语句导出数据
## 导出表作为原始数据
## 以SQL格式导出表内容或定义
## 复制表或数据库到另一台主机


# MySQL实用函数
## [MySQL Group By 子句](http://www.yiibai.com/mysql/mysql-group-by-clause.html) 
>MySQL的GROUP BY语句以及SQL聚合函数，用于类似SUM提供某些数据库表的列来分组结果数据集
## [MySQL IN 子句](http://www.yiibai.com/mysql/mysql_in_clause.html) 
>这是一个子句，它可以用来连同任何MySQL查询语句以指定条件
## [MySQL BETWEEN 子句](http://www.yiibai.com/mysql/mysql-between-clause.html)
>这是一个子句，它可以用来与任何MySQL查询来指定条件
## [MySQL UNION关键字](http://www.yiibai.com/mysql/mysql-union-keyword.html)
>使用UNION操作多个结果集组合成一个结果集
## [MySQL COUNT()函数](http://www.yiibai.com/mysql/mysql-count-function.html) 
>MySQL的COUNT聚合函数用于计算一个数据库表中的行数
## [MySQL MAX() 函数](http://www.yiibai.com/mysql/mysql-max-function.html)
>MySQL的MAX聚合函数允许我们选择某些列的最高(最大)值
## [MySQL MIN()函数](http://www.yiibai.com/mysql/mysql-min-function.html)
>MySQL的MIN聚合函数允许我们选择某些列的最低(最小)值
## [MySQL Avg()函数](http://www.yiibai.com/mysql/mysql-avg-function.html)
>MySQL的AVG聚合函数是用来对某些表的列求它的平均值
## [MySQL SUM()函数](http://www.yiibai.com/mysql/mysql-sum-function.html)
>MySQL的SUM聚合函数允许选择某列的总和
## [MySQL SQRT函数](http://www.yiibai.com/mysql/mysql-sqrt-function.html)
>这是用来生成给定数的平方根
## [MySQL RAND()函数](http://www.yiibai.com/mysql/mysql-rand-function.html) 
>使用MySQL命令产生一个随机数
## [MySQL CONCAT()函数](http://www.yiibai.com/mysql/mysql-concat-function.html)
>这是用来连接MySQL命令中的任何字符串
## [MySQL数字函数](http://www.yiibai.com/mysql/mysql-numeric-functions.html)
>在MySQL中操作数字的MySQL函数完整列表
