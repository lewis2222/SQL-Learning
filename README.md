# 数据库和SQL

结构化查询语言 (*structured query language*, SQL)是用来定义表格和完整性约束以及访问和操纵数据的语言。

## SQL概要

本书介绍的是标准SQL书写。

**法则 1-3** 学会标准SQL就可以在各种RDBMS中书写SQL语句了。

### SQL语句及其种类

* DDL (Data Definition Language, 数据定义语言)  
  用来创建或者删除存储数据用的数据库以及数据库中的表等对象。
  * CREATE 创建数据库和表等对象
  * DROP 删除数据库和表等对象
  * ALTER 修改数据库和表等对象
  
* DML (Data Manipulation Language, 数据操纵语言)
  用来查询或者变更表中的记录。
  * SELECT 查询表中的记录
  * INSERT 向表中插入记录
  * UPDATE 更新表中的记录
  * DELETE 删除表中的数据
  
* DCL(Data Control Language, 数据控制语言)
  确认或取消对表内容的变更，设定用户操作权限
  * COMMIT 确认对数据库中的数据进行的变更
  * ROLLBACK　取消对数据库中的数据进行的变更
  * GRANT　赋予用户权限
  * REVOKE　取消用户权限
  
**法则 1-4** SQL根据功能不同分为三类，其中DML使用最多。

### SQL基本书写规则

**法则 1-5** SQL语句以分号(;)结尾。

**法则 1-6** 关键字不区分大小写。  
本记录中  

* 关键字大写
* 表名首字母大写
* 其余(列名等)小写

**法则 1-7** 字符串和日期常数需要使用单引号(')括起来;数字常数无需加注单引号。  
本记录中日期的格式为'年-月-日'。  

**法则 1-8** 单词之间使用半角空格或换行符进行分隔。
