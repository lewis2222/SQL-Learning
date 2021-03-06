# MySQL学习

## 前言

本学习记录依附于《Java语言程序设计(进阶篇) 10th》的第32章Java数据库程序设计。肯定不如专业书籍详实，暂做入门使用。主要是MySQL、JDBC等暂且还不明白是啥的东西。

## 关系型数据库系统

数据库系统*database system* 由数据库、存储和管理数据库中数据的软件，以及显示数据并使用户能够与数据库系统进行交互的应用程序构成。

*数据库* 是由构成信息的数据组成的存储。而MySQL、Oracle等是数据库管理系统(*database management system*, DBMS)软件。DBMS是为专业程序设计人员使用而设计的，并不适用于普通用户。需要在DBMS上搭建应用程序，才能使用户访问和更新数据库  
大多数数据库系统都是***关系数据库系统*** (*relational database system*)，这个系统基于关系数据模型，这个模型有三要素：结构、完整性和语言。

* 结构 *structure*
  * 定义数据表示
* 完整性 *integrity*
  * 给出一些对数据的约束
* 语言 *language*
  * 提供了访问和操纵数据的手段

### 关系结构

一个关系实际上是一个没有重复行的表格。表的一行表示一条*记录*，表达一列表示该记录中的一个*属性的值*。  
在关系型数据库理论中，一行称为一个*元组*(tuple),一列称为一个*属性* (attribute)。
表描述数据之间的关系。表中的每一行表示相互关联的数据构成的一条记录。不同表格的数据可以通过共同的属性也可能相互关联。例如学生表和社保表，均共有身份号码这个属性，那就能构建关联。

### 完整性约束

完整性约束 *integrity constraint* 对表格加了一个条件，表中所有合法值都必须满足该条件。一般来说，有三种类型的约束：域约束、主键约束和外键约束。三种约束又分为两类：

* 内部关联型约束 *intrarelational constraint*:每个约束只涉及一个关系;
  * 域约束*domain constraint*
    * 规定一个属性的允许值。如，整数、浮点数、定长字符串和变长字符串，或数值的范围，值是否为null等；
  * 主键约束 *primary key constraint*
    * 超键 *superkey*: 是一个属性或一组属性，它唯一标识了一个关系。即没有两个记录有相同的超键值。由定义知，一个关系是由一组互相不同的记录组成的。关系中的所有属性的集合构成一个超键,但并不是说超键只能是所有属性的集合;
    * 键 *key*:K是一个最小的超键，意思是K的所有真子集都不是超键，一个关系可以有几个键，这种情况下，每个键称为一个候选键*candidate key*;
    * 主键*primary key*:是由数据库设计者指定的候选键之一，通常用来标识一个关系中的记录。
* 外键约束 *foreign key constraint*
  在关系数据库中，数据是相互关联的。关系中的记录是相互关联的，而不同关系中的记录通过它们的共同属性也是相互关联的。简单说，共同属性就是外键。外键约束 *foreign key constraint* 定义了关系之间的关系。
  形式化说：
  * 若FK是一个属性集，称FK是关系R的一个外键，它引用关系T前提是满足：
      >FK中的属性与关系T中的主键具有相同的域；
      >关系R中FK的非空值必须与关系T中的一个主键值相匹配。  则FK是关系R的一个外键，它引用关系T。  
* 强制完整性约束
  * 数据库管理系统强制执行完整性约束并且拒绝违反约束的操作。  

Q&A：  

Q:什么是超键、候选键和主键？  
A:超键：能唯一标志关系的属性，即有这些属性你就能认出是哪个关系，最大的超键是一个关系内所有的属性的集合。  
候选键：有的关系中有一种唯一的属性或属性集合，其单独存在已经是最小的超键，其真子集无法被认定为超键，这时这种属性或属性集合被称为键，有多个键时，每个键被称为候选键。  

Q:什么是外键?  
A:两个关系的共同属性就是外键。

## SQL

结构化查询语言 (*structured query language*, SQL)是用来定义表格和完整性约束以及访问和操纵数据的语言。

### 在MySQL上创建用户账户

1. 进入MySQL命令栏：MySQL 8.0.x版本有自己的命令提示符程序MySQL 8.0 Command Line Client - Unicode；打开此程序要求输入根密码，输入根密码即可；
2. 在MySQL提示符下输入  
   <kbd>use mysql;</kbd>
3. 创建用户名为scott，密码为tiger的账户，输入<br>
   <kbd>create user 'scott'@'localhost 'identified by 'tiger';</kbd><br>//注意有分号！！！
4. 赋予特权给scott<br>
   <kbd>grant select,insert,update,delete,create,create view,drop,execute,references on *.* to 'scott'@'localhost';</kbd>  
  如果希望该账号可以由任意IP地址远程访问，输入  
  <kbd>grant all privileges on *.* to 'scott'@'%' identified by 'tiger'</kbd>
  如果希望限制该账号可以从某个特定的IP地址访问，输入  
  <kbd>grant all privileges on *.* to 'scott'@'ipAddress' identified by 'tiger'</kbd><br>
5. 退出，输入  
   <kbd>exit;</kbd> 

再之后发现后面的实践环节需要随书的资源，否则没有表，也就无所谓开始与否，也就是说暂且腰斩。(我太监啦！！！
