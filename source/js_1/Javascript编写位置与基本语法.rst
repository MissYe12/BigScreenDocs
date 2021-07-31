
Javascript编写位置与基本语法
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

编写位置
------------
编写在标签的onclick属性中
^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: sh
   :linenos:

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Document</title>
    </head>
    <body>
        <button onclick="alert('你点我干嘛');">点我一下</button>
    </body>
    </html>

编写在超链接的href中
^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: sh
   :linenos:

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Document</title>
    </head>
    <body>
        <a href="JavaScript:alert('我在超链接的href里');">你点我一下</a>
    </body>
    </html>

**前两种方式属于结构与行为耦合，不方便维护，故不推荐使用**

引入外部JS文件
^^^^^^^^^^^^^^^^^^^^^^^

开发中常用方式：写在外部文件中，可以在不同的页面同时引用，也可以利用到浏览器的缓存机制，推荐使用。

.. code-block:: sh
   :linenos:

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Document</title>
        <script src="./直接创建的JS文件名.js">
        </script>
    </head>
    <body>

    </body>
    </html>


编写在script标签中
^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: sh
   :linenos:

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Document</title>
        <script> 
            alert('我是内部script的JS代码');//弹出警告框
        /*一旦引入外部文件，就不能再编写代码了，即使编写了浏览器也会忽略，如果需要则可以再创建一个新的script标签用于编写内部代码*/     
        </script>
    </head>
    <body>
    
    </body>
    </html>

基本语法
------------
ECMAScript借用了C、Java、Perl这些语言的语法，此外Java和ECMAScript有一些关键的语法特性相同，也有一些完全不同。

严格区分大小写
^^^^^^^^^^^^^^^^^^^^

与Java一样，变量、函数名、运算符以及其他一切东西都是区分大小写的。

注释
^^^^^^^^^^^^^^^^^^^^

- 单行注释以双斜杠开头
- 多行注释以单斜杠和星号开头，以星号和单斜杠结尾

.. code-block:: sh
   :linenos:

    //this is a single-line comment

    /*this is a
     multiline comment*/

变量弱类型
^^^^^^^^^^^^^^^^^^^^
ECMAScript中的变量无特定类型，定义变量时只用var运算符，可将其初始为任意值。因此可以随时改变变量所存数据的类型(**尽量避免这样做**)

结尾分号可有可无
^^^^^^^^^^^^^^^^^^^^
最好的代码编写习惯是总加入分号，因为没有分号有些浏览器不能正确运行(如果没有分号，ECMAScript会把折行的代码的结尾视为该语句的结尾，但是很可能会破坏语义)，不过根据ECMAScript标准，下面两行代码都是正确的。

.. code-block:: sh
   :linenos:

   var test1="yellow";
   var test2="blue"

