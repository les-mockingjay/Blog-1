---
title: Java笔记_进阶
date: 2017-01-18 02:09:45
tags: Java
---
# Java的继承
## 含义
一个对象获取的另一个对象属性的过程

## IS-A 关系
这个对象/类是一种类/接口的实例

### extends关键字
除了超类的私有属性外，它继承超类的所有属性
```Java
{
public class Animal{}
public class Mammal extends Animal{}
public class Reptile extends Animal{}
public class Dog extends Mammal{}
}
```    
  
### instanceof 关键字
判断左边对象/类是否为右边类/接口的实例 

```Java
interface Animal{}
class Mammal implements Animal{}
public class Dog extends Mammal{
   public static void main(String args[]){

      Mammal m = new Mammal();
      Dog d = new Dog();

      System.out.println(m instanceof Animal);
      System.out.println(d instanceof Mammal);
      System.out.println(d instanceof Animal);
   }
}
```
### implements关键字:
被使用的类从接口继承。接口永远不能凭借它的类进行扩展。

```Java
public interface Animal {}
public class Mammal implements Animal{}
public class Dog extends Mammal{}
```

### *注意*
Java只支持单一继承(extends 一个类)，但可以多实现(implements 一个或多个接口)
## HAS-A 关系
含义：某一类是否含有某一个东西
```Java
public class Vehicle{}
public class Speed{}
public class Van extends Vehicle{
	private Speed sp;
} 
```

 
# Java覆盖(重写)/重载
## 重载
### 含义
在同一个类中多个同名函数同时存在，具有不同的参数个数/类型。
### 重载的规则
①：在使用重载时只能通过相同的方法名、不同的参数形式实现。不同的参数类型可以是不同的参数类型，不同的参数个数，不同的参数顺序（参数类型必须不一样）；
②：不能通过访问权限、返回类型、抛出的异常进行重载；
③：方法的异常类型和数目不会对重载造成影响；

## 重写
### 含义
也叫覆盖，子类中定义一个与父类中方法同名同参数列表的方法。并将父类继承的方法重新定义，重新填写方法中的代码。
### 重写的规则
①：重写方法的参数列表必须完全与被重写的方法的相同,否则不能称其为重写而是重载.
②：重写方法的访问修饰符一定要大于被重写方法的访问修饰符（public>protected>default>private）。
③：重写的方法的返回值必须和被重写的方法的返回一致；
④：重写的方法所抛出的异常必须和被重写方法的所抛出的异常一致，或者是其子类；
⑤：被重写的方法不能为private，否则在其子类中只是新定义了一个方法，并没s有对其进行重写。
⑥：静态方法不能被重写为非静态的方法（会编译出错）。  

## 重写与重载的区别
>重载:本质是子类覆盖父类的方法
>重写:本质上是隐藏的父类，并且不调用，除非子类使用的重载方法中的super关键字。

## 例子
### 示例1
>b为一类动物的并运行在狗类中的move方法。
>编译时，检查是在引用类型。运行时，JVM计算出的对象类型和运行将属于特定对象的方法。 
 
```Java
class Animal{

   public void move(){
      System.out.println("Animals can move");
   }
}

class Dog extends Animal{

   public void move(){
      System.out.println("Dogs can walk and run");
   }
}

public class TestDog{

   public static void main(String args[]){
      Animal a = new Animal(); // Animal reference and object
      Animal b = new Dog(); // Animal reference but Dog object

      a.move();// runs the method in Animal class

      b.move();//Runs the method in Dog class
   }
}
```
```
Animals can move
Dogs can walk and run
```
### 示例2
>程序将抛出一个编译时错误，因为B的引用类型的动物没有一种方法
  
```Java  
class Animal{

   public void move(){
      System.out.println("Animals can move");
   }
}

class Dog extends Animal{

   public void move(){
      System.out.println("Dogs can walk and run");
   }
   public void bark(){
      System.out.println("Dogs can bark");
   }
}

public class TestDog{

   public static void main(String args[]){
      Animal a = new Animal(); // Animal reference and object
      Animal b = new Dog(); // Animal reference but Dog object

      a.move();// runs the method in Animal class
      b.move();//Runs the method in Dog class
      b.bark();
   }
}
```
```
TestDog.java:30: cannot find symbol
symbol  : method bark()
location: class Animal
                b.bark();
                 ^
```

## super关键字
### 作用
调用一个重载方法的超类版本，则使用super关键字
### 例子
```Java
class Animal{

   public void move(){
      System.out.println("Animals can move");
   }
}

class Dog extends Animal{

   public void move(){
      super.move(); // invokes the super class method
      System.out.println("Dogs can walk and run");
   }
}

public class TestDog{

   public static void main(String args[]){

      Animal b = new Dog(); // Animal reference but Dog object
      b.move(); //Runs the method in Dog class

   }
}
```
```Java
Animals can move
Dogs can walk and run
```


# Java多态性
## 含义
Java中，所有的Java对象是多态的,因任何对象可通过IS-A测试适合自己的类型和Object类。  
多态不严谨的说法是：继承是子类使用父类的方法，而多态则是父类使用子类的方法。一般，我们使用多态是为了避免在父类里大量重载引起代码臃肿且难于维护。

## 例子
>所有g的参考变量g,a,v,o 指向相同的Goat对象在堆中

```Java
Goat g = new Goat();
Animal a = g;
Vegetarian v = g;
Object o = g;
```
## 虚拟方法
### 含义
### 例子
①：Employee类
```Java
/* File name : Employee.java */
public class Employee
{
   private String name;
   private String address;
   private int number;
   public Employee(String name, String address, int number)
   {
      System.out.println("Constructing an Employee");
      this.name = name;
      this.address = address;
      this.number = number;
   }
   public void mailCheck()
   {
      System.out.println("Mailing a check to " + this.name
       + " " + this.address);
   }
   public String toString()
   {
      return name + " " + address + " " + number;
   }
   public String getName()
   {
      return name;
   }
   public String getAddress()
   {
      return address;
   }
   public void setAddress(String newAddress)
   {
      address = newAddress;
   }
   public int getNumber()
   {
     return number;
   }
}
```
②：假设扩展的Employee类

```Java
/* File name : Salary.java */
public class Salary extends Employee
{
   private double salary; //Annual salary
   public Salary(String name, String address, int number, double
      salary)
   {
       super(name, address, number);
       setSalary(salary);
   }
   public void mailCheck()
   {
       System.out.println("Within mailCheck of Salary class ");
       System.out.println("Mailing check to " + getName()
       + " with salary " + salary);
   }
   public double getSalary()
   {
       return salary;
   }
   public void setSalary(double newSalary)
   {
       if(newSalary >= 0.0)
       {
          salary = newSalary;
       }
   }
   public double computePay()
   {
      System.out.println("Computing salary pay for " + getName());
      return salary/52;
   }
}
```
③：输出

```Java
public class VirtualDemo
{
   public static void main(String [] args)
   {
      Salary s = new Salary("Mohd Mohtashim", "Ambehta, UP", 3, 3600.00);
      Employee e = new Salary("John Adams", "Boston, MA", 2, 2400.00);
      System.out.println("Call mailCheck using Salary reference --");
      s.mailCheck();
      System.out.println("
 Call mailCheck using Employee reference--");
      e.mailCheck();
    }
}
```
④：结果  
```Java
Constructing an Employee
Constructing an Employee
Call mailCheck using Salary reference --
Within mailCheck of Salary class
Mailing check to Mohd Mohtashim with salary 3600.0

Call mailCheck using Employee reference--
Within mailCheck of Salary class
Mailing check to John Adams with salary 2400.0
```
⑤：分析
>可实例化两种工资的对象。使用一个工资参考s，而使用其他的 Employee 引用e。调用 s.mailCheck() 时编译器看到 mailCheck() 在编译时Salary类，JVM 调用 mailCheck() 在 Salary类 在运行时。  
关于e调用 mailCheck() 是完全不同的，因为 e 是一个 Employee 引用。当编译器看到 e.mailCheck()，编译器看到在 Employee 类中的 mailCheck() 方法。  
在这里，在编译时，编译器使用mailCheck()员工，以验证这个语句。在运行时，但是，JVM调用 mailCheck() 在Salary类中。
>此行为被称为虚拟方法调用，并且该方法被称为虚拟方法 

# Java抽象
## 抽象类
### 含义
使用abstract关键字来声明一个类的抽象
### 例子
①：这个类是抽象的，但它仍然有三个字段，七种方法，和一个构造函数。
```Java
/* File name : Employee.java */
public abstract class Employee
{
   private String name;
   private String address;
   private int number;
   public Employee(String name, String address, int number)
   {
      System.out.println("Constructing an Employee");
      this.name = name;
      this.address = address;
      this.number = number;
   }
   public double computePay()
   {
     System.out.println("Inside Employee computePay");
     return 0.0;
   }
   public void mailCheck()
   {
      System.out.println("Mailing a check to " + this.name
       + " " + this.address);
   }
   public String toString()
   {
      return name + " " + address + " " + number;
   }
   public String getName()
   {
      return name;
   }
   public String getAddress()
   {
      return address;
   }
   public void setAddress(String newAddress)
   {
      address = newAddress;
   }
   public int getNumber()
   {
     return number;
   }
}
```
②：输出
```Java
/* File name : AbstractDemo.java */
public class AbstractDemo
{
   public static void main(String [] args)
   {
      /* Following is not allowed and would raise error */
      Employee e = new Employee("George W.", "Houston, TX", 43);

      System.out.println("
 Call mailCheck using Employee reference--");
      e.mailCheck();
    }
}
```
③：结果
```Java
Employee.java:46: Employee is abstract; cannot be instantiated
      Employee e = new Employee("George W.", "Houston, TX", 43);
                   ^
1 error
```
## 扩展抽象类
### 例子
①：以正常的方式扩展Employee类
```Java
/* File name : Salary.java */
public class Salary extends Employee
{
   private double salary; //Annual salary
   public Salary(String name, String address, int number, double
      salary)
   {
       super(name, address, number);
       setSalary(salary);
   }
   public void mailCheck()
   {
       System.out.println("Within mailCheck of Salary class ");
       System.out.println("Mailing check to " + getName()
       + " with salary " + salary);
   }
   public double getSalary()
   {
       return salary;
   }
   public void setSalary(double newSalary)
   {
       if(newSalary >= 0.0)
       {
          salary = newSalary;
       }
   }
   public double computePay()
   {
      System.out.println("Computing salary pay for " + getName());
      return salary/52;
   }
}
```
②：输出
>不能实例化一个新Employee，但如果我们实例化一个新的Salary 对象，Salary 对象将继承这三个字段，并从员工七种方法。  


```Java
/* File name : AbstractDemo.java */
public class AbstractDemo
{
   public static void main(String [] args)
   {
      Salary s = new Salary("Mohd Mohtashim", "Ambehta, UP", 3, 3600.00);
      Employee e = new Salary("John Adams", "Boston, MA", 2, 2400.00);

      System.out.println("Call mailCheck using Salary reference --");
      s.mailCheck();

      System.out.println("
 Call mailCheck using Employee reference--");
      e.mailCheck();
    }
}
```
③：结果
```Java
Constructing an Employee
Constructing an Employee
Call mailCheck using  Salary reference --
Within mailCheck of Salary class
Mailing check to Mohd Mohtashim with salary 3600.0

Call mailCheck using Employee reference--
Within mailCheck of Salary class
Mailing check to John Adams with salary 2400.
```
## 抽象方法
### 含义
有一个abstract关键字修饰的方法名，但没有方法体。签名后跟一个分号，而不是花括号。  

```Java
public abstract class Employee
{
   private String name;
   private String address;
   private int number;
   
   public abstract double computePay();
   
   //Remainder of class definition
}
```
### 声明抽象方法的两种方式
①：这个类是抽象的。如果一个类包含一个抽象方法的类必须是抽象的也是如此。  
②：所有子类必须要么重写抽象方法或者声明本身也为抽象。否则子类的方法依然是抽象的
### 示例
>如果Salary 在扩展Employee类，那么它是实现computePay() 方法

```Java
/* File name : Salary.java */
public class Salary extends Employee
{
   private double salary; // Annual salary
  
   public double computePay()
   {
      System.out.println("Computing salary pay for " + getName());
      return salary/52;
   }

   //Remainder of class definition
}
```

# Java封装
## 含义
一个类中使用private修饰，并通过公有方法提供接入字段的技术，任何类要访问的变量应该通过getter和setter方法​​访问它们
## 封装作用
代码不会破坏其他人谁使用我们的代码的代码的能力。有了这个功能封装提供了可维护性，灵活性和可扩展到我们的代码。
## 封装的好处
①一个类的字段可以只读作出或只写。  
②：一个类可以有完全控制什么是存储在它的字段。  
③：一类的用户不知道如何在类存储其数据。一个类可以改变一个字段的数据类型和类的使用者不需要更改任何其代码。

## 例子
①：封装类
```Java
/* File name : EncapTest.java */
public class EncapTest{

   private String name;
   private String idNum;
   private int age;

   public int getAge(){
      return age;
   }

   public String getName(){
      return name;
   }

   public String getIdNum(){
      return idNum;
   }

   public void setAge( int newAge){
      age = newAge;
   }

   public void setName(String newName){
      name = newName;
   }

   public void setIdNum( String newId){
      idNum = newId;
   }
}
```
②：EncapTest类的变量访问方式:
```Java
/* File name : RunEncap.java */
public class RunEncap{

   public static void main(String args[]){
      EncapTest encap = new EncapTest();
      encap.setName("James");
      encap.setAge(20);
      encap.setIdNum("12343ms");

      System.out.print("Name : " + encap.getName()+ 
                             " Age : "+ encap.getAge());
    }
}
```
③：结果
```Java
Name : James Age : 20
```

# Java接口
## 含义
接口是抽象方法的集合
  
## 接口与类的异同
### 异
- 类描述对象的属性和行为。接口包含一个类实现的行为。
- 不能实例化一个接口。
- 接口不包含任何构造函数.
- 所有在接口中的方法都是抽象的.
- 接口不能包含实例字段。可以出现在一个接口的唯一字段必须声明static和final.
- 接口不是由一个类扩展，它是由类实现.
- 一个接口可以扩展多个接口

### 同
- 接口可以包含任何数量的方法。  
- 接口被写在同一个 .java 扩展名的文件，并提供相应的文件的名称的接口的名称。  
- 接口的字节码会出现在一个 .class文件。  
- 接口出现在包中，及其相应的字节码文件必须相匹配的包名的目录结构。 
 
## 接口与类的关系
除非实现接口的类是抽象，接口中的所有方法必须在类中定义（接口中的方法都是抽象）

## 接口的特性
①：接口是隐式抽象的。声明一个接口，不需要使用abstract关键字.
②：在接口中的每个方法也隐式抽象的，所以abstract关键字不需要。
③：在接口中的方法是隐式公开的。 

## 声明接口
### 方法
interface关键字用于声明一个接口。
### 例子
```Java
/* File name : NameOfInterface.java */
import java.lang.*;
//Any number of import statements

public interface NameOfInterface
{
   //Any number of final, static fields
   //Any number of abstract method declarations
}
```
```Java
/* File name : Animal.java */
interface Animal {

   public void eat();
   public void travel();
}
```
## 接口的实现
>当一个类实现一个接口,如果类不执行该接口的所有行为，则该类须声明为abstract。
>类使用implements关键字来实现一个接口

### 实现接口的规则
①：一个类可以同时实现多个接口。
②：一个类只能扩展一个类，但实现多个接口。
③：一个接口可以扩展另一个接口，类似于一个类可以扩展另一个类中的方法。
### 重写接口中的方法的规则
①：检查型异常不应超过该接口的方法或那些由接口方法声明的子类中声明的那些其他的实现方法进行声明。
②：重写方法时，应保持接口的方法和相同的返回类型或子类型的签名。
③：一个实现类本身可以是抽象的，如果是这样的接口方法需要无法实施（实现）。
### 例子
```Java
/* File name : MammalInt.java */
public class MammalInt implements Animal{

   public void eat(){
      System.out.println("Mammal eats");
   }

   public void travel(){
      System.out.println("Mammal travels");
   } 

   public int noOfLegs(){
      return 0;
   }

   public static void main(String args[]){
      MammalInt m = new MammalInt();
      m.eat();
      m.travel();
   }
} 
```
```Java
Mammal eats
Mammal travels
```
## 扩展接口
### 含义
一个接口可以扩展另一个接口，类似于一个类可以扩展另一个类中的方法
extends关键字来扩展接口，及子接口继承父接口的方法。
### 例子
>由Hockey和Football接口扩展的Sports接口，Hockey接口有四种方法，但它继承了两个来自Sports，因此，实现Hockey类需要实现所有六个方法。同样地，一个实现Football 类需要定义从Football 的三种方法，并从Sports的两种方法

```Java
//Filename: Sports.java
public interface Sports
{
   public void setHomeTeam(String name);
   public void setVisitingTeam(String name);
}

//Filename: Football.java
public interface Football extends Sports
{
   public void homeTeamScored(int points);
   public void visitingTeamScored(int points);
   public void endOfQuarter(int quarter);
}

//Filename: Hockey.java
public interface Hockey extends Sports
{
   public void homeGoalScored();
   public void visitingGoalScored();
   public void endOfPeriod(int period);
   public void overtimePeriod(int ot);
}
```

## 扩展多个接口
### 含义
一个接口可以扩展多个父接口。extends关键字被使用一次，并且父接口在一个逗号分隔的列表中声明。

### 例子
>如果Hockey接口扩展两个Sports和Event

```Java
public interface Hockey extends Sports, Event
```
## 标签接口
### 含义
不带方法的接口被称为标记接口
### 作用
①：创建一个共同的父接口 
至于与事件监听器接口，这是由几十个Java API中的其他接口扩展，可以使用一个标记接口之间建立一组接口到一个共同的父接口。例如，当一个接口扩展事件监听器，则JVM知道这个特定的接口是要在一个事件的代理方案来使用。
②：增加了数据类型到类 
这种情况就是术语标签的由来。实现一个标记接口的类不需要定义任何方法（因为接口不具有任何），但通过类的多态性成为一个接口类型。

# Java包/package
## 含义
相关类型（类，接口，枚举和注解）提供访问保护和命名空间管理的分组
包常用小写名称，以避免与类，接口名称冲突
## 例子
①：一个接口放在包animals
```Java
/* File name : Animal.java */
package animals;

interface Animal {
   public void eat();
   public void travel();
}
```
②：把一个实现在同一个 animals 包
```Java
package animals;

/* File name : MammalInt.java */
public class MammalInt implements Animal{

   public void eat(){
      System.out.println("Mammal eats");
   }

   public void travel(){
      System.out.println("Mammal travels");
   } 

   public int noOfLegs(){
      return 0;
   }

   public static void main(String args[]){
      MammalInt m = new MammalInt();
      m.eat();
      m.travel();
   }
} 
```
③：结果
```Java
$ mkdir animals
$ cp Animal.class  MammalInt.class animals
$ java animals/MammalInt
Mammal eats
Mammal travels
```
## import 关键字
## 例子
## 软件包的目录结构
## 设置CLASSPATH系统变量

# Java数据结构
## 枚举
含义：
Enumeration接口本身不是一种数据结构但接口定义了检索的数据结构连续元素的一种手段。

## BitSet
### 含义
位集合类实现一组位或标志，可以设置和清除个别的
### 作用
在需要跟上一组布尔值的情况下非常有用，只分配一个位每个值，并设置或清除适当。  

## Vector - 矢量
含义：
类似于传统的Java数组，但它可以根据需要增长，以适应新的元素。在创建时在需要时自动增长

## Stack - 堆栈
含义：
Stack类实现元素的后进先出（LIFO）堆栈

## Dictionary - 字典
含义：
定义一个数据结构，映射键的值的抽象类
Dictionary类是定义一个数据结构，映射键的值的抽象类。通过特定的键，而不是一个整数索引来访问数据。
Dictionary类是抽象的，它仅提供了用于一个键映射数据结构的框架，而不是一个特定的实现

## Hashtable
含义：
提供了组织根据一些用户自定义键结构数据的方法
## Properties
含义：
属性是哈希表的一个子类。它是用来维持值列表，其中的关键是一个字符串，值也是一个字符串。

# Java集合框架
## 导语
集合框架包含以下内容
- 接口: 这些都是表示集合的抽象数据类型。接口允许其代表性细节的集合可以独立操作。在面向对象的语言，接口一般形成了一个等级。
- 实现，即类: 这些都是集合接口的具体实现。在本质上，它们是可重复使用的数据结构。
- 算法: 这些是执行有用的计算的方法，例如搜索和排序，在该实施集合接口的对象。说是多态的算法：也就是说，同样的方法可以在许多不同的适当的集合接口的实现中使用。

## 集合接口：
### 集合框架定义的接口
| SN | 接口及描述 |
|-|-|
|1 | [Collection 接口](http://www.yiibai.com/java/java_collection_interface.html)：这可以使用对象组的工作，它是在集合层次结构的顶层。|
|2 | [List 接口](http://www.yiibai.com/java/java_list_interface.html):这扩展集合和列表的一个实例存储元素的有序集合。|
|3 | [Set 接口](http://www.yiibai.com/java/java_set_interface.html):这扩大集合到处理集合，其中必须包含独特的元素|
|4 | [SortedSet 接口](http://www.yiibai.com/java/java_sortedset_interface.html):这扩展集合为处理有序集合|
|5 | [Map](http://www.yiibai.com/java/java_map_interface.html):这对应唯一键的值。|
|6 | [Map.Entry](http://www.yiibai.com/java/java_mapentry_interface.html):这说明在映射中的元素（一个键/值对）。这是一个内部Map类。|
|7 | [SortedMap](http://www.yiibai.com/java/java_sortedmap_interface.html):扩展映射Map，这样键维持升序排列。|
|8 | [Enumeration](http://www.yiibai.com/java/java_sortedmap_interface.html):这是传统的接口和定义，通过它可以枚举（获得一次一个）的对象集合的元素的方法。这个传统界面已经被取代了迭代器。|

## 集合类
### 含义
>实现Collection接口标准的集合类

### 标准的集合类汇总
>AbstractCollection, AbstractSet, AbstractList, AbstractSequentialList 和 AbstractMap 类提供的核心集合接口的框架实现，以最大限度地减少实现它们所需的工作

|SN|类及描述|  
|-|-|
|1| AbstractCollection:实现大多数的Collection接口。|  
|2| AbstractList:扩展AbstractCollection并实现最List接口。|  
|3| AbstractSequentialList:扩展AbstractList用于通过使用其元素的顺序而不是随机访问的集合。|  
|4| [LinkedList](http://www.yiibai.com/java/java_linkedlist_class.html):实现了一个链表通过扩展AbstractSequentialList。|
|5| [ArrayList](http://www.yiibai.com/java/java_arraylist_class.html):实现了一个动态数组通过扩展AbstractList。|
|6| AbstractSet:扩展AbstractCollection并实现大部分的Set接口。|
|7| [HashSet](http://www.yiibai.com/java/java_hashset_class.html):扩展AbstractSet 使用哈希表。|
|8| [LinkedHashSet](http://www.yiibai.com/java/java_linkedhashset_class.html):扩展HashSet，允许插入顺序迭代。|
|9| [TreeSet](http://www.yiibai.com/java/java_treeset_class.html):实现了一组存储在一个树。扩展AbstractSet。|
|10| AbstractMap: 实现大多数Map接口。|
|11| [HashMap](http://www.yiibai.com/java/java_hashmap_class.html):扩展AbstractMap使用一个哈希表。|
|12| [TreeMap](http://www.yiibai.com/java/java_treemap_class.html):扩展AbstractMap用一棵树。|
|13| [WeakHashMap](http://www.yiibai.com/java/java_weakhashmap_class.html):扩展AbstractMap使用一个哈希表和弱键。|
|14| [LinkedHashMap](http://www.yiibai.com/java/java_linkedhashmap_class.html):扩展HashMap，允许插入顺序迭代。|
|15| [IdentityHashMap](http://www.yiibai.com/java/java_identityhashmap_class.html):扩展AbstractMap并使用引用相等性比较文档时。|
### java.util定义的旧式类
|SN|类及描述|
|-|-|
|1|[Vector](http://www.yiibai.com/java/java_vector_class.html):这样就实现了动态数组。它类似于ArrayList，但有一些不同。|
|2|[Stack](http://www.yiibai.com/java/java_stack_class.html):堆栈是向量的一个子类，实现了一个标准的后进先出的堆栈。|
|3|[Dictionary](http://www.yiibai.com/java/java_dictionary_class.html):字典是代表一个键/值存储库，工作很像Map抽象类。|
|4|[Hashtable](http://www.yiibai.com/java/java_hashtable_class.html):Hashtable 哈希表是原来java.util中的一部分，是一个具体实现一个字典。|
|5|[Properties](http://www.yiibai.com/java/java_properties_class.html):Properties是哈希表的一个子类。它是用来维持值列表，其中键是一个字符串，值也是一个字符串。|
|6|[BitSet](http://www.yiibai.com/java/java_bitset_class.html):BitSet 类创建一个特殊类型的数组保存位值。此数组的大小可以根据需要增加。|

## 收集算法
### 集合框架定义所有算法的实现的列表
[The Collection Algorithms](http://www.yiibai.com/java/java_collection_algorithms.html)
### 注意
①：有几个方法可以抛出ClassCastException，当它尝试进行比较不兼容的类型时，或者抛出一个UnsupportedOperationException
②：集合定义了三个不可变的静态变量：EMPTY_SET，EMPTY_LIST和EMPTY_MAP
## 迭代器
### 含义
循环通过收集，获取或移除元素
### 迭代器方法及描述
[Java迭代器](http://www.yiibai.com/java/java_using_iterator.html)的实例方法的列表
### 注意
ListIterator扩展迭代器允许列表和元素的修饰双向遍历。
## 比较器
### 含义
以不同方式整理一个给定集合中所有数量或用于任何类（甚至类，我们不能修改）任何实例进行排序。
### 比较器方法及描述
<<<<<<< HEAD
[Java比较器](http://www.yiibai.com/java/java_using_comparator.html)的实例方法的列表

# Java Enumeration接口
## 含义
可通过该接口枚举（获得一次一个）的对象集合的元素的方法，已被迭代器取代 
## 枚举接口方法及描述
|SN|方法和描述|
|1|boolean hasMoreElements():
当实现，同时还有更多的元素来提取它必须返回true和false当所有的元素都被列举.|
|2|Object nextElement():
这将返回枚举中的下一个对象作为一种通用的对象引用.|
## 例子
①
```Java
import java.util.Vector;
import java.util.Enumeration;

public class EnumerationTester {

   public static void main(String args[]) {
      Enumeration days;
      Vector dayNames = new Vector();
      dayNames.add("Sunday");
      dayNames.add("Monday");
      dayNames.add("Tuesday");
      dayNames.add("Wednesday");
      dayNames.add("Thursday");
      dayNames.add("Friday");
      dayNames.add("Saturday");
      days = dayNames.elements();
      while (days.hasMoreElements()){
         System.out.println(days.nextElement()); 
      }
   }
}
```
②：结果
```Java
Sunday
Monday
Tuesday
Wednesday
Thursday
Friday
Saturday
```

# Java BitSet类
## 含义
用于创建一个特殊类型的数组保存位值，数组的大小可以根据需要增加
## BitSet类的2种构造函数
|SN|Methods|描述|
|1|BitSet()|创建一个默认位初始化为零|
|2|BitSet(int size)|指定它的初始大小，即比特，它可以容纳的数量|
## BitSet类的方法及描述
>BitSet中实现了Cloneable接口

|SN|Methods|描述|
|1|void and(BitSet bitSet)|与运算调用的内容BitSet中对象与那些指定bitSet。结果存放到调用对象。|
|2|void andNot(BitSet bitSet)|对于bitSet每1位，在调用BitSet中的相应位清零。|
|3|int cardinality()|返回设置位的调用对象的数量。|
|4|void clear()|所有位清零。|
|5|void clear(int index)|index指定的位清零。|
|6|void clear(int startIndex, int endIndex)|将从startIndex到endIndex清零。|
|7|Object clone()|重复调用BitSet中对象。|
|8|boolean equals(Object bitSet)|返回true如果调用位设置相当于一个在bitSet通过。否则，该方法返回false。|
|9|void flip(int index)|逆转由index指定的位。| 
|10	|void flip(int startIndex, int endIndex)|反转将从startIndex位到endIndex.|
|11	|boolean get(int index)|返回指定索引处的位的当前状态。|
|12	|BitSet get(int startIndex, int endIndex)|返回一个BitSet中，它包含的比特将从startIndex到endIndex.1。调用对象不被改变。|
|13	|int hashCode()|返回调用对象的哈希代码。|
|14	|boolean intersects(BitSet bitSet)|如果至少有一个对调用对象和bitSet内相应位为1，则返回true。|
|15|boolean isEmpty()|返回true如果在调用对象中的所有位均为零。|
|16	|int length()|返回到持有调用BitSet中的内容所需的比特数。这个值是由最后1位的位置决定的。|
|17	|int nextClearBit(int startIndex)|返回下个清零位的索引，（即，下一个零位），从由startIndex指定的索引开始|
|18	|int nextSetBit(int startIndex)|返回下一组位（即，下一个1比特）的索引，从由startIndex指定的索引开始。如果没有位被设置，则返回1。|
|19|void or(BitSet bitSet)|OR值调用的内容BitSet中对象，通过BitSet指定。结果被放置到调用对象。| 
|20|void set(int index)|设置由index指定的位。|
|21|void set(int index, boolean v)|设置由index指定在v. true为传递的值的位设置位，false则清除该位。|
|22|void set(int startIndex, int endIndex)|设置位将从startIndex到endIndex.1。|
|23	|void set(int startIndex, int endIndex, boolean v)|设置位从startIndex到endIndex.1，在真正传递的值v设置位，清除位为false|
|24	|int size()|返回位在调用BitSet中对象的数量。|
|25	|String toString()|返回字符串相当于调用BitSet中的对象。|
|26|void xor(BitSet bitSet)|在异或调用BitSet中对象的内容与由BitSet指定。结果存放到调用对象。|

## 例子
>几个通过这种数据结构支持的方法

```Java
import java.util.BitSet;

public class BitSetDemo {

  public static void main(String args[]) {
     BitSet bits1 = new BitSet(16);
     BitSet bits2 = new BitSet(16);
      
     // set some bits
     for(int i=0; i<16; i++) {
        if((i%2) == 0) bits1.set(i);
        if((i%5) != 0) bits2.set(i);
     }
     System.out.println("Initial pattern in bits1: ");
     System.out.println(bits1);
     System.out.println("
Initial pattern in bits2: ");
     System.out.println(bits2);

     // AND bits
     bits2.and(bits1);
     System.out.println("
bits2 AND bits1: ");
     System.out.println(bits2);

     // OR bits
     bits2.or(bits1);
     System.out.println("
bits2 OR bits1: ");
     System.out.println(bits2);

     // XOR bits
     bits2.xor(bits1);
     System.out.println("
bits2 XOR bits1: ");
     System.out.println(bits2);
  }
}
```
结果
```Java
Initial pattern in bits1:
{0, 2, 4, 6, 8, 10, 12, 14}
Initial pattern in bits2:
{1, 2, 3, 4, 6, 7, 8, 9, 11, 12, 13, 14}
bits2 AND bits1:
{2, 4, 6, 8, 12, 14}
bits2 OR bits1:
{0, 2, 4, 6, 8, 10, 12, 14}
bits2 XOR bits1:
{}
```

# Java Vector类
## 含义
向量类实现了一个动态数组。它类似于ArrayList 
*注意* :与Arraylist的区别
- Vector是同步的。
- 向量包含不属于集合框架的一部分许多传统方法。
## Vector类的4种构造函数
|SN|Methods|描述|
|1|Vector()|默认有10的初始大小的向量|
|2|Vector(int size)|创建其初始容量由size指定的向量|
|3|Vector(int size, int incr)|创建其初始容量是由大小和由incr指定的增量指定。增量指定元素的数目，以在每次分配该载体被向上调整|
|4|Vector(Collection c)|创建一个包含集合c的元素的向量|
=======
[Java比较器]()的实例方法的列表
## 总结


# Java Enumeration接口
## 导语 
## 例子：

# Java BitSet类
## 导语
## 例子：

# Java Vector类
## 导语 
>>>>>>> 9539ece9e3229e73ec73fcb77e78f46ba6a4758b
## 例子：

# Java Stack类
## 导语 
## 例子：

# Java Dictionary类
## 导语

# Java泛型
## 导语
## 泛型方法：
## 例子：
## 限制类型参数：
## 例子：
## 泛型类：
## 例子：
## 
## 

# Java Serialization/序列化/反序列化
## 导语
## 序列化对象：
## 反序列化对象：
 
# Java网络（Socket编程）
## 导语
## Socket 编程:
## ServerSocket类方法:
## Socket类方法：
## InetAddress类的方法：
## Socket Client 例子：
## Socket Server 例子：

# Java发送Email/邮件
## 导语
## 发送一个简单的电子邮件：
## 发送一个HTML电子邮件:
## 发送附件的电子邮件：
## 用户认证部分：

# Java多线程
## 导语
## 线程的生命周期：
## 线程的优先级：
## 创建线程：
## 通过实现Runnable创建线程：
## 例子：
## 通过扩展Thread创建线程：
## 例子：
## 线程方法：
## 例子：
## 主要线程概念：
## 使用多线程：

# Java文档注释
## 导语
## javadoc标签：
## 文档注释：
## javadoc输出
## 例子


