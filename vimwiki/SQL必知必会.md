[TOC]

# 1 了解 SQL

## 1.1 数据库基础

### 1.1.1 数据库

1. _DATABASE_:保存有组织的数据的容器(一个文件或者一组文件 ) 例如: .db 文件
2. _DBMS_:数据库管理系统(database manage system)例如:sqlserver

<font color = 'red'>DB 和 DBMS 不要混淆，txt 文件用 vim 或者记事本打开和 db 文件用 sqlserver 打开是一样的</font><br>
<font color = 'red'>便于理解可以认为数据库是一个文件柜</font>

### 1.1.2 表

> 表是某种特定数据类型的结构化清单
> 可直接理解为网状表格，类似账本、货物清单<br>

    表名

> 表的唯一标识

<font color = 'red'>模式(schema)</font>

> 数据库的组织和结构，模式对象可以是表、行、列、数据类型、视图、存储过程、关系、主键、外键等，一个数据库可以粗略认为就是一个 schema，具体定义不同的数据库系统定义不同，mysql 中 db 等同 schema，oracle 和 sqlserver 中不等同

> ![](https://img-blog.csdn.net/20180110131127332?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMDQyOTI4Ng==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast) > _<center>一个模式图的简单栗子</center>_

### 1.1.3 行、列和数据类型

    列(column)

> 表都由一个或多个列组成，每个列都存储表的某一部分的信息
> 产品清单表里有产品名、价格等列，每一列都只存储一种信息

<font color='red'>分解数据</font>

> 数据分列对以后数据分类或者过滤有很大影响，考虑到会对用户的地址进行筛选(找出某一省或者某一市的用户)的需求，在创建表格时可将地址这一列的数据细分到省、市、县、村等几列中这样将来查询时会很方便，若是确定不存在这样的需求就不用细分了。

    数据类型

> 数据类型就是每一列允许存放的一类数据的种类，例如年龄这一列你不可能写个男或者女上去吧

    font color='red'>数据类型兼容</font>

> 大部分的数据类型在不同数据库中都支持，但有些数据类型因数据库的差异而有所不同，会有相同的数据类型在不同数据库中名称不同的情况

    行(row)

> 表中的一条记录。也有称行为数据库记录的，这两个概念都是一个意思，可以互换，但技术上讲，行才是正确的

### 1.1.4 主键

    主键(primary key)

> 能够唯一标识某一行的一列或多列数据

- 主键不能相同
- 主键不能为空
- 主键值不允许修改
- 主键不能重用(某行删除后，该行的主键不能重新赋予新行)
- 多列数据为主键时也必须满足以上条件

## 1.2 什么是 SQL

    SQL

> Structured Query Language(结构化查询语言)，专门用来与数据库沟通
> SQL 语句由简单的英文单词构成

- 几乎所有 DBMS 都支持 SQL，标准 SQL 由 ANSI 标准委员会管理，《sql 必知必会》用 ANSI SQL

## 1.3 小结

第一课是 sql 的一些术语的介绍，书中所用栗子在 [附录 A](附录A.md)

# 2 检索数据

- [ ] select 语句用法
- [ ] 检索单/多/所有 列语句
- [ ] 检索不重复的值
- [ ] 限制检索行数(数据数)
- [ ] SQL 注释

## 2.1 SELECT

> keyword
>
> SQL 语句组成部分的保留字，关键字不能用来当列或表的名字；[附录 E](.附录E.md)有经常使用的保留字.

SQL 语句就是另类的英文语法.像“吃”这个动词用的时候一般都会说 “谁“ ”吃“ “东西” ;用 SELECT 就要告诉 SELECT 从什么地方选择什么数据(select what from where;) SQL 语句以“ ; ”来标识语句的结束(等于是句号). " ; "是必须有的(一口气读一千字的文章一个句号都没有谁受得了啊) .

## 2.2 检索单列数据

语句：SELECT 列名 FROM 表名;

```SQL
mysql> SELECT prod_name FROM Products;
+---------------------+
| prod_name           |
+---------------------+
| Fish bean bag toy   |
| Bird bean bag toy   |
| Rabbit bean bag toy |
| 8 inch teddy bear   |
| 12 inch teddy bear  |
| 18 inch teddy bear  |
| Raggedy Ann         |
| King doll           |
| Queen doll          |
+---------------------+
9 rows in set (0.09 sec)
```

sql 语句不分大小写，但列名表名分大小写；sql 语句忽略空格，在分号之前都算是同一句话

```SQL
SELECT prod_name
FROM Products;
```

这和上面的语句效果是一样的，有人这样写更利于调试和阅读.

## 2.3 检索多个列

列举事务多个中文用“、”，英文没有“、” 就用“,”，检索多个列将列名用','隔开 最后一列不用加逗号，加了会报错，逗号前后的词语在语句中的地位应该是一样的,select col1,col2, from tab1 这就告诉计算机 col2 和 from 都是列名.

```sql
mysql> SELECT prod_id , prod_name , prod_price FROM Products;
+---------+---------------------+------------+
| prod_id | prod_name           | prod_price |
+---------+---------------------+------------+
| BNBG01  | Fish bean bag toy   |       3.49 |
| BNBG02  | Bird bean bag toy   |       3.49 |
| BNBG03  | Rabbit bean bag toy |       3.49 |
| BR01    | 8 inch teddy bear   |       5.99 |
| BR02    | 12 inch teddy bear  |       8.99 |
| BR03    | 18 inch teddy bear  |      11.99 |
| RGAN01  | Raggedy Ann         |       4.99 |
| RYL01   | King doll           |       9.49 |
| RYL02   | Queen doll          |       9.49 |
+---------+---------------------+------------+
9 rows in set (0.25 sec)

```

## 2.4 检索所有列

通配符

> 用来模糊查找的字符 用一个字符代表某种特定的字符 这里\*匹配所有列名

```SQL
mysql> SELECT * FROM Products;
+---------+---------+---------------------+------------+-----------------------------------------------------------------------+
| prod_id | vend_id | prod_name           | prod_price | prod_desc                                                             |
+---------+---------+---------------------+------------+-----------------------------------------------------------------------+
| BNBG01  | DLL01   | Fish bean bag toy   |       3.49 | Fish bean bag toy, complete with bean bag worms with which to feed it |
| BNBG02  | DLL01   | Bird bean bag toy   |       3.49 | Bird bean bag toy, eggs are not included                              |
| BNBG03  | DLL01   | Rabbit bean bag toy |       3.49 | Rabbit bean bag toy, comes with bean bag carrots                      |
| BR01    | BRS01   | 8 inch teddy bear   |       5.99 | 8 inch teddy bear, comes with cap and jacket                          |
| BR02    | BRS01   | 12 inch teddy bear  |       8.99 | 12 inch teddy bear, comes with cap and jacket                         |
| BR03    | BRS01   | 18 inch teddy bear  |      11.99 | 18 inch teddy bear, comes with cap and jacket                         |
| RGAN01  | DLL01   | Raggedy Ann         |       4.99 | 18 inch Raggedy Ann doll                                              |
| RYL01   | FNG01   | King doll           |       9.49 | 12 inch king doll with royal garments and crown                       |
| RYL02   | FNG01   | Queen doll          |       9.49 | 12 inch queen doll with royal garments and crown                      |
+---------+---------+---------------------+------------+-----------------------------------------------------------------------+
9 rows in set (0.00 sec)

```

> 除了明确需要所有列的情况，都尽量不要使用通配符，因为检索不需要的列会影响程序的性能。

## 2.5 检索不同的值

如果想要检索都有哪些产品供应商

```SQL
mysql> SELECT vend_id FROM Products;
+---------+
| vend_id |
+---------+
| BRS01   |
| BRS01   |
| BRS01   |
| DLL01   |
| DLL01   |
| DLL01   |
| DLL01   |
| FNG01   |
| FNG01   |
+---------+
9 rows in set (0.02 sec)
```

我只想知道有几种供应商，这里有九条数据，还能看出是总共三种，如果是一千一万条，就找不出来了，要找不同的值，就要用 DISTINCT 关键字，顾名思义，就是筛选不重复的数据。

```SQL
mysql> SELECT DISTINCT vend_id FROM Products;
+---------+
| vend_id |
+---------+
| BRS01   |
| DLL01   |
| FNG01   |
+---------+
3 rows in set (0.04 sec)

```

> <font color = "red">不能部分使用 DISTINCT,DISTINCT 必须放在列名前面</font>
>
> select distinct vend_id, prod_price from Products;
>
> 选择多列时，只有多列的数据完全一样才会被认为是重复

## 2.6 限制检索行数

SELECT 语句一般返回所有匹配的行，但是如果只想查询第一条或者一定数量的行，那就需要进行一定的限制，很可惜，各个数据库的实现都不一样。在 SQL Server 和 Access 中使用 TOP 关键字来限制

```mysql
SELECT TOP 5 prod_name FROM Products;
```

返回前 5 行

DB2：

```mysql
SELECT prod_name FROM Products FETCH 5 ROWS ONLY;
```

Oracle:

```mysql
SELECT prod_name FROM Products WHERE ROWNUM <=5;
```

MYSQL、MARIADB、PostgreSQL 或 SQLite：

```mysql
SELECT prod_name FROM Products LIMIT 5;
```

上面语句返回查询到的前五条数据，要得到后五条数据就要用 OFFSET：

MYSQL：

```mysql
SELECT prod_name FROM Products LIMIT 5 OFFSET 5;
```

LIMIT 后表示要查询的条数，offset 后面表示从第几条数据开始取数据(0-based-indexing) LIMIT 2 OFFSET 0 表示检索第 0 行开始加其后面共两条数据，LIMIT 1 OFFSET 1 检索第 1 行在及其后面共一行数据

## 2.7 注释

SQL 标准注释用--和/\*\*/

```SQL
SELECT prod_name --这是一条单行注释
FROM Product;
/*
多行注释
多行注释
*/
```

# 3 按顺序检索数据

- [ ] 子句
- [ ] order by 子句怎么用
- [ ] 一列、多列、非检索列排序
- [ ] 排序顺序

## 3.1 排序数据

一般检索出的数据都以数据最初添加到表中的顺序显示，但这个顺序一般不代表任何意义，因为这个顺序会随着数据的更新和删除改变。

子句(clause)

> SQL 语句一般都有子句，有的子句是必须的有的是可选的，例如从某个表选择数据时 from 子句是必须的，limit 子句是可选的。

ORDER BY 子句

> ORDER BY 子句选取一列或者多列的名字，据此对检索的数据进行排序。

```sql
SELECT prod_name
FROM Products
ORDER BY prod_name;
```

prod_name 是字符型的，以其为依据排序会根据字母顺序排序数据

> <font color = "red">ORDER BY 子句一定要是 SELECT 语句的最后一个子句</font>（先检索再排序）

上面是按照检索的列进行排序，也可以用非检索的列进行排序.(如果有必要的话)

## 3.2 按多个列排序

需要同时按多个列进行排序，类似检索多个列，用逗号隔开就行，但多列排序时会根据语 ORDER BY 子句写的列的顺序，先对前一列排序，当前一列相同时才会按照第二列排序。

```sql
mysql> SELECT prod_id, prod_price , prod_name
    -> FROM Products
    -> ORDER BY prod_price , prod_name ;
+---------+------------+---------------------+
| prod_id | prod_price | prod_name           |
+---------+------------+---------------------+
| BNBG02  |       3.49 | Bird bean bag toy   |
| BNBG01  |       3.49 | Fish bean bag toy   |
| BNBG03  |       3.49 | Rabbit bean bag toy |
| RGAN01  |       4.99 | Raggedy Ann         |
| BR01    |       5.99 | 8 inch teddy bear   |
| BR02    |       8.99 | 12 inch teddy bear  |
| RYL01   |       9.49 | King doll           |
| RYL02   |       9.49 | Queen doll          |
| BR03    |      11.99 | 18 inch teddy bear  |
+---------+------------+---------------------+
9 rows in set (0.02 sec)

```

上面的语句可以简化一下，按照检索的列的相对列顺序进行排序

```sql
SELECT prod_id, prod_price , prod_name  FROM Products ORDER BY  2,3;
```

这种情况就不能按照非检索列排序了，而且使用相对位置而不使用明确列名会导致排序的错误。

## 3.3 升序降序

排序方式有两种，如果不指定，默认的都是升序排序(ASCENDING/ASC)。如果要进行降序排序就需要用到 DESC/DESCENDING 关键字。

```SQL
mysql> SELECT prod_id, prod_price, prod_name
    -> FROM Products
    -> ORDER BY prod_price DESC, prod_name ;
+---------+------------+---------------------+
| prod_id | prod_price | prod_name           |
+---------+------------+---------------------+
| BR03    |      11.99 | 18 inch teddy bear  |
| RYL01   |       9.49 | King doll           |
| RYL02   |       9.49 | Queen doll          |
| BR02    |       8.99 | 12 inch teddy bear  |
| BR01    |       5.99 | 8 inch teddy bear   |
| RGAN01  |       4.99 | Raggedy Ann         |
| BNBG02  |       3.49 | Bird bean bag toy   |
| BNBG01  |       3.49 | Fish bean bag toy   |
| BNBG03  |       3.49 | Rabbit bean bag toy |
+---------+------------+---------------------+
9 rows in set (0.00 sec)

```

> <font color = "red">DESC/ASC 只对该关键字前的一列有效</font>
>
> 上面只对 prod_price 有效，不对 prod_name 有效

# 4 过滤数据

## 4.1 where 子句

一般检索数据不会全部都检索，只是需要检索一些特定的数据，这时就要对检索结果进行过滤。WHERE 子句可以实现这一操作；语法：

WHERE filter_condition_expression;

WHERE 子句一般放在 FROM 子句后。

```SQL
mysql> SELECT prod_name , prod_price
    -> FROM Products
    -> WHERE prod_price = 3.49;
+---------------------+------------+
| prod_name           | prod_price |
+---------------------+------------+
| Fish bean bag toy   |       3.49 |
| Bird bean bag toy   |       3.49 |
| Rabbit bean bag toy |       3.49 |
+---------------------+------------+
3 rows in set (0.02 sec)
```

> 通常在应用层也可以进行数据过滤，可以通过客户端操作数据，但一般这种做法会影响应用性能，因此，最好是在数据层进行数据的过滤

## 4.2 WHERE 子句操作符

| 操作符  |        说明        |
| :-----: | :----------------: |
|    =    |        等于        |
|   < >   |       不等于       |
|   !=    |       不等于       |
|    <    |        小于        |
|   <=    |      小于等于      |
|    !    |       不小于       |
|    >    |        大于        |
|   >=    |      大于等于      |
|   !>    |       不大于       |
| BETWEEN | 在指定的两个值之间 |
| IS NULL |     为 NULL 值     |
|   IN    |  匹配指定的多个值  |
|   AND   |     逻辑与(且)     |
|   OR    |     逻辑或(或)     |
|   NOT   |     逻辑非(不)     |

### 4.2. 简单数据过滤

```SQL
mysql> SELECT prod_name , prod_price
    -> FROM Products
    -> WHERE prod_price < 10;
+---------------------+------------+
| prod_name           | prod_price |
+---------------------+------------+
| Fish bean bag toy   |       3.49 |
| Bird bean bag toy   |       3.49 |
| Rabbit bean bag toy |       3.49 |
| 8 inch teddy bear   |       5.99 |
| 12 inch teddy bear  |       8.99 |
| Raggedy Ann         |       4.99 |
| King doll           |       9.49 |
| Queen doll          |       9.49 |
+---------------------+------------+
8 rows in set (0.49 sec)
```

'>' '<‘ ’>=' '<=' '!='等这些操作符用法同上
范围值检查
BETWEEN:
WHERE COL BETWEEN A AND B;
空值检查
IS NULL:
WHERE COL IS NULL

### 4.3 高级数据过滤

根据多个条件检索时需要用逻辑操作符将多个条件组合起来

**ADN 操作符**

```SQL
SELECT prod_id, prod_price, prod_name
FROM Products
WHERE vend_id = 'DLL01' AND prod_price <= 4;
```

检索 id 为‘DLL01’ 而且 price <= 4 的行

**OR 操作符**

```SQL
SELECT prod_name, prod_price
FROM Products
WHERE vend_id = 'DLL01' OR vend_id = 'BRS01';
```

检索 id 为‘DLL01’ 或 'BRS01'的行

**组合使用**
多个操作符一起使用时会引起歧义:

```SQL
mysql> SELECT prod_name, prod_price
    -> FROM Products
    -> WHERE vend_id = 'DLL01' OR vend_id = 'BRS01'
    -> AND prod_price >= 10;
+---------------------+------------+
| prod_name           | prod_price |
+---------------------+------------+
| Fish bean bag toy   |       3.49 |
| Bird bean bag toy   |       3.49 |
| Rabbit bean bag toy |       3.49 |
| 18 inch teddy bear  |      11.99 |
| Raggedy Ann         |       4.99 |
+---------------------+------------+
5 rows in set (0.04 sec)

```

这句话本意是要找到 id 为'DLL01'或'BRS01'， 而且价格大于 10 的产品，但执行结果并不对，像先乘除后加减一样，SQL 里 AND 的优先级高于 OR，所以计算机认为你要检索的是 价格大于 10 而且是 BRS01 的产品，或者是 DLL01 的产品，这就和数学公式 A+B\*C 一样，如果要得到正确的结果就要将 A+B 用()括起来才能得到(A+B)\*C 的效果,SQL 语句也是一样的碰到可能引起歧义的地方就要用括号括起来;下面的语句才能得到正确结果

```SQL
mysql> SELECT prod_name, prod_price
FROM Products
WHERE (vend_id = 'DLL01' OR vend_id = 'BRS01')
AND prod_price >= 10;
+--------------------+------------+
| prod_name          | prod_price |
+--------------------+------------+
| 18 inch teddy bear |      11.99 |
+--------------------+------------+
1 row in set (0.00 sec)

```

> <font color="red">where 子句中使用圆括号和数学里一样，多用没什么坏处，而且还能消除歧义.</font>

**IN 操作符**

当需要根据多个特定值筛选时如果用 “=” 会很麻烦

```SQL
SELECT prod_name , prod_price
FROM Products
WHERE vend_id = 'DLL01' OR vend_id = 'BRS01'
ORDER BY prod_name;
```

这里植根据两个特定值筛选，如果值多了就要一直重复

但是用 IN 操作符可以简化这一语句：

```SQL
SELECT prod_name , prod_price
FROM Products
WHERE vend_id IN ('DLL01','BRS01')
ORDER BY prod_name;
```

> <font color = "red">IN 操作符比一连串 OR 操作符执行的更快</font>
>
> IN 操作符的条件还可以包含其他 SELECT 语句
> SELECT prod_name
> FROM Products
> WHERE vend_id IN
> (select vend_id from Products where prod_name = 'Fish bean bag toy');
> 检索生产'Fish bean bag toy'这个产品的公司的所有产品

**NOT 操作符**

和 ADN OR 用法类似，NOT 表示否定其后的条件

```SQL
SELECT prod_name
FROM Products
WHERE NOT (vend_id = 'DLL01' OR vend_id = 'BRS01');
```

检索既不是 DLL01 也不是 BRS01 的产品的名字

# 5 通配符过滤(模糊查询)

当不知道要检索的具体信息，只知道某一特征时，就需要用到模糊查找；

语法：像\*\*样的数据

where col like '';

模糊查询只针对文本字段，非文本字段不可用

| 通配符 |            说明            |
| :----: | :------------------------: |
|   %    |   匹配任意次数的任意字符   |
|   \_   |        匹配单个字符        |
|  [ ]   | 集合(匹配集合里的某一字符) |

**LIKE**关键字

WHERE 子句的一个谓语(操作符)，LIKE 后面给出模糊查询的条件

```SQL
SELECT prod_id, prod_name
FROM Products
WHERE prod_name LIKE 'Fish%';
-- 查找产品名字是Fish开头的产品id和名字
SELECT prod_name
FROM Products
WHERE prod_name LIKE 'F%y';
-- 查找产品名F开头y结尾的产品的名字
SELECT prod_id, prod_name
FROM Products
WHERE prod_name LIKE '__ inch teddy bear';
-- 查找产品名前面是两个字符后面是' inch teddy bear'的产品

```

[ ]指定一个字符集;并不是所有 DBMS 都支持[ ];更具体用法参照正则表达式

```SQL
SELECT cust_contact
FROM Customers
WHERE cust_contact LIKE '[JM]%'
ORDER BY cust_contact;
-- 找名字是J或M开头的联系人
```

> <font color = "red">虽然通配符用起来很方便，但是使用通配符比其他搜索更费时</font>
>
> - 不要过度使用通配符，其他操作符能实现相同效果就用其他操作符
> - 非要使用通配符时，不要将其放在搜索模式的最开始，放在最开始搜索是最慢的
> - 通配符的位置要注意，通配符匹配的是一种格式，格式错了匹配结果也不会正确

# 6 计算字段

一般情况下数据库中存储的数据不是应用程序最终需要的数据，例如数据库中的地址是按照省、县、区等分开存储的，而程序需要的是完整的地址。这就需要在数据库中将这些数据检索出来并且格式化，再传给应用程序；虽然也可以先检索程序再到客户端格式化，但这样会影响性能。

格式化数据就需要用到**计算字段**，计算字段不是实际存储在数据库中，，而是运行 SELECT 语句时创建的

**字段(field)**

> 字段与列基本是一样的，只不过在数据库中经常用列，字段则一般与计算字段一起使用

只有数据库才会知道计算字段和实际列的区别，传递给客户端的数据在客户端看来都是一样的

## 7.1 拼接字段

Vendors 表有供货商和地址的信息，如果想要生成一个供应商的报表，要求在供应上名称后列出供应商的位置，这时候就需要把供货商名称和地址字段拼接起来

> **拼接(concatenate)**
>
> 将多个值联接到一起形成单个值

SQL 语句中可以用特殊的操作符来拼接两个列实现这一操作：

ACCESS 和 SQL Server 用" + "

DB2、Oracle、SQLite 用 "||"

MySQL 和 MariaDB 要用特殊函数

+：

```sql
SELECT vend_name + ' (' + vend_country + ')'
FROM Vendors
ORDER BY vend_name;
```

||:

```sql
SELECT vend_name || ' (' || vend_country || ')'
FROM Vendors
ORDER BY vend_name;
```

上述语句的输出可能会有许多不必要的空格这时可以用**RTRIM()函数**来去掉空格

```SQL
SELECT RTRIM(vend_name) + ' (' + RTRIM(vend_country) + ')'
FROM Vendors
ORDER BY vend_name;
```

```sql
SELECT RTRIM(vend_name) || ' (' || RTRIM(vend_country) || ')'
FROM Vendors
ORDER BY vend_name;
```

**RTRIM()**函数去掉字符右边的空格**LTRIM()**去掉左边的空格**TRIM()**起吊左右的空格

MySQL：

```mysql
SELECT CONCAT(vend_name , '(' , vend_country , ')')
    -> AS vend_title
    -> FROM Vendors
    -> ORDER BY vend_name ;
+------------------------+
| vend_title             |
+------------------------+
| Bear Emporium(USA)     |
| Bears R Us(USA)        |
| Doll House Inc.(USA)   |
| Fun and Games(England) |
| Furball Inc.(USA)      |
| Jouets et ours(France) |
+------------------------+
6 rows in set (0.02 sec)
```

这条语句的输出和前面几条都一样，但是列名被换成了 vend_title,这就是**AS**关键字的作用：为字段取别名(也叫导出列 derived colummn),取的别名可以直接当列名使用，但是并不是真实存在数据库中的列，一般为了提高可读性，避免混淆等目的都会给列取一个别名

## 7.2 计算字段

**算术操作符：**

| 操作符 | 说明 |
| :----: | :--: |
|   +    |  加  |
|   -    |  减  |
|   \*   |  乘  |
|   /    |  除  |

```mysql
mysql> SELECT prod_id,
    ->        quantity,
    ->        item_price,
    ->        quantity*item_price AS expanded_price
    -> FROM OrderItems
    -> WHERE order_num = 20008;
+---------+----------+------------+----------------+
| prod_id | quantity | item_price | expanded_price |
+---------+----------+------------+----------------+
| RGAN01  |        5 |       4.99 |          24.95 |
| BR03    |        5 |      11.99 |          59.95 |
| BNBG01  |       10 |       3.49 |          34.90 |
| BNBG02  |       10 |       3.49 |          34.90 |
| BNBG03  |       10 |       3.49 |          34.90 |
+---------+----------+------------+----------------+
5 rows in set (0.29 sec)
```

```mysql
mysql> SELECT prod_id,quantity,item_price,
quantity*item_price AS expanded_price
FROM OrderItems
WHERE order_num = 20008
order by expanded_price;
+---------+----------+------------+----------------+
| prod_id | quantity | item_price | expanded_price |
+---------+----------+------------+----------------+
| RGAN01  |        5 |       4.99 |          24.95 |
| BNBG01  |       10 |       3.49 |          34.90 |
| BNBG02  |       10 |       3.49 |          34.90 |
| BNBG03  |       10 |       3.49 |          34.90 |
| BR03    |        5 |      11.99 |          59.95 |
+---------+----------+------------+----------------+
5 rows in set (0.03 sec)

```

**select 可以理解为执行的意思**

select 2\*3 会输出 6 select Now()会执行 Now()函数输出当前日期可以用来做测试

# 7 数据处理函数

SQL 的函数一般都是处理数据的，几乎所有 DBMS 都支持 SQL 但是只有很少的函数被所有 DBMS 支持，虽然所有类型的函数在所有 DBMS 中都有，但是函数名称和用法都有所不同

**DBMS 函数的差异**

|         函数         |                                                                            语法                                                                             |
| :------------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------: |
| 提取字符串的组成部分 |                          Access 使用 MID()；DB2、Oracle、PostgreSQL 和 SQLite 使用 SUBSTR()；MySQL 和 SQL Server 使用 SUBSTRING()                           |
|       数型转换       |             Access 和 Oracle 使用多个函数，每种类型的转换有一个函数；DB2 和 PostgreSQL 使用 CAST()；MariaDB、MySQL 和 SQL Server 使用 CONVERT()             |
|      取当前日期      | Access 使用 NOW()；DB2 和 PostgreSQL 使用 CURRENT_DATE；MariaDB 和 MySQL 使用 CURDATE()；Oracle 使用 SYSDATE；SQL Server 使用 GETDATE()；SQLite 使用 DATE() |

## 8.1 文本处理函数

**常用文本处理函数**
|函　　数|说　　明|
|-:-|-:-|
|LEFT()（或使用子字符串函数）| 返回字符串左边的字符|
|LENGTH()（也使用 DATALENGTH()或 LEN()）| 返回字符串的长度|
|LOWER()（Access 使用 LCASE()）| 将字符串转换为小写|
|LTRIM()| 去掉字符串左边的空格|
|RIGHT()（或使用子字符串函数）| 返回字符串右边的字符|
|RTRIM()| 去掉字符串右边的空格|
|SOUNDEX()| 返回字符串的 SOUNDEX 值|
|UPPER()（Access 使用 UCASE()）| 将字符串转换为大写|

> SOUNDEX()函数能将文本串转换为语音，SOUNDEX()不是 SQL 概念，但是多数 DBMS 都支持 SOUNDEX

```MYSQL
mysql> SELECT cust_name , cust_contact
    -> FROM Customers
    -> WHERE SOUNDEX(cust_contact ) = SOUNDEX('MICHAEL gREEN');
+------------+----------------+
| cust_name  | cust_contact   |
+------------+----------------+
| Kids Place | Michelle Green |
+------------+----------------+
1 row in set (0.30 sec)
```

检索发音和'Michale green'类似的联系人名

```mysql
mysql> SELECT vend_name, UPPER(vend_name) AS vend_name_upcase
    -> FROM Vendors
    -> ORDER BY vend_name;
+-----------------+------------------+
| vend_name       | vend_name_upcase |
+-----------------+------------------+
| Bear Emporium   | BEAR EMPORIUM    |
| Bears R Us      | BEARS R US       |
| Doll House Inc. | DOLL HOUSE INC.  |
| Fun and Games   | FUN AND GAMES    |
| Furball Inc.    | FURBALL INC.     |
| Jouets et ours  | JOUETS ET OURS   |
+-----------------+------------------+
6 rows in set (0.01 sec)
```

## 8.2 日期时间处理函数

日期和时间在数据库中都有对应的数据类型，而每种 DBMS 都有自己的特殊形式，日期和时间用特殊格式存储能快速有效的进行排序和过滤，并节省物理存储空间。

在编程序读取数据时一般不用日期和时间在数据库中的存储格式，一般都会用数字或者字符串的形式使用，因此日期和时间的相关函数总是用来读取，计算 和处理这些值的，但因为种种原因，各个 DBMS 的时间日期处理函数都不一致

例如：检索 2012 年的所有订单

SQLServer：DATEPART()

```SQL
SELECT order_num
FROM Orders
WHERE DATEPART(yy, order_date) = 2012;
```

PostgreSQL: DATE_PART()

```SQL
SELECT order_num
FROM Orders
WHERE DATE_PART('year', order_date) = 2012;
```

Oracle: 没有 DATEPART()函数但有几个函数可以完成对时间日期的处理

```SQL
SELECT order_num
FROM Orders
WHERE to_number(to_char(order_date, 'YYYY')) = 2012;
```

```sql
SELECT order_num
FROM Orders
WHERE order_date BETWEEN to_date('01-01-2012')
AND to_date('12-31-2012');
```

MYSQL：

```mysql
mysql> SELECT order_num
    -> FROM Orders
    -> WHERE YEAR(order_date) = 2012;
+-----------+
| order_num |
+-----------+
|     20005 |
|     20006 |
|     20007 |
|     20008 |
|     20009 |
+-----------+
5 rows in set (0.11 sec)
```

SQLite：

```sqlite
SELECT order_num
FROM Orders
WHERE strftime('%Y', order_date) = 2012;
```

关于时间日期的处理函数的具体用法还是参考具体 DBMS 的文档为准。

## 8.3 数值处理函数

**常用数值处理函数**

| 函　　数 |      说　　明      |
| :------: | :----------------: |
|  ABS()   | 返回一个数的绝对值 |
|  COS()   | 返回一个角度的余弦 |
|  EXP()   | 返回一个数的指数值 |
|   PI()   |     返回圆周率     |
|  SIN()   | 返回一个角度的正弦 |
|  SQRT()  | 返回一个数的平方根 |
|  TAN()   | 返回一个角度的正切 |

```mysql
mysql> select PI();
+----------+
| PI()     |
+----------+
| 3.141593 |
+----------+
1 row in set (0.03 sec)

```

# 8 汇总数据

当需要对数据库中的数值进行汇总整理例如求平均值，求和，求数据条数等等操作时，就要用到 SQL 的聚集函数

**SQL 聚集函数(aggregate function)**

| 函　　数 |     说　　明     |
| :------: | :--------------: |
|  AVG()   | 返回某列的平均值 |
| COUNT()  |  返回某列的行数  |
|  MAX()   | 返回某列的最大值 |
|  MIN()   | 返回某列的最小值 |
|  SUM()   |  返回某列值之和  |

AVG():

```MYSQL
mysql> SELECT AVG(prod_price) AS avg_pro_price
    -> FROM Products;
+---------------+
| avg_pro_price |
+---------------+
|      6.823333 |
+---------------+
1 row in set (0.00 sec)
```

AVG()函数只作用于单列，要求多个列的平均值要用多个 AVG 函数，而且必须给出列名；AVG 函数会忽略为 NULL 值的行，AVG 用于文本列一般无意义

作用于数字列时，MIN，MAX 函数和 AVG 用法一样，作用于文本列时，按照文本字符顺序排列先比较第一个字符在比较第二个一直到最后；

```mysql
mysql> select max(prod_name )from Products;
+-----------------+
| max(prod_name ) |
+-----------------+
| Raggedy Ann     |
+-----------------+
1 row in set (0.00 sec)

mysql> select prod_name
    -> from Products;
+---------------------+
| prod_name           |
+---------------------+
| Fish bean bag toy   |
| Bird bean bag toy   |
| Rabbit bean bag toy |
| 8 inch teddy bear   |
| 12 inch teddy bear  |
| 18 inch teddy bear  |
| Raggedy Ann         |
| King doll           |
| Queen doll          |
+---------------------+
9 rows in set (0.00 sec)

```

SUM()函数的用法也和上面一致

```mysql
SELECT SUM(item_price*quantity) AS total_price
FROM OrderItems
WHERE order_num = 20005;
```

上面用了算术操作符执行了多个列的计算，所有的聚集函数都可以这样用

COUNT 函数用来统计某列的行数，用法基本也与上面一致，count(\*)和 count(col)有时候结果不一样，因为 count(col)会忽略 NULL 值，count(\*)统计整个表的行数。

上面函数默认会选择所有检索出来的数据进行计算，但数据中会有很多是重复的，当不需要重复数据时可以使用 DISTINCT 参数，这里函数，所以是参数，其实也可以认为是关键字，默认的参数是 ALL

```SQL
SELECT AVG(DISTINCT prod_price) AS avg_price
    -> FROM Products
    -> WHERE vend_id = 'DLL01';
+-----------+
| avg_price |
+-----------+
|  4.240000 |
+-----------+
1 row in set (0.16 sec)

SELECT AVG( prod_price) AS avg_price FROM Products WHERE vend_id = 'DLL01';
+-----------+
| avg_price |
+-----------+
|  3.865000 |
+-----------+
1 row in set (0.00 sec)

```

因为有几条重复的低价数据，去重之后平均值就变高了。聚集函数还支持其他参数，具体查阅相对应 DBMS 的文档

这些聚集函数也可以一起使用只需要用逗号隔开就行。

```SQL
SELECT COUNT(*) AS num_items,
MIN(prod_price) AS price_min,
MAX(prod_price) AS price_max,
AVG(prod_price) AS price_avg
FROM Products;
+-----------+-----------+-----------+-----------+
| num_items | price_min | price_max | price_avg |
+-----------+-----------+-----------+-----------+
|         9 |      3.49 |     11.99 |  6.823333 |
+-----------+-----------+-----------+-----------+
1 row in set (0.03 sec)

```

> 在执行聚集和计算操作时最好使用别名，取别名不应使用数据库中实际的列名，虽然这样也在语法层面没问题，但许多 DBMS 都会报错，而且会引起歧义

# 9 分组数据

聚集函数可以汇总数据，但之前的查询都是在 表已有的数据或者特定的 WHERE 子句上的数据进行的；例如返回供应商 DLL01 提供的产品数：

```MYSQL
mysql> SELECT COUNT(*) AS num_prods
    -> FROM Products
    -> WHERE vend_id = 'DLL01';
+-----------+
| num_prods |
+-----------+
|         4 |
+-----------+
1 row in set (0.05 sec)
```

若要查询两个或多个供应商的产品数可以用 OR 操作符实现，但要是需要查询所有供应商提供的产品数而且供应商名 ID 也不清楚的情况下就不能用了；针对这种情况 SQL 提供 GROUP BY 子句顾名思义是按照某一条件分组，这里的分组也是逻辑组，不会在数据库中插入实际的数据；例:查询所有供应商提供的产品数情况：

```MYSQL
SELECT vend_id,COUNT(*) AS num_prods  FROM Products GROUP BY vend_id;
+---------+-----------+
| vend_id | num_prods |
+---------+-----------+
| BRS01   |         3 |
| DLL01   |         4 |
| FNG01   |         2 |
+---------+-----------+
3 rows in set (0.00 sec)

```

分组一般只在需要分组进行聚集运算时使用，上例中按照 vend_id 进行分组后在进行 COUNT 操作，count 操作会针对每一个组分别计算

> <font color="red">1.GROUP BY 子句可以包含任意数目的组，因此可以对分组进行嵌套,进行更细致的分组;select 中的每一列(除了聚集函数)都要在 GTOUP BY 子句中给出;GROUP BY 子句不允许使用别名，select 语句中是表达式 group by 子句也要是表达式</font>

如果想要在分组时按一定规则分组就要对分组进行过滤；SELECT 有 WHERE 子句，GROUP BY 也有类似的子句 HAVING，用法和 WHERE 一致，操作符也都相同

**GROUP BY&ORDER BY：**

|                   ORDER BY                   |                         GROUP BY                         |
| :------------------------------------------: | :------------------------------------------------------: |
|               对产生的输出排序               |            对行分组，但输出可能不是分组的顺序            |
| 任意列都可以使用（甚至非选择的列也可以使用） | 只可能使用选择列或表达式列，而且必须使用每个选择列表达式 |
|                  不一定需要                  |     如果与聚集函数一起使用列（或表达式），则必须使用     |

到此已经学了多种子句，列一个表看一下区别：

| 子　　句 |      说　　明      |      是否必须使用      |
| :------: | :----------------: | :--------------------: |
|  SELECT  | 要返回的列或表达式 |           是           |
|   FROM   |  从中检索数据的表  | 仅在从表选择数据时使用 |
|  WHERE   |      行级过滤      |           否           |
| GROUP BY |      分组说明      | 仅在按组计算聚集时使用 |
|  HAVING  |      组级过滤      |           否           |
| ORDER BY |    输出排序顺序    |           否           |

# 10 子查询

之前的栗子基本上需要的数据都在一个表中能够找到，不然就是很直接的检索操作，但是如果要进行检索的信息不在同一个表中，而且是需要分为多步的检索操作，那就需要写多条语句，并将前一步的检索结果记录下来用到下一步中去，最终才能完成检索，例如需要查询订购 RANG01 的所有顾客信息，订单信息在 OrdersItems 表里:

```mysql
select * from OrderItems;
+-----------+------------+---------+----------+------------+
| order_num | order_item | prod_id | quantity | item_price |
+-----------+------------+---------+----------+------------+
|     20005 |          1 | BR01    |      100 |       5.49 |
|     20005 |          2 | BR03    |      100 |      10.99 |
|     20006 |          1 | BR01    |       20 |       5.99 |
|     20006 |          2 | BR02    |       10 |       8.99 |
|     20006 |          3 | BR03    |       10 |      11.99 |
|     20007 |          1 | BR03    |       50 |      11.49 |
|     20007 |          2 | BNBG01  |      100 |       2.99 |
|     20007 |          3 | BNBG02  |      100 |       2.99 |
|     20007 |          4 | BNBG03  |      100 |       2.99 |
|     20007 |          5 | RGAN01  |       50 |       4.49 |
|     20008 |          1 | RGAN01  |        5 |       4.99 |
|     20008 |          2 | BR03    |        5 |      11.99 |
|     20008 |          3 | BNBG01  |       10 |       3.49 |
|     20008 |          4 | BNBG02  |       10 |       3.49 |
|     20008 |          5 | BNBG03  |       10 |       3.49 |
|     20009 |          1 | BNBG01  |      250 |       2.49 |
|     20009 |          2 | BNBG02  |      250 |       2.49 |
|     20009 |          3 | BNBG03  |      250 |       2.49 |
+-----------+------------+---------+----------+------------+
18 rows in set (0.02 sec)

select * from Orders;
+-----------+---------------------+------------+
| order_num | order_date          | cust_id    |
+-----------+---------------------+------------+
|     20005 | 2012-05-01 00:00:00 | 1000000001 |
|     20006 | 2012-01-12 00:00:00 | 1000000003 |
|     20007 | 2012-01-30 00:00:00 | 1000000004 |
|     20008 | 2012-02-03 00:00:00 | 1000000005 |
|     20009 | 2012-02-08 00:00:00 | 1000000001 |
+-----------+---------------------+------------+
5 rows in set (0.00 sec)

```

Orders 表里只有订单编号和顾客编号，OrderItem 表里有产品名和订单编号，只有 Customers 表里才有最终我们要查的信息，这需要我们先从 OrderItem 表检索出订单编号，再从 Orders 表检索出顾客编号，再据此检索出顾客信息，而子查询可以将这三步结合到一条语句

```MYSQL
select cust_name,cust_address from Customers
     where cust_id in (select cust_id
                       from Orders
                       where Orders.order_num in (select order_num
                                                  from OrderItems
                                                  where prod_id = 'RGAN01'));
+---------------+---------------------+
| cust_name     | cust_address        |
+---------------+---------------------+
| Fun4All       | 829 Riverside Drive |
| The Toy Store | 4545 53rd Street    |
+---------------+---------------------+
2 rows in set (0.00 sec)

```

要显示每个顾客的订单总数：

```mysql
select cust_name ,
     (select count(*)
      from Orders
      where Orders.cust_id = Customers.cust_id) as nums
from Customers;

+---------------+------+
| cust_name     | nums |
+---------------+------+
| Village Toys  |    2 |
| Kids Place    |    0 |
| Fun4All       |    1 |
| Fun4All       |    1 |
| The Toy Store |    1 |
+---------------+------+
5 rows in set (0.01 sec)

```

- 子查询只能返回单列不能返回多列
- 嵌套太多子查询会影响性能，子查询不总是解决这类问题的最好方法
- 实际子查询就是让计算机帮你手动执行了那三步操作，where 子句该怎么用还是怎么用，如果不确定子查询的输出个数就用 IN 确定只有一个也可以用=
- 表名.列名 的用法叫完全限定名，在语句中出现不同表中的相同列名时需要使用，不然计算机识别不了你到底是要用哪个表里的列

# 11 联结表

**关系表**

> 把信息分解成多个表，一类数据一个表，各表通过**某些共同的值相互关联**(所以才叫关系型数据库)

举个栗子：一个产品目录的数据库，每类产品占一行，每种物品都要有描述、价格和供应商信息，有一个供应商提供多种产品的情况，供应商信息包括供应商名、地址、联系方式等；这时供应商信息和产品信息要分开存储，如果不分开存储：

- 同一供应商的每个产品，其供应商信息都是相同的，每个产品重复存储此信息是浪费时间和存储空间的
- 如果供应商信息发生改变，那每条信息都要更新一次
- 多次输入重复数据可能会有人为失误，而且不易更改和找错

将产品信息和供应商信息分开存储 Products 只存储产品信息和供应商 ID，Vendors 表的主键 vend_id 将 Venders 和 Products 关联，利用 Products 中的 vend_id 能从 Vendors 中找出相应的供应商信息好处：

- 供应商信息不重复，节省时间空间
- 供应商信息改变只需要更新 Vendors 表的某条记录，其他表不用改
- 数据不重复，两个表的数据具有一致性，便于数据处理和生成报表

**可伸缩**

> 能够适应不断增加的工作量而不失败。设计良好的数据库或应用程序成为可伸缩性好(scale well)关系型数据库的可伸缩性比非关系型数据库的好

## 11.1 为什么使用联结

虽然将数据分解为多个表存储更方便数据处理，存储更高效，且伸缩性好，但是也有坏处：还是上面的栗子将数据分开存储了之后如果要生成报表，如何才能将两个表的数据再对应的检索出来呢？

SQL 提供了一种联结机制，用来在一条 SELECT 语句中关联表。使用联结机制可以联结多个表并返回一组输出，**联结在表中需要关联正确的行**。

在使用关系表时，仅在关系列中插入合法的数据是非常重要的，如果 Productss 中存储了无效的 vend_id 则相应的产品无法访问，为了避免这种情况，可指示数据库只允许 Products 中的 vend_id 出现合法值(就是后面的主键外键)，这叫**引用完整性**，引用完整性表示 DBMS 强制实施**数据库完整性规则**，这些规则一般由有界面的 DBMS 管理。

## 11.2 创建联结

- 指定联结的表
- 给出关联他们的方式

```mysql
select vend_name , prod_name , prod_price
from Vendors, Products #指定联结的表
where Vendors.vend_id = Products.vend_id ;#联结方式
+-----------------+---------------------+------------+
| vend_name       | prod_name           | prod_price |
+-----------------+---------------------+------------+
| Doll House Inc. | Fish bean bag toy   |       3.49 |
| Doll House Inc. | Bird bean bag toy   |       3.49 |
| Doll House Inc. | Rabbit bean bag toy |       3.49 |
| Bears R Us      | 8 inch teddy bear   |       5.99 |
| Bears R Us      | 12 inch teddy bear  |       8.99 |
| Bears R Us      | 18 inch teddy bear  |      11.99 |
| Doll House Inc. | Raggedy Ann         |       4.99 |
| Fun and Games   | King doll           |       9.49 |
| Fun and Games   | Queen doll          |       9.49 |
+-----------------+---------------------+------------+
9 rows in set (0.10 sec)
```

联结的机制就是根据给出的条件将要联结的表每一行都进行比较并将符合条件的行输出，如果不给出条件，那么每次比较都是符合要求的此时返回的结果就叫做**笛卡尔积**(没有联结条件的关系表返回的结果)，检索结果的行数是第一个表中的行数乘以第二个表中的行数

```mysql
select vend_name , prod_name , prod_price  from Vendors, Products ;
+-----------------+---------------------+------------+
| vend_name       | prod_name           | prod_price |
+-----------------+---------------------+------------+
| Bear Emporium   | Fish bean bag toy   |       3.49 |
| Bears R Us      | Fish bean bag toy   |       3.49 |
| Doll House Inc. | Fish bean bag toy   |       3.49 |
| Fun and Games   | Fish bean bag toy   |       3.49 |
| Furball Inc.    | Fish bean bag toy   |       3.49 |
| Jouets et ours  | Fish bean bag toy   |       3.49 |
| Bear Emporium   | Bird bean bag toy   |       3.49 |
| Bears R Us      | Bird bean bag toy   |       3.49 |
| Doll House Inc. | Bird bean bag toy   |       3.49 |
| Fun and Games   | Bird bean bag toy   |       3.49 |
| Furball Inc.    | Bird bean bag toy   |       3.49 |
| Jouets et ours  | Bird bean bag toy   |       3.49 |
| Bear Emporium   | Rabbit bean bag toy |       3.49 |
| Bears R Us      | Rabbit bean bag toy |       3.49 |
| Doll House Inc. | Rabbit bean bag toy |       3.49 |
| Fun and Games   | Rabbit bean bag toy |       3.49 |
| Furball Inc.    | Rabbit bean bag toy |       3.49 |
| Jouets et ours  | Rabbit bean bag toy |       3.49 |
| Bear Emporium   | 8 inch teddy bear   |       5.99 |
| Bears R Us      | 8 inch teddy bear   |       5.99 |
| Doll House Inc. | 8 inch teddy bear   |       5.99 |
| Fun and Games   | 8 inch teddy bear   |       5.99 |
| Furball Inc.    | 8 inch teddy bear   |       5.99 |
| Jouets et ours  | 8 inch teddy bear   |       5.99 |
| Bear Emporium   | 12 inch teddy bear  |       8.99 |
| Bears R Us      | 12 inch teddy bear  |       8.99 |
| Doll House Inc. | 12 inch teddy bear  |       8.99 |
| Fun and Games   | 12 inch teddy bear  |       8.99 |
| Furball Inc.    | 12 inch teddy bear  |       8.99 |
| Jouets et ours  | 12 inch teddy bear  |       8.99 |
| Bear Emporium   | 18 inch teddy bear  |      11.99 |
| Bears R Us      | 18 inch teddy bear  |      11.99 |
| Doll House Inc. | 18 inch teddy bear  |      11.99 |
| Fun and Games   | 18 inch teddy bear  |      11.99 |
| Furball Inc.    | 18 inch teddy bear  |      11.99 |
| Jouets et ours  | 18 inch teddy bear  |      11.99 |
| Bear Emporium   | Raggedy Ann         |       4.99 |
| Bears R Us      | Raggedy Ann         |       4.99 |
| Doll House Inc. | Raggedy Ann         |       4.99 |
| Fun and Games   | Raggedy Ann         |       4.99 |
| Furball Inc.    | Raggedy Ann         |       4.99 |
| Jouets et ours  | Raggedy Ann         |       4.99 |
| Bear Emporium   | King doll           |       9.49 |
| Bears R Us      | King doll           |       9.49 |
| Doll House Inc. | King doll           |       9.49 |
| Fun and Games   | King doll           |       9.49 |
| Furball Inc.    | King doll           |       9.49 |
| Jouets et ours  | King doll           |       9.49 |
| Bear Emporium   | Queen doll          |       9.49 |
| Bears R Us      | Queen doll          |       9.49 |
| Doll House Inc. | Queen doll          |       9.49 |
| Fun and Games   | Queen doll          |       9.49 |
| Furball Inc.    | Queen doll          |       9.49 |
| Jouets et ours  | Queen doll          |       9.49 |
+-----------------+---------------------+------------+
54 rows in set (0.00 sec)
```

## 11.3 内联结

上面的联结方式叫做**等值联结(equijoin)**,等值联结基于两个表之间的相等测试，这种联结也叫**内联结(innerjoin)**,这种联结还有另一种写法，可以明确联结的类型：

```mysql
select vend_name , prod_name , prod_price
from Vendors inner join Products
on Vendors.vend_id = Products.vend_id ;
+-----------------+---------------------+------------+
| vend_name       | prod_name           | prod_price |
+-----------------+---------------------+------------+
| Doll House Inc. | Fish bean bag toy   |       3.49 |
| Doll House Inc. | Bird bean bag toy   |       3.49 |
| Doll House Inc. | Rabbit bean bag toy |       3.49 |
| Bears R Us      | 8 inch teddy bear   |       5.99 |
| Bears R Us      | 12 inch teddy bear  |       8.99 |
| Bears R Us      | 18 inch teddy bear  |      11.99 |
| Doll House Inc. | Raggedy Ann         |       4.99 |
| Fun and Games   | King doll           |       9.49 |
| Fun and Games   | Queen doll          |       9.49 |
+-----------------+---------------------+------------+
9 rows in set (0.00 sec)

```

两个表的关系是以 INNER JOIN 指定的部分 From 子句，在使用 inner join 时条件要用 ON 给出，而不是用 WHERE 子句给出。(where 子句是简单的等值语法)

> ANSI SQL 规范首选 INNER JOIN 语法，DBMS 支持简单格式和标准格式具体使用看哪个更顺手(SQL 语言纯正论者是鄙视简单语法的)

**联结多个表**

第十课子查询中说子查询并不总是最好的解决方式，那个栗子能用联结实现

简单：

```mysql
SELECT cust_name, cust_contact
FROM Customers, Orders, OrderItems
WHERE Customers.cust_id = Orders.cust_id
AND OrderItems.order_num = Orders.order_num
AND prod_id = 'RGAN01';
+---------------+--------------------+
| cust_name     | cust_contact       |
+---------------+--------------------+
| Fun4All       | Denise L. Stephens |
| The Toy Store | Kim Howard         |
+---------------+--------------------+
2 rows in set (0.00 sec)

```

标准：

```mysql
select cust_name , cust_contact
from Customers inner join Orders inner join OrderItems
on Customers.cust_id  = Orders.cust_id
and OrderItems.order_num  = Orders.order_num
and prod_id  = 'RGAN01';
+---------------+--------------------+
| cust_name     | cust_contact       |
+---------------+--------------------+
| Fun4All       | Denise L. Stephens |
| The Toy Store | Kim Howard         |
+---------------+--------------------+
2 rows in set (0.06 sec)

```

## 11.4 自联结

表别名：之前学习了给列取别名的方法，栗子：

```mysql
SELECT RTRIM(vend_name) + ' (' + RTRIM(vend_country) + ')'
       AS vend_title
FROM Vendors
ORDER BY vend_name;
```

SQL 除了可以给列取别名之外还可以给表取别名，取名方法同上，给表取别名的好处：

- 缩短 SQL 语句
- 允许在一条 select 语句中多次使用相同的表

上一节中的栗子改成使用别名的版本：

```mysql
SELECT cust_name, cust_contact
FROM Customers AS C, Orders AS O, OrderItems AS OI
WHERE C.cust_id = O.cust_id
 AND OI.order_num = O.order_num
 AND prod_id = 'RGAN01';
```

> 表别名只在查询执行中使用，与列别名不一样，表别名不返回到客户端

**自联结**

一个需要在一条语句中使用不止一次相同的表的栗子：

找出与 Jim Jones 同一公司的所有顾客的 ID、姓名和联系人

子查询：

```mysql
SELECT cust_id, cust_name, cust_contact
FROM Customers
WHERE cust_name = (SELECT cust_name
                   FROM Customers
                   WHERE cust_contact = 'Jim Jones');
```

自联结：

```mysql
SELECT c1.cust_id, c1.cust_name, c1.cust_contact
FROM Customers AS c1, Customers AS c2
WHERE c1.cust_name = c2.cust_name
 AND c2.cust_contact = 'Jim Jones';
 +------------+-----------+--------------------+
| cust_id    | cust_name | cust_contact       |
+------------+-----------+--------------------+
| 1000000003 | Fun4All   | Jim Jones          |
| 1000000004 | Fun4All   | Denise L. Stephens |
+------------+-----------+--------------------+
2 rows in set (0.00 sec)
```

> 自联结通常作为外部语句，替代从相同表中检索数据的使用子查询语句，结果相同，但许多 DBMS 处理联结远比处理子查询快得多，应该都试试，确定哪种性能好

## 11.5 自然联结

上面的内联结的栗子如果不指定返回的列，将会返回所联结表中符合筛选条件的所有行合并后的所有数据，此处的合并不是相同的列合并为同一列，而是之间简单两个表进行拼接，不做任何操作，因此有相同的列多次出现的情况，**自然联结**就是排除多次出现的列，使每列只出现一次。自然联结需要我们自己实现，系统并不完成这项工作，上面的所有内联结都是自然联结。事实上，除了某些特殊的时候，都不会用到不是自然联结的内联结。

## 11.6 外联结

上面的内联结都有关联行，但是有时候需要包含没有关联行的行，例如：

- 对每个顾客的订单计数，包括没有订单的顾客
- 列出所有产品的订购数，报告括没人订购的产品
- 计算平均销售规模，包括为下订单的顾客

**外联结**：联结中包含了相关表中没有关联行的行

检索所有顾客订单：

```mysql
SELECT Customers.cust_id, Orders.order_num
FROM Customers INNER JOIN Orders
 ON Customers.cust_id = Orders.cust_id;
 +------------+-----------+
| cust_id    | order_num |
+------------+-----------+
| 1000000001 |     20005 |
| 1000000001 |     20009 |
| 1000000003 |     20006 |
| 1000000004 |     20007 |
| 1000000005 |     20008 |
+------------+-----------+
5 rows in set (0.00 sec)
```

检索包括没有订单顾客的所有顾客：

```mysql
SELECT Customers.cust_id, Orders.order_num
FROM Customers LEFT OUTER JOIN Orders
 ON Customers.cust_id = Orders.cust_id;
 +------------+-----------+
| cust_id    | order_num |
+------------+-----------+
| 1000000001 |     20005 |
| 1000000001 |     20009 |
| 1000000002 |      NULL |
| 1000000003 |     20006 |
| 1000000004 |     20007 |
| 1000000005 |     20008 |
+------------+-----------+
6 rows in set (0.00 sec)

```

这里用了关键字**OUTER JOIN**指定联结类型关键字**LEFT**必须使用，用来指定包括其所有行的表，LEFT 指定 OUTER JOIN 左边的表，RIGHT 指定 OUTER JOIN 右边的表,这里左联结和右联结唯一区别是表的顺序，所以两种联结可以互换，只要交换表的顺序即可。SQLite 不支持 RIGHT OUTER JOIN,只支持 LEFT OUTER JOIN。还有一种更简单的联结：全外联结(full outer join)，他检索两个表中的所有行，并关联可以关联的行，全外联结包含两个表不关联的行

```mysql
SELECT Customers.cust_id, Orders.order_num
FROM Orders FULL OUTER JOIN Customers
ON Orders.cust_id = Customers.cust_id;
```

> **警告：`FULL OUTER JOIN`的支持**
>
> Access、MariaDB、MySQL、Open Office Base 或 SQLite 不支持`FULL OUTER JOIN`语法

## 11.7 带聚集函数的联结

聚集函数也可以和联结一起使用，用上节的栗子：

检索每个顾客的订单数：

```mysql
SELECT Customers.cust_id,
       COUNT(Orders.order_num) AS num_ord
FROM Customers INNER JOIN Orders
 ON Customers.cust_id = Orders.cust_id
GROUP BY Customers.cust_id;
+------------+---------+
| cust_id    | num_ord |
+------------+---------+
| 1000000001 |       2 |
| 1000000003 |       1 |
| 1000000004 |       1 |
| 1000000005 |       1 |
+------------+---------+
4 rows in set (0.02 sec)

```

检索每个顾客(包含未下订单的)的订单数：

```mysql
SELECT Customers.cust_id,
       COUNT(Orders.order_num) AS num_ord
FROM Customers LEFT OUTER JOIN Orders
 ON Customers.cust_id = Orders.cust_id
GROUP BY Customers.cust_id;
+------------+---------+
| cust_id    | num_ord |
+------------+---------+
| 1000000001 |       2 |
| 1000000002 |       0 |
| 1000000003 |       1 |
| 1000000004 |       1 |
| 1000000005 |       1 |
+------------+---------+
5 rows in set (0.00 sec)

```

**小结**：

- 注意所使用的联结类型。一般我们使用内联结，但使用外联结也有效。
- 关于确切的联结语法，应该查看具体的文档，看相应的 DBMS 支持何种语法（大多数 DBMS 使用这两课中描述的某种语法）。
- 保证使用正确的联结条件（不管采用哪种语法），否则会返回不正确的数据。
- 应该总是提供联结条件，否则会得出笛卡儿积。
- 在一个联结中可以包含多个表，甚至可以对每个联结采用不同的联结类型。虽然这样做是合法的，一般也很有用，但应该在一起测试它们前分别测试每个联结。这会使故障排除更为简单。

# 12 组合查询

多数 SQL 查询只包含从一个或多个表中返回数据的单条 SELECT 语句，但 SQL 也允许执行多个查询(多条 select 语句)，并将结果集返回，这些查询称为**并**(union)或**复合查询**(compound query).

主要两种情况需要用到组合查询：

- 一个查询中从不同的表返回数据
- 对一个表执行多个查询，按一个查询返回数据

> 多数情况下，组合**相同的**两个表的两个查询所完成的工作与具有多个 WHERE 子句的一个查询是等同的

## 12.1 创建组合查询

用**UNION**关键字来组合数条 SQL 查询，利用 UNION，可给出多条 SELECT 语句，并将结果组合成一个结果集

栗子：需要 IL，IN，MI 这三个州的顾客的报表，还需包括 Fun4ALL

多条语句：

```mysql
select cust_name,cust_contact, cust_email
from Customers
where cust_state in ('IL','IN','MI');
+---------------+--------------+-----------------------+
| cust_name     | cust_contact | cust_email            |
+---------------+--------------+-----------------------+
| Village Toys  | John Smith   | sales@villagetoys.com |
| Fun4All       | Jim Jones    | jjones@fun4all.com    |
| The Toy Store | Kim Howard   | NULL                  |
+---------------+--------------+-----------------------+
3 rows in set (0.00 sec)
select  cust_name, cust_contact, cust_email
from Customers
where cust_name = 'Fun4ALL';
+-----------+--------------------+-----------------------+
| cust_name | cust_contact       | cust_email            |
+-----------+--------------------+-----------------------+
| Fun4All   | Jim Jones          | jjones@fun4all.com    |
| Fun4All   | Denise L. Stephens | dstephens@fun4all.com |
+-----------+--------------------+-----------------------+
2 rows in set (0.00 sec)

```

组合这两条语句：

```mysql
select cust_name, cust_contact, cust_email
from Customers
where cust_state in ('IL','IN','MI')
union
select cust_name, cust_contact, cust_email
from Customers
where cust_name = 'Fun4ALL';
+---------------+--------------------+-----------------------+
| cust_name     | cust_contact       | cust_email            |
+---------------+--------------------+-----------------------+
| Village Toys  | John Smith         | sales@villagetoys.com |
| Fun4All       | Jim Jones          | jjones@fun4all.com    |
| The Toy Store | Kim Howard         | NULL                  |
| Fun4All       | Denise L. Stephens | dstephens@fun4all.com |
+---------------+--------------------+-----------------------+
4 rows in set (0.02 sec)

```

换成多个 where 子句版本：

```mysql
SELECT cust_name, cust_contact, cust_email
FROM Customers
WHERE cust_state IN ('IL','IN','MI')
OR cust_name = 'Fun4All';
+---------------+--------------------+-----------------------+
| cust_name     | cust_contact       | cust_email            |
+---------------+--------------------+-----------------------+
| Village Toys  | John Smith         | sales@villagetoys.com |
| Fun4All       | Jim Jones          | jjones@fun4all.com    |
| Fun4All       | Denise L. Stephens | dstephens@fun4all.com |
| The Toy Store | Kim Howard         | NULL                  |
+---------------+--------------------+-----------------------+
4 rows in set (0.00 sec)

```

> **提示：`UNION`的限制**
> 使用`UNION`组合`SELECT`语句的数目，SQL 没有标准限制。但是，最好是参考一下具体的 DBMS 文档，了解它是否对`UNION`能组合的最大语句数目有限制。

> **警告：性能问题**
> 多数好的 DBMS 使用内部查询优化程序，在处理各条`SELECT`语句前组合它们。理论上讲，这意味着从性能上看使用多条`WHERE`子句条件还是`UNION`应该没有实际的差别。不过我说的是理论上，实践中多数查询优化程序并不能达到理想状态，所以最好测试一下这两种方法，看哪种工作得更好。

## 12.2 UNION 规则

- `UNION`必须由两条或两条以上的`SELECT`语句组成，语句之间用关键字`UNION`分隔（因此，如果组合四条`SELECT`语句，将要使用三个`UNION`关键字）。
- `UNION`中的每个查询必须包含相同的列、表达式或聚集函数（不过，各个列不需要以相同的次序列出）。
- 列数据类型必须兼容：类型不必完全相同，但必须是 DBMS 可以隐含转换的类型（例如，不同的数值类型或不同的日期类型）。

如果遵守了这些基本规则或限制，则可以将`UNION`用于任何数据检索操作。

UNION 自动从结果集中去掉了重复的行，如果要求不去除重复行可以用 UNION ALL

```mysql
SELECT cust_name, cust_contact, cust_email
FROM Customers
WHERE cust_state IN ('IL','IN','MI')
UNION ALL
SELECT cust_name, cust_contact, cust_email
FROM Customers
WHERE cust_name = 'Fun4All';
+---------------+--------------------+-----------------------+
| cust_name     | cust_contact       | cust_email            |
+---------------+--------------------+-----------------------+
| Village Toys  | John Smith         | sales@villagetoys.com |
| Fun4All       | Jim Jones          | jjones@fun4all.com    |
| The Toy Store | Kim Howard         | NULL                  |
| Fun4All       | Jim Jones          | jjones@fun4all.com    |
| Fun4All       | Denise L. Stephens | dstephens@fun4all.com |
+---------------+--------------------+-----------------------+
5 rows in set (0.00 sec)

```

UNION ALL 就是 UNION 和 WHERE 子句的区别，WHERE 子句达不到保留重复行的效果

**组合查询结果排序**

排序仍用 ORDER BY 子句，在前面说过 ORDER BY 子句只能在 SELECT 语句最后，这里也是一样，稍有不同的是，对于结果集，只存在一种排序方式，不能用升序排序一部分，降序排序另一部分，这在简单查询的栗子里是可以的，所以，组合查询不允许多条 ORDER BY 子句

```mysql
SELECT cust_name, cust_contact, cust_email
FROM Customers
WHERE cust_state IN ('IL','IN','MI')
UNION
SELECT cust_name, cust_contact, cust_email
FROM Customers
WHERE cust_name = 'Fun4All'
ORDER BY cust_name, cust_contact;
+---------------+--------------------+-----------------------+
| cust_name     | cust_contact       | cust_email            |
+---------------+--------------------+-----------------------+
| Fun4All       | Denise L. Stephens | dstephens@fun4all.com |
| Fun4All       | Jim Jones          | jjones@fun4all.com    |
| The Toy Store | Kim Howard         | NULL                  |
| Village Toys  | John Smith         | sales@villagetoys.com |
+---------------+--------------------+-----------------------+
4 rows in set (0.02 sec)

```

虽然 order by 子句只跟在了最后一个 select 语句后面，但其实 DBMS 会用它排序所有 SELECT 语句的返回结果

# 13 INSERT DATA

**INSERT**顾名思义，用来将行插入(添加)到数据库表。插入有几种方式：

- 插入完整的行
- 插入行的一部分
- 插入某些查询结果

> **提示：插入及系统安全**
> 使用`INSERT`语句可能需要客户端/服务器 DBMS 中的特定安全权限。在你试图使用`INSERT`前，应该保证自己有足够的安全权限。

## 13.1 插入完整的行

INSERT INTO TABLE VALUES(col1,col2,col3);

栗子：新增一个顾客到 Customers 表

```mysql
INSERT INTO Customers
VALUES('1000000006',
       'Toy Land',
       '123 Any Street',
       'New York',
       'NY',
       '11111',
       'USA',
       NULL,
       NULL);
```

插入到表中的每一列的数据都要在 VALUE 子句中给出，必须每一列提供一个值，如果某列没有值，则要用 NULL 值代替(假设该列允许为 NULL)，各列的值必须按照各列在表中定义的次序填充。这种写法虽然简单，但是并不安全，一旦表结构稍有变化，就会出现问题，因此，编写依赖于特定表次序的 SQL 语句时候很不安全的，还有一种更安全(更繁琐)的方法：

```mysql
INSERT INTO Customers(cust_id,
                      cust_name,
                      cust_address,
                      cust_city,
                      cust_state,
                      cust_zip,
                      cust_country,
                      cust_contact,
                      cust_email)
VALUES('1000000006',
       'Toy Land',
       '123 Any Street',
       'New York',
       'NY',
       '11111',
       'USA',
       NULL,
       NULL);
```

这种写法即使表结构改变，这条语句也能正常运行

**提示：总是使用列的列表**
不要使用没有明确给出列的`INSERT`语句。给出列能使 SQL 代码继续发挥作用，即使表结构发生了变化。

> **警告：小心使用`VALUES`**
> 不管使用哪种`INSERT`语法，`VALUES`的数目都必须正确。如果不提供列名，则必须给每个表列提供一个值；如果提供列名，则必须给列出的每个列一个值。否则，就会产生一条错误消息，相应的行不能成功插入。

## 13.2 插入部分行

给出列名的插入语句可以只给出部分列名，这就表示可以只为部分列提供值。栗子：

```mysql
INSERT INTO Customers(cust_id,
                      cust_name,
                      cust_address,
                      cust_city,
                      cust_state,
                      cust_zip,
                      cust_country)
VALUES('1000000006',
       'Toy Land',
       '123 Any Street',
       'New York',
       'NY',
       '11111',
       'USA');
```

上面两列没有提供值，这里省略了这两列和对应的值

> **警告：省略列**
> 如果表的定义允许，则可以在`INSERT`操作中省略某些列。省略的列必须满足以下某个条件。
>
> - 该列定义为允许`NULL`值（无值或空值）。
> - 在表定义中给出默认值。这表示如果不给出值，将使用默认值。
>
> 如果对表中不允许`NULL`值且没有默认值的列不给出值，DBMS 将产生错误消息，并且相应的行插入不成功。

## 13.3 插入检索的数据

```mysql
INSERT INTO Customers(cust_id,
                      cust_contact,
                      cust_email,
                      cust_name,
                      cust_address,
                      cust_city,
                      cust_state,
                      cust_zip,
                      cust_country)
SELECT cust_id,
       cust_contact,
       cust_email,
       cust_name,
       cust_address,
       cust_city,
       cust_state,
       cust_zip,
       cust_country
FROM CustNew;
```

**说明：新例子的说明**
这个例子从一个名为`CustNew`的表中读出数据并插入到`Customers`表。为了试验这个例子，应该首先创建和填充`CustNew`表。`CustNew`表的结构与附录 A 中描述的`Customers`表相同。在填充`CustNew`时，不应该使用已经在`Customers`中用过的`cust_id`值（如果主键值重复，后续的`INSERT`操作将会失败）。

> **提示：`INSERT SELECT`中的列名**
> 为简单起见，这个例子在`INSERT`和`SELECT`语句中使用了相同的列名。但是，不一定要求列名匹配。事实上，DBMS 一点儿也不关心`SELECT`返回的列名。它使用的是列的位置，因此`SELECT`中的第一列（不管其列名）将用来填充表列中指定的第一列，第二列将用来填充表列中指定的第二列，如此等等。

**插入多行**：

- INSERT 通常只插入一行，若要插入多行，需执行多个 INSERT 语句，但 INSERT SELECT 例外，它可以用一条 insert 语句插入多行，select 返回多少行就插入多少行。

- 还有一种插入多行的方法就是前面学过的组合查询(UNION)其实还是 INSERT SELECT 用法，只不过将多个 SELECT 结果组合称一个结果集返回

```mysql
insert into table(col1,col2,col3)
select val1,val2,val3
union
select val4,val5,val6;
```

union 换成 union all 则相同记录会都被插入

**复制表**

要将一个表的内容复制到另一个表。 要用 SELECT INTO

```mysql
SELECT *
INTO CustCopy
FROM Customers;
```

这里创建了一个 CustCopy 表并与 Customers 一样

MariaDB、MySQL、Oracle、PostgreSQL 和 SQLite 使用的语法稍有不同：

**输入 ▼**

```mysql
CREATE TABLE CustCopy AS
SELECT * FROM Customers;
```

**提示：进行表的复制**
`SELECT INTO`是试验新 SQL 语句前进行表复制的很好工具。先进行复制，可在复制的数据上测试 SQL 代码，而不会影响实际的数据。

在使用`SELECT INTO`时，需要知道一些事情：

- 任何`SELECT`选项和子句都可以使用，包括`WHERE`和`GROUP BY`；
- 可利用联结从多个表插入数据；
- 不管从多少个表中检索数据，数据都只能插入到一个表中。

# 14 更新和删除数据

## 14.1 更新数据

更新表中的某一行数据，要使用 UPDATE 语句，使用 UPDATE 语句的三要点：

1. 指定要更新的表
2. 给出要更新的列和值
3. 给出确定更新哪些行的过滤条件

```mysql
UPDATE Customers #要更新的比表
SET cust_email = 'kim@thetoystore.com' #要更新的列和值
WHERE cust_id = '1000000005';#过滤条件
##更新多个列
UPDATE Customers
SET cust_contact = 'Sam Roberts' ,
    cust_email = 'sam@toyland.com'
WHERE cust_id = '1000000006';
# 如果不给出筛选条件，那就是更新所有行
```

> **提示：在`UPDATE`语句中使用子查询** > `UPDATE`语句中可以使用子查询，使得能用`SELECT`语句检索出的数据更新列数据。关于子查询及使用的更多内容，请参阅第 11 课。

> **提示：`FROM`关键字**
> 有的 SQL 实现支持在`UPDATE`语句中使用`FROM`子句，用一个表的数据更新另一个表的行。如想知道你的 DBMS 是否支持这个特性，请参阅它的文档。

要删除某个列的值可以更新其值为 NULL(若果允许为空)

## 14.2 删除数据

删除特定行的数据用 DELETE 语句，类似 update，两个要点：

1. 指定表
2. 给出确定删除哪些行的筛选条件

```mysql
DELETE FROM Customers
WHERE cust_id = '1000000006';
```

> **提示：`FROM`关键字**
> 在某些 SQL 实现中，跟在`DELETE`后的关键字`FROM`是可选的。但是即使不需要，也最好提供这个关键字。这样做将保证 SQL 代码在 DBMS 之间可移植。

`DELETE`不需要列名或通配符。`DELETE`删除整行而不是删除列。要删除指定的列，请使用`UPDATE`语句。

> **说明：删除表的内容而不是表** > `DELETE`语句从表中删除行，甚至是删除表中所有行。但是，`DELETE`不删除表本身。

> **提示：更快的删除**
> 如果想从表中删除所有行，不要使用`DELETE`。可使用`TRUNCATE TABLE`语句，它完成相同的工作，而速度更快（因为不记录数据的变动）。

## 14.3 DELETE UPDATE 使用原则

前一节使用的`UPDATE`和`DELETE`语句都有`WHERE`子句，这样做的理由很充分。如果省略了`WHERE`子句，则`UPDATE`或`DELETE`将被应用到表中所有的行。换句话说，如果执行`UPDATE`而不带`WHERE`子句，则表中每一行都将用新值更新。类似地，如果执行`DELETE`语句而不带`WHERE`子句，表的所有数据都将被删除。

下面是许多 SQL 程序员使用`UPDATE`或`DELETE`时所遵循的重要原则。

- 除非确实打算更新和删除每一行，否则绝对不要使用不带`WHERE`子句的`UPDATE`或`DELETE`语句。
- 保证每个表都有主键（如果忘记这个内容，请参阅第 12 课），尽可能像`WHERE`子句那样使用它（可以指定各主键、多个值或值的范围）。
- 在`UPDATE`或`DELETE`语句使用`WHERE`子句前，应该先用`SELECT`进行测试，保证它过滤的是正确的记录，以防编写的`WHERE`子句不正确。
- 使用强制实施引用完整性的数据库（关于这个内容，请参阅第 12 课），这样 DBMS 将不允许删除其数据与其他表相关联的行。
- 有的 DBMS 允许数据库管理员施加约束，防止执行不带`WHERE`子句的`UPDATE`或`DELETE`语句。如果所采用的 DBMS 支持这个特性，应该使用它。

若是 SQL 没有撤销（undo）按钮，应该非常小心地使用`UPDATE`和`DELETE`，否则你会发现自己更新或删除了错误的数据。

# 15 操作表

## 15.1 创建表

创建表用 CREATE TABLE ，要点：

- 表的名字，在 CREATE TABLE 后给出
- 表列的定义和名字，用逗号隔开
- 有的 DBMS 要求指定表的位置

用例表 Products 的创建语句：

```mysql
CREATE TABLE Products
(
    prod_id       CHAR(10)          NOT NULL,
    vend_id       CHAR(10)          NOT NULL,
    prod_name     CHAR(254)         NOT NULL,
    prod_price    DECIMAL(8,2)      NOT NULL,
    prod_desc     VARCHAR(1000)     NULL
);
```

NOT NULL 表示该列不允许有空值，大多数 DBMS 不写 NULL 或者 NOT NULL 则默认是允许空值

> **提示：主键和`NULL`值**
> 第 1 课介绍过，主键是其值唯一标识表中每一行的列。只有不允许`NULL`值的列可作为主键，允许`NULL`值的列不能作为唯一标识。

> **警告：理解`NULL`**
> 不要把`NULL`值与空字符串相混淆。`NULL`值是没有值，不是空字符串。如果指定`''`（两个单引号，其间没有字符），这在`NOT NULL`列中是允许的。空字符串是一个有效的值，它不是无值。`NULL`值用关键字`NULL`而不是空字符串指定。

**指定默认值**

SQL 允许指定默认值，在插入行时如果不给出值，则该列的值自动设置为默认值，默认值在创建表时由 DEFAULT 关键字指定

```mysql
CREATE TABLE OrderItems
(
    order_num      INTEGER          NOT NULL,
    order_item     INTEGER          NOT NULL,
    prod_id        CHAR(10)         NOT NULL,
    quantity       INTEGER          NOT NULL      DEFAULT 1,
    item_price     DECIMAL(8,2)     NOT NULL
);
```

默认值经常用于日期或时间戳列。例如，通过指定引用系统日期的函数或变量，将系统日期用作默认日期。MySQL 用户指定`DEFAULT CURRENT_DATE()`，Oracle 用户指定`DEFAULT SYSDATE`，而 SQL Server 用户指定`DEFAULT GETDATE()`。遗憾的是，这条获得系统日期的命令在不同的 DBMS 中几乎都是不同的。表 17-1 列出了这条命令在某些 DBMS 中的语法。这里若未列出某个 DBMS，请参阅相应的文档。

**获得系统日期**

|    DBMS    |   函数/变量    |
| :--------: | :------------: |
|   Access   |     NOW()      |
|    DB2     |  CURRENT_DATE  |
|   MySQL    | CURRENT_DATE() |
|   Oracle   |    SYSDATE     |
| PostgreSQL |  CURRENT_DATE  |
| SQL Server |   GETDATE()    |
|   SQLite   |  date('now')   |
|            |                |

> **提示：使用`DEFAULT`而不是`NULL`值**
> 许多数据库开发人员喜欢使用`DEFAULT`值而不是`NULL`列，对于用于计算或数据分组的列更是如此。

## 15.2 更新表

更新表结构使用 ALTER TABLE 语句，虽然所有 DBMS 都支持该语句，但是它们允许更新的内容有差别。更新表的注意事项：

- 理想情况下，不要在表中包含数据时对其进行更新。应该在表的设计过程中充分考虑未来可能的需求，避免今后对表的结构做大改动。
- 所有的 DBMS 都允许给现有的表增加列，不过对所增加列的数据类型（以及`NULL`和`DEFAULT`的使用）有所限制。
- 许多 DBMS 不允许删除或更改表中的列。
- 多数 DBMS 允许重新命名表中的列。
- 许多 DBMS 限制对已经填有数据的列进行更改，对未填有数据的列几乎没有限制。

使用 ALTER TABLE 的要点:

- 在`ALTER TABLE`之后给出要更改的表名（该表必须存在，否则将出错）；
- 列出要做哪些更改。

给表增加列是所有 DBMS 都支持的操作，栗子：

```mysql
ALTER TABLE Vendors
ADD vend_phone CHAR(20);
```

更改或删除列、增加约束或增加键，这些操作也使用类似的语法

删除列(并不是所有 DBMS 都支持下面语句)：

```mysql
ALTER TABLE Vendors
DROP COLUMN vend_phone;
```

复杂的表结构更改一般需要手动删除过程，它涉及以下步骤：

1. 用新的列布局创建一个新表；
2. 使用`INSERT SELECT`语句（关于这条语句的详细介绍，请参阅第 15 课）从旧表复制数据到新表。有必要的话，可以使用转换函数和计算字段；
3. 检验包含所需数据的新表；
4. 重命名旧表（如果确定，可以删除它）；
5. 用旧表原来的名字重命名新表；
6. 根据需要，重新创建触发器、存储过程、索引和外键。

> **说明：`ALTER TABLE`和 SQLite**
> SQLite 对使用`ALTER TABLE`执行的操作有所限制。最重要的一个限制是，它不支持使用`ALTER TABLE`定义主键和外键，这些必须在最初创建表时指定。

> **警告：小心使用`ALTER TABLE`**
> 使用`ALTER TABLE`要极为小心，应该在进行改动前做完整的备份（模式和数据的备份）。数据库表的更改不能撤销，如果增加了不需要的列，也许无法删除它们。类似地，如果删除了不应该删除的列，可能会丢失该列中的所有数据。

## 15.3 删除表

删除整个表用 DROP TABLE 语句，删除之前创建的 CustCopy 表

```mysql
DROP TABLE CustCopy;
```

这条语句删除`CustCopy`表。删除表没有确认，也不能撤销，执行这条语句将永久删除该表。

> **提示：使用关系规则防止意外删除**
> 许多 DBMS 允许强制实施有关规则，防止删除与其他表相关联的表。在实施这些规则时，如果对某个表发布一条`DROP TABLE`语句，且该表是某个关系的组成部分，则 DBMS 将阻止这条语句执行，直到该关系被删除为止。如果允许，应该启用这些选项，它能防止意外删除有用的表。

## 15.4 重命名表

每个 DBMS 对表重命名的支持有所不同。对于这个操作，不存在严格的标准。DB2、MariaDB、MySQL、Oracle 和 PostgreSQL 用户使用`RENAME`语句，SQL Server 用户使用`sp_rename`存储过程，SQLite 用户使用`ALTER TABLE`语句。

所有重命名操作的基本语法都要求指定旧表名和新表名。不过，存在 DBMS 实现差异。关于具体的语法，请参阅相应的 DBMS 文档。

# 16 使用视图

视图是虚拟的表，将某条检索的检索结果保存为一个虚表，使用时实际就是执行该条检索。

栗子：之前有的检索订购某产品的顾客信息：

```mysql
SELECT cust_name, cust_contact
FROM Customers, Orders, OrderItems
WHERE Customers.cust_id = Orders.cust_id
 AND OrderItems.order_num = Orders.order_num
 AND prod_id = 'RGAN01';
```

当需要这类信息时需要知道表的结构，知道如何创建查询，联结等操作，但是如果把整个查询包装称一个表：

```mysql
SELECT cust_name, cust_contact
FROM ProductCustomers
WHERE prod_id = 'RGAN01';
```

这就很方便的找出了所需数据。

上面只是一个栗子，下面是视图的一些常见应用：

- 重用 SQL 语句。
- 简化复杂的 SQL 操作。在编写查询后，可以方便地重用它而不必知道其基本查询细节。
- 使用表的一部分而不是整个表。
- 保护数据。可以授予用户访问表的特定部分的权限，而不是整个表的访问权限。
- 更改数据格式和表示。视图可返回与底层表的表示和格式不同的数据。

视图创建以后使用方法和表基本相同，只是添加和更新数据有所限制。

视图仅仅是用来查看存储在别处的数据的一中虚表，其本身不包含数据，其返回的数据都是从其他表检索出来的，其他表的数据进行了更改，视图的所返回的数据也会随之更改。

> **警告：性能问题**
> 因为视图不包含数据，所以每次使用视图时，都必须处理查询执行时需要的所有检索。如果你用多个联结和过滤创建了复杂的视图或者嵌套了视图，性能可能会下降得很厉害。因此，在部署使用了大量视图的应用前，应该进行测试。

下面是关于视图创建和使用的一些最常见的规则和限制。

- 与表一样，视图必须唯一命名（不能给视图取与别的视图或表相同的名字）。
- 对于可以创建的视图数目没有限制。
- 创建视图，必须具有足够的访问权限。这些权限通常由数据库管理人员授予。
- 视图可以嵌套，即可以利用从其他视图中检索数据的查询来构造视图。所允许的嵌套层数在不同的 DBMS 中有所不同（嵌套视图可能会严重降低查询的性能，因此在产品环境中使用之前，应该对其进行全面测试）。
- 许多 DBMS 禁止在视图查询中使用`ORDER BY`子句。
- 有些 DBMS 要求对返回的所有列进行命名，如果列是计算字段，则需要使用别名（关于列别名的更多信息，请参阅第 7 课）。
- 视图不能索引，也不能有关联的触发器或默认值。
- 有些 DBMS 把视图作为只读的查询，这表示可以从视图检索数据，但不能将数据写回底层表。详情请参阅具体的 DBMS 文档。
- 有些 DBMS 允许创建这样的视图，它不能进行导致行不再属于视图的插入或更新。例如有一个视图，只检索带有电子邮件地址的顾客。如果更新某个顾客，删除他的电子邮件地址，将使该顾客不再属于视图。这是默认行为，而且是允许的，但有的 DBMS 可能会防止这种情况发生。

> **提示：参阅具体的 DBMS 文档**
> 上面的规则不少，而具体的 DBMS 文档很可能还包含别的规则。因此，在创建视图前，有必要花点时间了解必须遵守的规定。

## 16.1 CREATE VIEW

创建视图用 CREATE VIEW 语句

> **说明：视图重命名**
> 删除视图，可以使用`DROP`语句，其语法为`DROP VIEW viewname;`覆盖（或更新）视图，必须先删除它，然后再重新创建。

CREATE VIEW viewname AS select .....

## 16.2 简化 SQL 语句

视图最常见的应用是隐藏复杂的 SQL，通常都是有联结的 SQL 语句

栗子：

```sql
CREATE VIEW AS ProductCustomers AS
SELECT cust_name, cust_contact, prod_id
FROM Customers, Orders, OrdersItems
WHERE Customers.cust_id = Orders.cust_id
AND OrderItems.order_num = Orders.order_num;
Query OK, 0 rows affected (0.24 sec)

```

这个视图返回已订购了任意产品的顾客的列表，生成视图后再要检索订购了 RGAN01 的顾客：

```mysql
SELECT cust_name, cust_contact
FROM ProductCustomers
WHERE prod_id = 'RGAN01';
+---------------+--------------------+
| cust_name     | cust_contact       |
+---------------+--------------------+
| Fun4All       | Denise L. Stephens |
| The Toy Store | Kim Howard         |
+---------------+--------------------+
2 rows in set (0.17 sec)

```

这条语句执行时其实就是把语句中的 where 子句添加到视图的查询语句已有的 where 子句中。

视图极大地简化了复杂 SQL 语句的使用。利用视图，可一次性编写基础的 SQL，然后根据需要多次使用。

> **提示：创建可重用的视图**
> 创建不绑定特定数据的视图是一种好办法。例如，上面创建的视图返回订购所有产品而不仅仅是`RGAN01`的顾客（这个视图先创建）。扩展视图的范围不仅使得它能被重用，而且可能更有用。这样做不需要创建和维护多个类似视图。

## 16.3 格式化数据

视图的另一常见用途是重新格式化检索出的数据。下面的`SELECT`语句在单个组合计算列中返回供应商名和位置：

```mysql
SELECT CONCAT(RTRIM(vend_name), '(',RTRIM(vend_country),')')
       AS vend_title
FROM Vendors
ORDER BY vend_name;
+------------------------+
| vend_title             |
+------------------------+
| Bear Emporium(USA)     |
| Bears R Us(USA)        |
| Doll House Inc.(USA)   |
| Fun and Games(England) |
| Furball Inc.(USA)      |
| Jouets et ours(France) |
+------------------------+
6 rows in set (0.00 sec)

```

创建视图：

```mysql
CREATE VIEW VendorsLocations AS
SELECT CONCAT(RTRIM(vend_name), '(',RTRIM(vend_country),')')
       AS vend_title
FROM Vendors
ORDER BY vend_name;
Query OK, 0 rows affected (0.10 sec)

```

想要检索数据：

```mysql
SELECT * FROM VendorsLocations;
+------------------------+
| vend_title             |
+------------------------+
| Bear Emporium(USA)     |
| Bears R Us(USA)        |
| Doll House Inc.(USA)   |
| Fun and Games(England) |
| Furball Inc.(USA)      |
| Jouets et ours(France) |
+------------------------+
6 rows in set (0.00 sec)

```

> **说明：`SELECT`约束全部适用**
> 在这一课的前面提到，各种 DBMS 中用来创建视图的语法相当一致。那么，为什么会有多种创建视图的语句版本呢？因为视图只包含一个`SELECT`语句，而这个语句的语法必须遵循具体 DBMS 的所有规则和约束，所以会有多个创建视图的语句版本。

上面这句话是书中原话，因为书里面给了两个 SELECT 语句，一个是用“+”一个使用“||”，我用的 mysql 要用函数 CONTAC().

## 16.4 过滤数据

视图对于应用普通的`WHERE`子句也很有用。例如，可以定义`CustomerEMailList`视图，过滤没有电子邮件地址的顾客。为此，可使用下面的语句：

```sql
CREATE VIEW CustomerEMailList AS
SELECT cust_id, cust_name, cust_email
FROM Customers
WHERE cust_email IS NOT NULL;
```

```mysql
SELECT *
FROM CustomerEMailList;
+------------+--------------+-----------------------+
| cust_id    | cust_name    | cust_email            |
+------------+--------------+-----------------------+
| 1000000001 | Village Toys | sales@villagetoys.com |
| 1000000003 | Fun4All      | jjones@fun4all.com    |
| 1000000004 | Fun4All      | dstephens@fun4all.com |
+------------+--------------+-----------------------+
3 rows in set (0.04 sec)
```

> **说明：`WHERE`子句与`WHERE`子句**
> 从视图检索数据时如果使用了一条`WHERE`子句，则两组子句（一组在视图中，另一组是传递给视图的）将自动组合。前面 16.2 也提到过

## 16.5 简化计算字段

在简化计算字段的使用上，视图也特别有用。下面的一条`SELECT`语句，它检索某个订单中的物品，计算每种物品的总价格：

```sql
SELECT prod_id,
       quantity,
       item_price,
       quantity*item_price AS expanded_price
FROM OrderItems
WHERE order_num = 20008;
+---------+----------+------------+----------------+
| prod_id | quantity | item_price | expanded_price |
+---------+----------+------------+----------------+
| RGAN01  |        5 |       4.99 |          24.95 |
| BR03    |        5 |      11.99 |          59.95 |
| BNBG01  |       10 |       3.49 |          34.90 |
| BNBG02  |       10 |       3.49 |          34.90 |
| BNBG03  |       10 |       3.49 |          34.90 |
+---------+----------+------------+----------------+
5 rows in set (0.53 sec)

```

转化为视图：

```mysql
CREATE VIEW OrderItemExpanded AS
SELECT order_num, prod_id, quantity, item_price,
quantity*item_price AS expanded_price
FROM OrderItems;
```

检索订单 20008 的信息：

```mysql
SELECT * FROM OrderItemExpanded
WHERE order_num = 20008;
+-----------+---------+----------+------------+----------------+
| order_num | prod_id | quantity | item_price | expanded_price |
+-----------+---------+----------+------------+----------------+
|     20008 | RGAN01  |        5 |       4.99 |          24.95 |
|     20008 | BR03    |        5 |      11.99 |          59.95 |
|     20008 | BNBG01  |       10 |       3.49 |          34.90 |
|     20008 | BNBG02  |       10 |       3.49 |          34.90 |
|     20008 | BNBG03  |       10 |       3.49 |          34.90 |
+-----------+---------+----------+------------+----------------+
5 rows in set (0.00 sec)
```

# 17 存储过程

- [ ] what
- [ ] why
- [ ] how

## 17.1 what is procedure

迄今为止，我们使用的大多数 SQL 语句都是针对一个或多个表的单条语句。并非所有操作都这么简单，经常会有一些复杂的操作需要多条语句才能完成。例如以下的情形：

- 为了处理订单，必须核对以保证库存中有相应的物品。
- 如果物品有库存，需要预定，不再出售给别的人，并且减少物品数据以反映正确的库存量。
- 库存中没有的物品需要订购，这需要与供应商进行某种交互。
- 关于哪些物品入库（并且可以立即发货）和哪些物品退订，需要通知相应的顾客。

这显然不是一个完整的例子，它甚至超出了本书中所用样例表的范围，但足以表达我们的意思了。执行这个处理需要针对许多表的多条 SQL 语句。此外，需要执行的具体 SQL 语句及其次序也不是固定的，它们可能会根据物品是否在库存中而变化。

其实就是函数的概念，将一系列操作封装存储过程(函数)简化操作，便于参数传递

书(4th)里没有 mysql 的下面是网上找的

### 优点

- 存储过程可封装，并隐藏复杂的商业逻辑。
- 存储过程可以回传值，并可以接受参数。
- 存储过程无法使用 SELECT 指令来运行，因为它是子程序，与查看表，数据表或用户定义函数不同。
- 存储过程可以用在数据检验，强制实行商业逻辑等。

### 缺点

- 存储过程，往往定制化于特定的数据库上，因为支持的编程语言不同。当切换到其他厂商的数据库系统时，需要重写原有的存储过程。
- 存储过程的性能调校与撰写，受限于各种数据库系统。

## 17.2 why do we need procedure?

advantages:

- 通过把处理封装在一个易用的单元中，可以简化复杂的操作（如前面例子所述）。
- 由于不要求反复建立一系列处理步骤，因而保证了数据的一致性。如果所有开发人员和应用程序都使用同一存储过程，则所使用的代码都是相同的。
  这一点的延伸就是防止错误。需要执行的步骤越多，出错的可能性就越大。防止错误保证了数据的一致性。
- 简化对变动的管理。如果表名、列名或业务逻辑（或别的内容）有变化，那么只需要更改存储过程的代码。使用它的人员甚至不需要知道这些变化。
  这一点的延伸就是安全性。通过存储过程限制对基础数据的访问，减少了数据讹误（无意识的或别的原因所导致的数据讹误）的机会。
- 因为存储过程通常以编译过的形式存储，所以 DBMS 处理命令的工作较少，提高了性能。
- 存在一些只能用在单个请求中的 SQL 元素和特性，存储过程可以使用它们来编写功能更强更灵活的代码。
  > 简单、安全、高性能

disadvantages:

- 不同 DBMS 中的存储过程语法有所不同。事实上，编写真正的可移植存储过程几乎是不可能的。不过，存储过程的自我调用（名字以及数据如何传递）可以相对保持可移植。因此，如果需要移植到别的 DBMS，至少客户端应用代码不需要变动。
- 一般来说，编写存储过程比编写基本 SQL 语句复杂，需要更高的技能，更丰富的经验。因此，许多数据库管理员把限制存储过程的创建作为安全措施（主要受上一条缺陷的影响）。

> **说明：不能编写存储过程？你依然可以使用**
> 大多数 DBMS 将编写存储过程所需的安全和访问权限与执行存储过程所需的安全和访问权限区分开来。这是好事情，即使你不能（或不想）编写自己的存储过程，也仍然可以在适当的时候执行别的存储过程。

## 17.3 how to use procedure
