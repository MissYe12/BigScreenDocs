
搭建Node.js + Express + Mysql框架
=====================================================

https://blog.csdn.net/weixin_41018304/article/details/102574116
https://www.runoob.com/nodejs/nodejs-express-framework.html
https://www.cnblogs.com/jj-notes/p/6670310.html

前面我已经学习了html、node.js、express以及mysql的相关知识了，现在我们试着将他们串联起来

登录注册页面
~~~~~~~~~~~~~~~~

html部分代码：

1. 登录页面html文件代码:

.. code-block:: html
    :linenos:

    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8">
        <title>账户登录</title>
    </head>
    <body>
        <form action="http://localhost:3000/LogIn" method="GET">
            <br> 帐号: <input type="text" name="account">
            <br> 密码: <input type="text" name="password">
            <br><input type="submit" value="登陆">
        </form>
    </body>
    </html>

1. 注册页面html文件代码：

.. code-block:: html
    :linenos:

    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8">
        <title>z账户注册</title>
    </head>
    <body>
    <form action="http://127.0.0.1:3000/SignUp" method="GET"><br>
        帐号: <input type="text" name="account"> <br>
        密码: <input type="text" name="password"><br>
        姓名: <input type="text" name="name"><br>
        <input type="submit" value="注册">
    </form>
    </body>
    </html>


js部分代码：

1. 连接数据库部分

.. code-block:: js
    :linenos:

2. 启动服务器部分

.. code-block:: js
    :linenos:

3. 设置登录路由

.. code-block:: js
    :linenos:

4. 设置注册路由

.. code-block:: js
    :linenos:

5. 完整代码

.. code-block:: js
    :linenos:

利用postman发送请求进行测试
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

postman是什么

上面测试中我们写了一个html页面来发送相关的数据，但是如果每次测试一个功能都要再写一个html页面的话会很麻烦，这里我们推荐使用postman或者国产的apipost，这两款软件可以快速简单的提交http不同类型的请求，从而提高开发的速度

注意：apipost是具有相同功能的国产软件，且能免费使用基本功能，除了界面布局上的一些区别，其余功能基本一致

进入官网下载页面https://www.postman.com/downloads/

点击download，选择对应版本下载，下载完成后双击即可自动安装

1. 保持上面的代码，打开postman发送请求进行测试

postman输入url：

利用node.js创建接口，postman发送请求
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**问题：跨域**

1. 数据库连接和启动服务器部分

.. code-block:: js
    :linenos:

2. 路由：查询，app.get路径('/user')

.. code-block:: js
    :linenos:

3. 发送get请求

数据库图

结果图

1. 路由：添加，app.post路径('/api/adduser')

.. code-block:: js
    :linenos:

4. 发送post请求

发送图

数据库图

5. 路由：修改app.post('/api/updateuser')

.. code-block:: js
    :linenos:

6. body携带参数，post请求

图

数据库图