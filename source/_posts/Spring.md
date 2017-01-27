---
title: Spring
date: 2017-01-23 02:34:32
tags: Java
---
# 介绍
## Spring简介
### 含义
1. Spring是一个轻量级控制反转(IoC)和面向切面(AOP)的容器框架.
2. Spring框架下实现多个子框架的组合，这些子框架之间可以彼此独立，也可以使用其它的框架方案加以代替,为J2EE应用提供了全方位的整合框架

### 目的
解决企业应用开发的复杂性
### 功能
使用基本的JavaBean代替EJB
### 范围
任何Java应用  
### Spring的优点
- 低侵入式设计，代码污染极低
- Write Once, Run Anywhere
- DI有效的降低了耦合度
- AOP提供了通用任务的集中管理
- ORM和DAO简化了对数据库访问

### 优点给开发带来的好处
- 可以有效组织中间层对象
- 使用统一的配置文件
- 促进良好编程习惯，减少编程代价
- 易于单元测试
- 使EJB成为一种备选
- 为数据存取提供了一致的框架


## Spring 的框架组成
### Spring的核心模块
- 核心容器(Spring Core)
- 应用上下文(Spring Context)
- AOP模块(Spring AOP)
- JDBC和DAO模块(Spring DAO)
- 对象实体映射（Spring ORM）
- Web模块(Spring Web)
- MVC模块(Spring Web MVC)

### 图解
![Spring的核心模块
](http://ojifsovoq.bkt.clouddn.com/image/jpg/Java/Spring%E7%9A%84%E6%A0%B8%E5%BF%83%E6%A8%A1%E5%9D%97.png)

## Spring 之 IOC与DI
### 含义
IOC（Inversion of Control，控制反转）是spring的核心，即由spring来负责控制对象的生命周期和对象间的关系
### IOC模式与传统模式的区别
- 传统开发模式：对象之间互相依赖
- IOC开发模式：IOC容器安排对象之间的依赖

### IOC理论的背景
![IOC理论的背景](http://ojifsovoq.bkt.clouddn.com/image/jpg/Java/IOC%E7%90%86%E8%AE%BA%E7%9A%84%E8%83%8C%E6%99%AF%20.png)

### 依赖注入（DI)
IOC的另外的名字叫做依赖注入（Dependency Injection),依赖注入就是由IOC容器在运行期间，动态地将某种依赖关系注入到对象之中

### 控制反转与依赖注入的关系
- 通过引入IOC容器，利用依赖关系注入的方式，实现对象之间的解耦
- IOC控制反转：说的是创建对象实例的控制权从代码控制剥离到IOC容器控制，实际就是你在xml文件控制，侧重于原理
- DI依赖注入：说的是创建对象实例时，为这个对象注入属性值或其它对象实例，侧重于实现

### IOC的好处
- 降低组件之间的耦合度
- 提高开发效率和产品质量
- 统一标准，提高模块的复用性
- 模块具有热插拔特性

## Spring 之 AOP
### AOP通俗的理解
一个组件A，不关心其他常用的服务组件B，但是这个组件A使用组件B的时候，不是组件A自身去调用，而是通过配置等其他方式，比如Spring中可以通过xml配置文件。A只关心自己的业务逻辑，具体A使用B的时候，配置文件去做，与具体的A组件无关。
### AOP的关键概念
- 切面 - Aspect
- 连接点 - Join Point
- 通知 - Advice
- 切入点 - Point Cut
- 引入 - Introduction
- 目标对象 - Target Object
- AOP代理 - AOP Proxy
- 织入 - Weaving

### AOP的原理
1. AOP 代理是由 AOP 框架动态生成的一个对象，该对象可作为目标对象使用  
2. AOP 代理所包含的方法与目标对象的方法如下图所示：
![AOP的原理剖析
](http://ojifsovoq.bkt.clouddn.com/image/jpg/Java/AOP%E7%9A%84%E5%8E%9F%E7%90%86%E5%89%96%E6%9E%90%20.png)

### AOP的存在价值
AOP 专门用于处理系统中分布于各个模块中的交叉关注点的问题，在 Java EE 应用中，常常通过 AOP 来处理一些具有横切性质的系统级服务，如事务管理、安全检查、缓存、对象池管理等。
![AOP的存在价值](http://ojifsovoq.bkt.clouddn.com/image/jpg/Java/AOP%E7%9A%84%E5%AD%98%E5%9C%A8%E4%BB%B7%E5%80%BC.png)

# 入门示例
## 开发环境搭建
### Spring核心开发包
在建立Spring工程的时候，需要引入Spring的开发包，否则无法建立Spring的开发和运行环境

- Spring Core
- Spring Beans
- Spring AOP
- Spring Context

### Spring辅助开发包
提供了各种企业级服务 

- Spring Aspects 
- Spring Context Support
- Spring Expression
- Spring Framework Bom
- Spring Instrument
- Spring Instrument Tomcat
- Spring JDBC
- Spring JMS
- Spring orm
- Spring oxm
- Spring Struts
- Spring test
- Spring tx
- Spring web
- Spring webmvc
- Spring webmvc portlet
 
### 下载链接
[http://www.eclipse.org/downloads/packages/eclipse-ide-java-ee-developers/lunasr2](http://www.eclipse.org/downloads/packages/eclipse-ide-java-ee-developers/lunasr2)
[http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html)
[http://www.eclipse.org/downloads/packages/eclipse-ide-java-ee-developers/lunasr2](http://www.eclipse.org/downloads/packages/eclipse-ide-java-ee-developers/lunasr2)  
[http://projects.spring.io/spring-framework/](http://projects.spring.io/spring-framework/)

## 创建示例工程
### 步骤
1. 建立Spring工程
2. 编写Java文件
3. 编写配置文件
4. 运行示例工程

### 建立Spring工程
需要在Eclipse中建立一个普通Java工程，然后引入Spring的核心jar文件到工程中，其中标注起来的为核心jar文件
![Spring的核心jar文件](http://ojifsovoq.bkt.clouddn.com/image/jpg/Java/Spring%E7%9A%84%E6%A0%B8%E5%BF%83jar%E6%96%87%E4%BB%B6.png)

### 编写Java文件
工程中逐个建立Java文件：  

- IHelloMessage：一个接口，用于定义输出问候信息
- HelloWorld：接口的实现类，向用户输出“Hello everybody”信息
- HelloChina：接口的实现类，向用户输出“大家好！”信息
- Person：一个人物类，调用IHelloMessage接口，向用户输出问候信息
- Main：程序的入口类，用于加载配置文件以及启动IOC容器，调用人物- 类，向用户输出问候信息

![Spring的核心jar文件](http://ojifsovoq.bkt.clouddn.com/image/jpg/Java/Spring%E5%88%9B%E5%BB%BA%E7%A4%BA%E4%BE%8B%E5%B7%A5%E7%A8%8B_%E7%BC%96%E5%86%99Java%E6%96%87%E4%BB%B6%20.png)

### 编写配置文件
建立配置文件helloMessage.xml文件  
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE beans PUBLIC "-//SPRING/DTD BEAN/EN" "http://www.springframework.org/dtd/spring-beans.dtd">
<beans>
	<bean id="helloWorld" class="com.jike.spring.chapter01.HelloWorld"></bean>
	<bean id="helloChina" class="com.jike.spring.chapter01.HelloChina"></bean>
	<bean id="person" class="com.jike.spring.chapter01.Person">
	    <property name="helloMessage" ref="helloChina"/>
	</bean>
</beans>
```
### 运行示例工程
1. 确认程序输出是否正常
2. 通过配置文件，来控制人的输出信息
3. 当人在国内时，是否输出了“大家好！”的信息
4. 当人在国外时，是否输出了“Hello everybody！”的信息


# IoC 容器深入理解 
# 配置文件讲解
# 简化 Spring XML 的配置 
# 注解技术详解
# Spring表达式语言
# AOP概述 
# Spring AOP 之增强
