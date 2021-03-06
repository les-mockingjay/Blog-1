---
title: Java基础
date: 2017-01-23 02:29:17
tags: Java
---
# Java的3种错误类型  
程序的错误分为编译期语法错误、运行期异常错误和运行期逻辑错误。  

- 编译错误:可以借助Eclipse的帮助方便地定位错误，并进行修改。
- 运行期异常:系统会提示错误的类型和出错的位置
- 逻辑错误:指程序可以编译运行，但程序执行的结果却不是预期的效果。


# 进制转换：二进制、八进制、十进制、十六进制互转
## 进制概述
Java代码中十六进制数用0X或0x做前缀,八进制数用0做前缀(0是数字零，而不是字母O)

## 进制规律
### 二进制<-->十进制：  
- --->  
从右至左分别算出2的位数减1次幂，再将所有结果求和
- <---  
 不断除以2，保留余数，商为0时不再除2，将所有余数倒序排列。
 
### 二进制<-->十六/八进制：  
   - --->   
十六进制0-15对应十进制的0-F  
0 1 2 3 4 5 6 7 8 9 A  B  C  D  E  F  
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15   
八进制0-8对应十进制的0-8  
0 1 2 3 4 5 6 7 8  
0 1 2 3 4 5 6 7 8  
以每4位二进制数隔开作为1位十六进制数，求出每1位十六进制数  
以每3位二进制数隔开作为1位八进制数，求出每1位八进制数
将十六/八进制数**合并**（不是相加）  
   - <---  
 以每4位二进制数隔开作为1位十六进制数，求出每1位十六进制数  
 以每3位二进制数隔开作为1位八进制数，求出每1位八进制数
 
### 十进制<-->十六/八进制
- --->  
求几进制就将十进制数除以几
- <---  
先转换成二进制在转换成十进制

## 二进制补码
### 补码规则
- Java程序中输入的十进制的数据都会被自动转换为二进制，Java内部也以二进制来进行数值运算，但返回的结果是十进制
- 二进制的最高位是符号位，0表示正数，1表示负数。
- 正数的值是其本身，负数的值是最高位(符号位)不变，其它位逐位取反，再加1。
- 两数相加，若最高位（符号位）有进位，则进位被舍弃。  

### 补码作用
- 可以将符号位和其它位统一处理；
- 最高位不再表示数值，而是作为符号位，正好将数值折半，即一半是0至正数，一半是负数。  
例如：  
(1)4位二进制数共有16个数，用补码表示，则一半是0～7,一半是-1～-8。  
(2)8位二进制数共有256个数，用补码表示，则一半是
0～127,一半是-1~-128。

### 补码运算的特征原理
- 计算机中负数转正数:取反加一；正数转负数:取反减一；
- 正数+负数=模。
- 模：某种类型数据的总数，例如：  
4位二进制数的模是2的4次幂=16，数的范围是-8~7  
8位二进制数的模是2的8次幂=256，数的范围是-128~127

## 例子
### 二进制数转十进制
![二进制数转十进制](http://ojifsovoq.bkt.clouddn.com/image/jpg/Java/%E4%BA%8C%E8%BF%9B%E5%88%B6%E6%95%B0%E8%BD%AC%E5%8D%81%E8%BF%9B%E5%88%B6.png)
### 十进制转换为二进制
![十进制数转二进制](http://ojifsovoq.bkt.clouddn.com/image/jpg/Java/%E5%8D%81%E8%BF%9B%E5%88%B6%E6%95%B0%E8%BD%AC%E4%BA%8C%E8%BF%9B%E5%88%B6%20.png)

二进制数转十六进制/八进制
![二进制数转十六进制](http://ojifsovoq.bkt.clouddn.com/image/jpg/Java/%E4%BA%8C%E8%BF%9B%E5%88%B6%E6%95%B0%E8%BD%AC%E5%8D%81%E5%85%AD%E8%BF%9B%E5%88%B6.png)

### 十六进制转换为其它进制
![十六进制转换为其它进制](http://ojifsovoq.bkt.clouddn.com/image/jpg/Java/%E5%8D%81%E5%85%AD%E8%BF%9B%E5%88%B6%E8%BD%AC%E6%8D%A2%E4%B8%BA%E5%85%B6%E5%AE%83%E8%BF%9B%E5%88%B6.png)

### 十进制转换为十六进制
不断除以16，保留余数，商为0时不再除16,将所有余数倒序排序。
![十进制数转十六进制](http://ojifsovoq.bkt.clouddn.com/image/jpg/Java/%E5%8D%81%E8%BF%9B%E5%88%B6%E6%95%B0%E8%BD%AC%E5%8D%81%E5%85%AD%E8%BF%9B%E5%88%B6%20.png)

### 面试示例
>计算机的基本存储单位是字节(byte)，一个字节有8位,计算并显示8位2进制数的最大值

即将(11111111)2转换为10进制数。
![二进制转换其它进制示例](http://ojifsovoq.bkt.clouddn.com/image/jpg/Java/%E4%BA%8C%E8%BF%9B%E5%88%B6%E8%BD%AC%E6%8D%A2%E5%85%B6%E5%AE%83%E8%BF%9B%E5%88%B6%E7%A4%BA%E4%BE%8B.png)


# 变量与数据类型
## 栈与堆
### 栈特点
- 栈空间存取数据的效率高。
- 栈中的数据按“先进后出”的方式管理。
- 栈空间存储空间较小，不能存放大量的数据。
- JVM将基本类型的数据存放在栈空间。

### 堆特点
- 堆空间存取数据的效率最低；
- 数据存放的位置随机分配；
- 堆空间存储数据的空间大，能存放大容量的数据

## 变量
### 含义
可变的量，用于管理引用类型的数据，每个变量必须属于一种数据类型
### 命名
- 首字母是英文字母、$或下划线，由字母、数字、下划线组成；
- 变量的命名遵循见名知义的原则。
- Java变量名建议不用中文。
- 变量名首字母建议不用大写字母。 
- 用驼峰命名法命名多个单词组成的变量名。例如：sumScore

### 变量的作用域
- Java用一对大括号作为语句块的范围，称为作用域。
- 作用域中的变量不能重复定义。
- 离开作用域，变量所分配的内存空间将被JVM回收

### 变量的相关运算
#### 自增1
- 先加1：++i  
	示例：
		int i=1;
		System.out.println(++i)输出结果是2，变量i的值是2
- 后加1：i++  
	例如：
		 int i=1;
		System.out.println(i++)输出结果是1，变量i的值是2
		
#### 自减1
- 先减1：--i  
示例：
	int i=1;
	System.out.println(--i)输出结果是0，变量i的值是0
- 后减1：i--  
例如：
	 int i=1;
	System.out.println(i--)输出结果是1，变量i的值是0
	
#### 两个变量值互换
>已知：int  a=100;int  b=10;交换两个变量值

- 算法(1)

```Java
int c=a; 
int a=b; 
int b=c; 
```
- 算法(2)

```Java
a=a+b;
b=a-b;
a=a-b; 
```

## 常量&字面量
常量：不可变的量。
字面量：Java的变量和常量中存放的具体的数据称为字面量。

## 包装类
### 含义
包装类即把基本类型变成对象类型  

### 作用
- 包装类中封装了一些很实用的方法和常量。例如：
	Byte.MIN_VALUE是Byte类中的一个常量，存放了byte类型数据的最小值。
- 包装类在集合中用来定义集合元素的类型

### 常用方法
- Integer.MIN_VALUE：int类型的最小值：-2^31
- Integer.MAX_VALUE：int类型的最大值：2^31-1
- int  Integer.parseInt(String  sInteger);  
	作用：将字符串类型的整数转换为int类型的数据。
- String  Integer.toBinaryString(int  value);  
	作用：将十进制数转换为二进制，返回结果String类型。
- Long.MIN_VALUE：long类型的最小值
- Long.MAX_VALUE：long类型的最大值
- long  Long.parseLong(String  sLong);  
	作用：将字符串类型的整数转换为long类型的数据


## 整数、浮点、字符数据类型
### 整数类型
- 有四种整数类型：byte、short、int和long。
- Java默认整数计算的结果是int类型。
- 整数的字面量是int类型。
- 若字面量超过int类型的最大值，则字面量是long类型，那么后面要用L(或l)表示该值是long类型

### 浮点类型
- 浮点类型用于表示小数的数据类型。
- 浮点数原理:也就是二进制科学计数法。
- Java的浮点类型有float和double两种。
- Java默认浮点类型计算的结果是double类型，字面量也是double类型。

#### float类型
- float类型共32位，1位为符号位, 指数8位, 尾数23位。
- float的精度是23位（即能精确表达23位的数，超过就被截取了）。
小数是以尾数长度来表示精确度的，比如pi=3.1415的精度是4位。
- float存储数据的范围大于int类型，但精度比int要小，因为int的精度是31位。

#### double类型
- double类型，1位符号位,11位指数,52位尾数。
- double范围远远大于long，但double精度不如long

### 字符类型
- char类型的字面量可以是一个英文字母、字符或一个汉字，并且由单引号包括。
- Java底层使用一个16位的整数来处理字符类型,该数值是一个字符的unicode编码值，unicode编码是全球范围内的编码方法。
- unicode编码的英文部分与ASCII码兼容（ASCII表示范围0~128）, 同时英文字符和数字是连续编码的。
- Java在处理char类型的数据时，在底层是按unicode码来处理的。  
 例如：65代表的字符是A

### 小类型向大类型转换
#### 适用的情况  
	byte->short->int->long->float->double  
#### 规则
- 符号位会自动扩展, 负数补1, 正数补0。  
- int和char类型的数据在某些情况下可以自动相互转换。
- 小类型向大类型转换一般情况下是安全的。
- 当小类型的精度高于大类型时要注意精度丢失的隐患
#### 示例

### 大类型向小类型转换 
#### 含义&规则
强转类型转换-简称强转  
强制类型转换时，要注意边界数风险问题
#### 示例
【示例-1】大类型转换小类型时，源数据的数据位变为目标数据的符号位。  
    int i=129;
    byte b=(byte)i;
    变量b的值是多少？-127

【示例-2】大类型的数据超过了小类型的位数示例。
    int i=257;
    byte b=(byte)i;
    变量b的值是多少？1



### 转义符
转义字符是”\”，通过转义字符，可表示一些特殊的字符。
- '\n' 表示回车
- '\t' 表示制表位字符，一个制表符表示向右跳8-10个字符
- '\\' 表示\
- '\' ' 表示单引号
- '\"' 表示双引号

## 控制台获取数据的方法
### 使用args数组获取数据
#### 概述
通过main方法的args数组可以从控制台获取一组字符串数据

### 使用Scanner类获取数据
#### 概述
- Scanner类用于扫描从控制台输入的数据，可以接收字符串和基本数据类型的数据。
- Scanner类位于java.util.Scanner包中。

#### 常用方法
- String  next();
	作用：接收控制台输入的一个字符串。
- String  nextLine();
	作用：接收控制台输入的一个字符串。
- int  nexInt();
	作用：接收控制台输入的一个int类型的数据。
- double  nextDouble();
	作用：接收控制台输入的一个double类型的数据。
- boolean  nextBoolean();
	作用：接收控制台输入的一个boolean类型的数据。
	
#### 实现步骤
1. 创建Scanner类的一个对象。
2. 通过scanner调用next等方法，接收控制台输入的数据。

#### 示例
```Java
Scanner scanner=new Scanner(System.in);
System.out.println(“姓名：”);
String  name=scanner.next();

```

# 关系运算
提供了对两个量之间的关系进行比较,结果为true或false的运算
![关系运算的种类](http://ojifsovoq.bkt.clouddn.com/image/jpg/Java/%E5%85%B3%E7%B3%BB%E8%BF%90%E7%AE%97%E7%9A%84%E7%A7%8D%E7%B1%BB.png)

# 逻辑运算
## 逻辑运算含义
在关系运算基础之上,结果为true或false的运算
![逻辑运算](http://ojifsovoq.bkt.clouddn.com/image/jpg/Java/%E9%80%BB%E8%BE%91%E8%BF%90%E7%AE%97.png)

## 与运算
### 长路与运算
1. 运算符号：&
2. &在两边都是整数时，是逐位与运算；在两边是关系运算时，是逻辑运算

### 短路与运算
1. 运算符号：&&
2. 特点：当运算符左边的关系运算结果是false时，不再对右边的关系运算进行计算

## 或运算
### 长路或运算
1. 运算符：|
2. 特点：长路或运算在两边都是整数时，是逐位或运算；在两边是关系
运算时，是逻辑运算。

### 短路或运算
特点：当运算符号左边的关系运算结果是true时，不再进行右边的关系运算，直接得出true的结果

## 非运算
对有一个**关系运算的结果**取反

# 运算的优先级
## 规律
- 关系运算高于逻辑运算，完成关系运算后执行逻辑运算
- 在逻辑运算中，非运算最高，其次是与运算，优先级最低的是或运算

## 示例
> 5>=7 || 4<5 && !false

1. 计算关系运算：5>=7，结果：false；
2. 计算关系运算：4<5，结果：true；
3. 计算逻辑非运算：!false，结果：true；
	false || true && true
4. 计算逻辑运算： true && true，结果：true；
5. 计算逻辑或运算：false || true，结果：true。

# 判断语句
## if语句3种使用格式
```Java
if(条件表达式){
	条件表达式结果是true时，执行本代码块
}
```
```Java
if(条件表达式){
	条件表达式结果是true时，执行本代码块
}
else{
	条件表达式结果是false时，执行本代码块
}

```
```Java
if(条件表达式1){
		条件表达式1结果是true时，执行本代码块
	}else if(……){
		……
	}else if(条件表达式n){
		条件表达式n结果是true时，执行本代码块
	}else{
		条件表达式n结果是false时，执行本代码块
	}

```

## 三目运算
### 含义
三目运算又称三元运算，当一个变量只有两种可能值时，用三目运算最简便
### 使用格式
```Java
变量=条件表达式?值1:值2;
条件表达式为true时，值1赋值给变量；
条件表达式为false时，值2赋值给变量
```

## Switch语句
### 概述
- switch语句称为情况选择语句，又称开关语句。
- switch是分支语句的一种，用于对多种情况进行
不同处理的语句。
- JDK1.7之前的switch语句限定对整形数据进行判断。

### 使用格式
```Java
switch(表达式){ 
       case 常量值1：
       		代码块1；
       		break;
       case 常量值2：
       		代码块2；
       		break;
       		......
       default:
       		以上常量值均不是时，执行本代码。
       }
```

# 循环结构语句
Java提供了四种循环语句

## while循环
### 使用格式
```Java
while(循环继续的条件表达式){
		循环体或称循环内容
}
```
### 执行流程
![while循环的执行流程](http://ojifsovoq.bkt.clouddn.com/image/jpg/Java/while%E5%BE%AA%E7%8E%AF%E7%9A%84%E6%89%A7%E8%A1%8C%E6%B5%81%E7%A8%8B.png)

## do while循环
### 使用格式
```Java
do{
	循环内容
} while(循环继续的条件表达式);
```
### 执行流程
![do while循环的执行流程](http://ojifsovoq.bkt.clouddn.com/image/jpg/Java/do%20while%E5%BE%AA%E7%8E%AF%E7%9A%84%E6%89%A7%E8%A1%8C%E6%B5%81%E7%A8%8B.png)

## for循环
### 使用格式
```Java
for(循环变量初始化; 循环继续的条件表达式; 循环变量值变更){
		循环内容
}
```
### 执行流程
![for循环的执行流程](http://ojifsovoq.bkt.clouddn.com/image/jpg/Java/for%E5%BE%AA%E7%8E%AF%E7%9A%84%E6%89%A7%E8%A1%8C%E6%B5%81%E7%A8%8B.png)

## 循环中的break
### 概述
在循环中用于退出当前循环

## 循环中的continue
### 概述
continue命令在循环中使用，用于跳过该命令后面的循环内容，
执行下一次循环

# 数组
## 数组的定义
数组是有序数据的集合，数组中的每个元素具有相同的数组名和下标来做唯一标识
## 数组的分类
1、一维数组
2、二维数组
3、多维数组

## 数组的声明及内存分配
### 声明
- 声明形式一：
	type arrayName[];
- 声明形式二：
	type[] arrayName;

### 内存分配
使用new关键字来为数组分配内存空间
![数组的内存分配](http://ojifsovoq.bkt.clouddn.com/image/jpg/Java/%E6%95%B0%E7%BB%84%E7%9A%84%E5%86%85%E5%AD%98%E5%88%86%E9%85%8D.png)

## 数组的初始化
### 动态初始化
所有的内容不会具体指定，都是默认值。
### 静态初始化
在数组创建之初直接指定其内容

## 二维数组介绍以及使用
### 声明
```Java
type arrayName[][];
```

### 动态初始化
```Java
arrayName[][] = new type[行][列];
```

### 静态初始化
```Java
type arrayName[][]={{valuse},{valuse},{valuse}}；
```

![二维数组静态初始化例子](http://ojifsovoq.bkt.clouddn.com/image/jpg/Java/%E4%BA%8C%E7%BB%B4%E6%95%B0%E7%BB%84%E9%9D%99%E6%80%81%E5%88%9D%E5%A7%8B%E5%8C%96%E4%BE%8B%E5%AD%90.png)

# String字符串
[未处理](http://www.jikexueyuan.com/course/132.html)

# 异常处理 
[未处理](http://www.jikexueyuan.com/course/166.html)


