
SQL语法
===================================

SQL语句怎么使用（这一段放到mysql 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
打开命令提示符，登录mysql，登录后命令提示符中出现 mysql> 字样，输入需要使用的sql语句即可


数据定义语言（Data Definition Language，DDL）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

用来创建或删除数据库以及表等对象，主要包含以下几种命令：

- DROP：删除数据库和表等对象
- CREATE：创建数据库和表等对象
- ALTER：修改数据库和表等对象的结构
- DELETE: 用于删除表中的记录

1. 通过使用 DROP 语句，可以轻松地删除索引、表和数据库。

两点注意：

用户必须拥有执行 DROP TABLE 命令的权限，否则数据表不会被删除。

表被删除时，用户在该表上的权限不会自动删除
   
.. code-block:: 
    :linenos:

    DROP [表(库)] [表(库)名];

例子:

.. code-block:: sql
    :linenos:

    DROP TABLE table_name;
    DROP DATABASE database_name;

TABLE表示表，table_name表示表名 
DATABASE表示库，database_name表示库名

2. 通过使用 CREATE 语句可以创建数据库和表等对象

.. code-block:: 
    :linenos:

    CREATE [表(库)] [表(库)名];

例子：

CREATE DATABASE 语句用于创建数据库。

.. code-block:: sql
    :linenos:

    CREATE DATABASE database_name;

CREATE TABLE 语句用于创建数据库中的表。而表由行和列组成，每个表都必须有个表名。

.. code-block:: sql
    :linenos:

    CREATE TABLE table_name
    (
    column_name1 data_type(size),
    column_name2 data_type(size),
    column_name3 data_type(size),
    );

这是一个名为table_name的表，其中包含三个列的数据表，column_name 参数规定表中列的名称，data_type 参数规定列的数据类型(例如 varchar、integer、decimal、date 等等)，size 参数规定表中列的最大长度。

3. ALTER语句

例子：

ALTER DATABASE 语句用于更改数据库的全局特性

.. code-block:: sql
    :linenos:

    mysql> ALTER DATABASE database_name 
        -> DEFAULT CHARACTER SET utf-8
        -> DEFAULT COLLATE utf8_general_ci;

这段语句中有是三个参数，database_name是要修改的<数据库名>，utf-8是要修改的<字符集名>，utf8_general_ci是要修改的 <排序规则名>

ALTER TABLE  语句用于在已有的表中添加、删除或修改列。

向表table_name中添加column_name列，设置该新增列的数据类型为datatype

.. code-block:: sql
    :linenos:

    ALTER TABLE table_name ADD column_name datatype

删除表table_name中的column_name列

.. code-block:: sql
    :linenos:

    ALTER TABLE table_name DROP COLUMN column_name


数据操作语言（Data Manipulation Language，DML）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

用来变更表中的记录，主要包含以下几种命令：

- INSERT：向表中插入新数据
- UPDATE：更新表中的数据
- DELETE：删除表中的数据

1. INSERT INTO 语句用于向表中插入新记录(行)
   
例子：

第一种形式，不指定需要插入数据的列名，只提供被插入的值：

使用这种形式时需要列出插入行的每一列值。如表中有三列数据，则应分别列出要插入三列中的值。

.. code-block:: sql
    :linenos:

    INSERT INTO table_name VALUES (value1,value2,value3,...);

第二种形式，指定列名及被插入的值：

.. code-block:: sql
    :linenos:

    INSERT INTO table_name (column1,column2,column3,...) VALUES (value1,value2,value3,...);

2. UPDATE 语句用于更新表中已存在的记录(行)
   
例子：

将table_name表中，some_column列上，值为some_value的对应行中，column1和column2列的数据分别改为value1，value2

.. code-block:: sql
    :linenos:

    UPDATE table_name SET column1=value1,column2=value2 WHERE some_column=some_value;

3. DELETE语句用于删除表中的记录(行)

例子：

删除table_name表中，在some_column列上，值为some_value的对应行

.. code-block:: sql
    :linenos:

    DELETE FROM table_name WHERE some_column=some_value;

演示表(执行前):

.. code-block:: 
    :linenos:

    +------------+-------------+-------------+
    |some_column |some_column1 |some_column2 |
    +------------+-------------+-------------+
    |some_value  |1            |2            |
    |3           |some_value   |5            |
    +------------+-------------+-------------+

则执行该语句后some_column中，some_value对应的行豆浆被删除

演示表(执行后):

.. code-block:: 
    :linenos:

    +------------+-------------+-------------+
    |some_column |some_column1 |some_column2 |
    +------------+-------------+-------------+
    |3           |some_value   |5            |
    +------------+-------------+-------------+

**注意：** WHERE 子句规定哪条记录或者哪些记录需要删除。如果您省略了 WHERE 子句，所有的记录都将被删除！


数据查询语言（Data Query Language，DQL）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

用来查询表中的记录，主要包含：

- SELECT 命令，来查询表中的数据。

1. SELECT 语句用于从数据库中选取数据。

例子：

从table_name表中选取column_name1和column_name2两列数据

.. code-block:: sql
    :linenos:

    SELECT column_name1,column_name2 FROM table_name;

从table_name表中选取所有列

.. code-block:: sql
    :linenos:

    SELECT * FROM table_name;

数据控制语言（Data Control Language，DCL）(本教程中使用不多)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

用来确认或者取消对数据库中的数据进行的变更。除此之外，还可以对数据库中的用户设定权限。主要包含以下几种命令：
    
- GRANT：赋予用户操作权限
- REVOKE：取消用户的操作权限
- COMMIT：确认对数据库中的数据进行的变更
- ROLLBACK：取消对数据库中的数据进行的变更


WHERE语句
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

在上面的示例中我们会用到where后面跟一个或多个过滤条件，以选择我们需要的数据,可知 WHERE 子句是用于过滤记录。

下面的运算符可以在 WHERE 子句中使用：

===== ========= ========================================
Id    运算符        描述
===== ========= ========================================
1       =       等于
2       <>      不等于。在 SQL 的一些版本中，该操作符可被写成 != 
3       >       大于
4       <       小于
5       >=      大于等于
6       <=      小于等于
7       BETWEEN 在某个范围内
8       LIKE    搜索某种模式
9       IN      指定针对某个列的多个可能值
===== ========= ========================================



