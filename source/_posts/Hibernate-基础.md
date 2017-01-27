---
title: Hibernate_基础
date: 2017-01-25 22:42:04
tags:
---
# 第一个 Hibernate 应用
## Hibernate开发环境的搭建
### MySQL下载、安装及配置
1. 下载MySQL
	http://dev.mysql.com/downloads/mysql/
	根据自己的操作系统选择适合的MySQL版本
2. 安装MySQL
3. 配置远程访问MySQL

```sql
	mysql>use mysql;
	mysql>update user set host = '%' where user = 'root';
	mysql>select host, user from user;
	mysql>FLUSH PRIVILEGES;

```
### Maven下载、安装及配置
1. 下载[Maven](http://maven.apache.org/download.cgi)	
2. 安装Maven
3. 配置Maven
	设置MAVEN_HOME环境变量
	更新path环境变量，添加【;%MAVEN_HOME%\bin;】到尾部
	注意：安装maven前请确保已安装JDK并成功配置其环境变量
4. 验证  
  `mvn -v`

## 使用Maven管理项目
### 效果展示
![Maven管理项目_效果展示](http://ojifsovoq.bkt.clouddn.com/image/jpg/Hibernate/Maven%E7%AE%A1%E7%90%86%E9%A1%B9%E7%9B%AE_%E6%95%88%E6%9E%9C%E5%B1%95%E7%A4%BA.png)
### Maven仓库
#### 仓库解决的问题
没有 Maven 时，项目用到的 .jar 文件通常需要拷贝到 /lib 目录，项目多了，拷贝的文件副本就多了，占用磁盘空间，且难于管理。
#### 仓库的含义
Maven 使用一个称之为仓库的目录，根据构件的坐标统一存储这些构件的唯一副本，在项目中通过依赖声明，可以方便的引用构件。
#### 仓库的布局
构件都有唯一的坐标，Maven 根据坐标管理构件的存储。
如以下对 javax.servlet-api-3.1.0 的存储： 
文件路径对应了：groupId/artifactId/version/artifactId-version.packaging
![Maven仓库的布局](http://ojifsovoq.bkt.clouddn.com/image/jpg/Hibernate/Maven%E4%BB%93%E5%BA%93%E7%9A%84%E5%B8%83%E5%B1%80.png)
#### 仓库的分类
- Maven 仓库分为本地仓库和远程仓库，寻找构件时，首先从本地仓库找，找不到则到远程仓库找，再找不到就报错。
- 在远程仓库中找到了，就下载到本地仓库再使用。
- 中央仓库是 Maven 核心自带的远程仓库。
- 除了中央仓库，还有其它很多公共的远程仓库。

##### 本地仓库：
Maven 本地仓库默认地址为：${user.home}/.m2/repository。
通过修改 %MAVEN_HOME%/conf/settings.xml （或者：${user.home}/.m2/settings.xml，针对当前用户（推荐））配置文件可以更改本地仓库的位置。

##### 中央仓库：
安装完 Maven ，本地仓库几乎是空的，这时需要从远程仓库下载所需构件。
Maven 配置了一个默认的远程仓库，即中央仓库。
找到 %MAVEN_HOME%/lib/maven-model-builder-3.2.1.jar，在org/apache/maven/model/pom-4.0.0.xml 超级POM中有默认的中央仓库地址。

### Maven坐标
>maven 的所有构件均通过坐标进行组织和管理。maven 的坐标通过 5 个元素进行定义，其中 groupId、artifactId、version 是必须的，packaging 是可选的（默认为jar），classifier 是不能直接定义的。

- groupId：定义当前 Maven 项目所属的实际项目，跟 Java 包名类似，通常与域名反向一一对应。
- artifactId：定义当前 Maven 项目的一个模块，默认情况下，Maven 生成的构件，其文件名会以 artifactId 开头，如 javax.servlet-api-3.1.0.jar。
- version：定义项目版本。
- packaging：定义项目打包方式，如 jar，war，pom，zip ……，默认为 jar。

### Maven依赖




### 
## 创建第一个Hibernate应用helloapp