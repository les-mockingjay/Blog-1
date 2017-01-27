---
title: Maven
date: 2017-01-15 17:23:57
tags: Java
---


# 导语
> [Maven](http://baike.baidu.com/link?url=sSKvPv_McvkW5-iuiDXJkSKldmX-v614dcOJ_3qykvzFKxW_OyAWP1pXuvEBLOEUOkY2h939UWQ1e-b1w8sgkq)是一个向开发人员构建一个完整的生命周期框架同时创建报表，检查，构建和测试自动化设置的项目管理和综合工具。

# 目的
>向开发人员提供：  
>项目是可重复使用，易维护，更容易理解的一个综合模型。  
>插件或交互的工具，这种声明性的模式。

# Maven安装和配置
## Windows上安装Maven
**参考：**  
[在Windows上安装Maven](http://www.yiibai.com/maven/maven_environment_setup.html)：如何在 Windows 上安装 Maven，


## 启用Maven的代理访问
**参考：**  
[Maven启用代理访问](http://www.yiibai.com/maven/enable-proxy-setting-in-maven.html)：在 Maven 配置代理设置实现使用代理服务器连接互联网

# Maven术语
* [Maven本地资源库](http://www.yiibai.com/maven/maven-local-repository.html)    
* [Maven中央存储库](http://www.yiibai.com/maven/maven-central-repository.html)
* [如何从Maven远程存储库下载？](http://www.yiibai.com/maven/how-do-download-from-remote-repository-maven.html) 
* [如何添加远程库？](http://www.yiibai.com/maven/add-remote-repository-in-maven-pom-xml.html) 
* [Maven依赖机制](http://www.yiibai.com/maven/maven-dependency-to-download-library.html) 
* [定制库到Maven本地资源库](http://www.yiibai.com/maven/include-library-manully-into-maven-local-repository.html)

## Maven本地资源库  
>用来存储项目的依赖库，默认的文件夹是 “.m2” 目录，可能需要将其更改为另一个文件夹。

## Maven中央存储库
>是Maven用来下载所有项目的依赖库的默认位置。

## 如何从Maven远程存储库下载？
  
## 如何添加远程库？
>并非所有的库存储在Maven的中央存储库，很多时候需要添加一些远程仓库来从其他位置，而不是默认的中央存储库下载库。 
 
## Maven依赖机制  
>传统方式和Maven方式的依赖库的有区别

## 定制库到Maven本地资源库
>很多库仍然不支持 Maven的pom.xml的概念,有一个指南来说明如何包括“非Maven支持”库到 Maven 本地资源库中。

# 基于Maven项目和Eclipse IDE
* [使用Maven创建Java项目](http://www.yiibai.com/maven/create-a-java-project-with-maven.html)
* [转换基于Maven的Java项目支持Eclipse ID](http://www.yiibai.com/maven/convert-maven-java-project-to-support-eclipse.html)
* [使用Maven创建Web应用程序项目](http://www.yiibai.com/maven/create-a-web-application-project-with-maven.html)
* [转换基于Maven的Web应用程序支持Eclipse IDE](http://www.yiibai.com/maven/use-maven-to-create-a-dynamic-web-project-in-eclipse.html)
* [使用Maven模板创建项目](http://www.yiibai.com/maven/create-a-project-with-maven-template.html)
 
## 使用Maven创建Java项目
>使用 Maven来创建Java项目

## 转换基于Maven的Java项目支持Eclipse IDE
>转换基于Maven的Java项目来支持在 Eclipse IDE 中

## 使用Maven创建Web应用程序项目
>使用 Maven来创建Web应用程序项目。

## 转换基于Maven的Web应用程序支持Eclipse IDE
>转换基于Maven的Web项目来支持在 Eclipse IDE 中

## 使用Maven模板创建项目
>从 Maven 的模板来创建标准项目


# Maven基本操作
* [使用Maven构建项目](http://www.yiibai.com/maven/build-project-with-maven.html)
* [使用Maven清理项目](http://www.yiibai.com/maven/clean-project-with-maven.html)
* [使用Maven运行单元测试](http://www.yiibai.com/maven/run-unit-test-with-maven.html)
* [将项目安装到Maven本地资源库](http://www.yiibai.com/maven/install-project-into-maven-local-repository.html)
* [生成基于Maven的项目文档站点](http://www.yiibai.com/maven/generate-a-site-for-your-maven-based-project.html)
* [使用“mvn site-deploy”部署站点（WebDAV例子）](http://www.yiibai.com/maven/deploy-site-with-mvn-site-deploy-webdav-example.html)
* [部署基于Maven的war文件到Tomcat](http://www.yiibai.com/maven/deploy-maven-based-war-file-to-tomcat.html)

## 使用Maven构建项目
>“mvn package” 来构建项目

## 使用Maven清理项目
>“mvn clean” 来清理项目

## 使用Maven运行单元测试
>“mvn test” 来执行单元测试

## 将项目安装到Maven本地资源库
>“mvn install” 打包和部署项目到本地资源库

## 生成基于Maven的项目文档站点
>“mvn site” 来为项目生成信息文档站点

## 使用“mvn site-deploy”部署站点（WebDAV例子）
>“mvn site-deploy” 通过WebDAV部署自动生成的文档站点到服务器

## 部署基于Maven的war文件到Tomcat
>“mvn tomcat:deploy” 以 WAR 文件部署到 Tomcat
