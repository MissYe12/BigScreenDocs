https://developer.mozilla.org/zh-CN/docs/learn/Server-side/Express_Nodejs/Introduction
https://www.runoob.com/nodejs/nodejs-express-framework.html
Express
===================================

4.x Express API参考手册

简介
~~~~~~~~~~~~~~~~

在上一节中，我们已经演示了如何通过npm命令来给工程文件安装express模块，那么express是什么，如何在程序中发挥作用的呢

使用 Express 可以快速地搭建一个完整功能的网站。

Express 框架核心特性：

- 可以设置中间件来响应 HTTP 请求。

- 定义了路由表用于执行不同的 HTTP 请求动作。

- 可以通过向模板传递参数来动态渲染 HTML 页面。

虽然 Express 本身是极简风格的，但是开发人员通过创建各类兼容的中间件包解决了几乎所有的 web 开发问题。这些库可以实现 cookie、会话、用户登录、URL 参数、POST 数据、安全头等功能。可在 Express 中间件 网页中找到由 Express 团队维护的中间件软件包列表（还有一张流行的第三方软件包列表）。

HelloExpress.js
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: js
    :linenos:

    var express = require('express');  //require()引入express模块
    var app = express();        //创建一个express对象

    //路由定义

    app.get('/', (req, res) => {   //app.get()方法指定了一个回调函数，该函数在每监听到一个关于站点根目录路径('/')的 http GET 请求时调用。此回调函数以一个请求(req)和一个响应对象(res)作为参数
    res.send('Hello Express!');    //调用响应对象的api，send函数
    });

    app.listen(3000, () => {    //在3000端口上启动服务器监听，需要有这一代码块，服务端才能监听到客户端的请求
    console.log('示例应用正在监听 3000 端口!'); //在控制台打印日志
    });

最后一个代码块在 “3000” 端口上启动服务器，并在控制台打印日志。服务器运行时，可用浏览器访问 localhost:3000，看看响应返回了什么。
    
app对象具有以下方法
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

路由HTTP请求；具体可以看app.METHOD和app.param这两个例子。

配置中间件；具体请看app.route。

渲染HTML视图；具体请看app.render。

注册模板引擎；具体请看app.engine。

简单api实例
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**postman或者apipost的使用**

.. code-block:: js
    :linenos:

    app.get('/',(req,res) => {
        res.send('这是get请求')
    })

.. code-block:: js
    :linenos:
    
    app.post('/',(req,res) =>{
        res.send('这是post请求')
    })

app.delete

app.patch

app.listen

中间件route
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


