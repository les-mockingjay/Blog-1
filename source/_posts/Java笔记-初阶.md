---
title: Java笔记_初阶
date: 2017-01-20 00:48:15
tags:
---
# Java JDK安装和配置
# Java基本语法
## 
**对象**  对象具有状态和行为。对象是类的实例。
**类** 一个类可以被定义为描述行为的模板/蓝色印花/指出其类型支持的对象。
**方法** 一种方法，基本上是一个行为。一个类可以包含许多方法。它是在将逻辑写入时，数据操纵和所有的动作被执行的方法。
**实例变量** 每个对象都有其独特的实例变量。一个对象的状态是由分配给这些实例变量的值来创建。
## 基本语法
- 大小写敏感性 
- 类名称 ：所有的类名首字母应该大写。若几个单词来构成类的名称，每个内部单词的第一个字母应该大写。
- 方法名称： 方法名以小写字母开头。若几个单词来构成方法的名称，每个内部单词的第一个字母应该大写。如 myMethodName()
- 程序文件名：程序文件的名称与类的名称完全匹配。保存文件时，应该使用类名（请记住Java是大小写敏感）并添加 '.java'的名称的末尾（如果该文件名和类名不符合程序将无法编译）保存。  如: 假设'MyFirstJavaProgram“是类名。该文件应保存为 'MyFirstJavaProgram.java'
- public static void main(String args[])：Java程序处理从main（）方法开始，这是每一个Java程序的强制性部分入口

## Java标识符
- 所有的标识符应该以一个字母（A至Z或a到z），货币字符（$）或下划线（_）。
- 之后的第一个字符的标识符可以具有字符的任意组合。
- 关键字不能被用作标识符。
- 标识符是区分大小写的。

合法标识符的例子: age, $salary, _value, __1_value  
非法标识符的例子s: 123abc, -salary

## Java修饰符
- 访问修饰符: default, public , protected, private
- 非访问修饰符: final, abstract, strictfp

## Java变量
- 局部变量
- 类变量（静态变量）
- 实例变量（非静态变量）

## Java数组
存储相同类型的多个变量的东东

## Java 关键字
![Java 关键字](http://ojifsovoq.bkt.clouddn.com/image/jpg/Java/Java%20%E5%85%B3%E9%94%AE%E5%AD%97.png)

# Java对象和类
## Java对象
含义：
具有状态和行为的事物

## Java的类
### 含义
描述一类对象行为和属性的模板

### 类可包含的变量类型
- 局部变量：方法里面，构造函数或块中定义的变量称为局部变量。该变量将被声明和初始化的方法中，当该方法完成该变量将被销毁。
- 实例变量: 实例变量都在一个类，但任何方法之外的变量。这些变量在类被加载的实例化。实例变量可以从内部的任何方法，构造函数或特定类别的块访问。
- 类变量: 类变量是在一个类中声明，任何方法之外的变量，用static关键字。

## 构造函数：
###
每个类都有一个默认的构造函数，或可以有多个构造函数。
### 例子

```Java
public class Puppy{
   public Puppy(){
   }

   public Puppy(String name){
      // This constructor has one parameter, name.
   }
}
```
## Java单例类
### 目的
Java单例的目的是控制对象的创建，数量限制
### 例子1
①:代码
```Java
public class Singleton {

   private static Singleton singleton = new Singleton( );
   
   /* A private Constructor prevents any other 
    * class from instantiating.
    */
   private Singleton(){ }
   
   /* Static 'instance' method */
   public static Singleton getInstance( ) {
      return singleton;
   }
   /* Other methods protected by singleton-ness */
   protected static void demoMethod( ) {
      System.out.println("demoMethod for singleton"); 
   }
}

public class SingletonDemo {
   public static void main(String[] args) {
      Singleton tmp = Singleton.getInstance( );
      tmp.demoMethod( );
   }
}
```
②：结果
```Java
demoMethod for singleton
```
### 例子2
①：代码
```Java
public class ClassicSingleton {
   private static ClassicSingleton instance = null;
   protected ClassicSingleton() {
      // Exists only to defeat instantiation. by www.yiibai.com
   }
   public static ClassicSingleton getInstance() {
      if(instance == null) {
         instance = new ClassicSingleton();
      }
      return instance;
   }
}
```
②：分析
>ClassicSingleton类维护一个孤独的单例实例的静态引用，并返回从静态getInstance()方法参考.
这里ClassicSingleton类采用的技术被称为惰性的实例创建的单例;作为一个结果，直到第一次调用getInstance()方法不创建Singleton实例。此方法可确保只在需要时创建单例实例.
创建对象：
# Java方法
# Java基本数据类型
# Java变量类型
# Java修饰符类型
# Java基本运算符
# Java循环for, while和do...while
# Java决策制定
# Java Numbers类
# Java String类
# Java修饰符
# Java枚举
# Java注解
# Java日期时间
# Java数组
# Java日期时间(Date/Time)
# Java正则表达式
# Java字符流
# Java二进制流
# Java流，文件和I/O
# Java String, StringBuffer和StringBuilder实例
# Java异常处理
# Java异常处理实例教程
# Java抽象类和接口
# Java的比较和排序
# Java泛型实例
# Java集合框架实例
# Java正则表达式实例教程
# Java多线程编程教程
# Java JDBC连接各种数据库实例
# Eclipse安装和配置 