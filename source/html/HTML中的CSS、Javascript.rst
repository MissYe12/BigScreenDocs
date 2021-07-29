
HTML中的CSS、Javascript
===========================================

在3.1. HTML、CSS与Javascript简述这一节中，我们已经知道，一个网页中，HTML是主体，CSS在HTML的基础上来描述网页的样子。

具体来说则为： CSS用于渲染HTML元素标签的样式。

CSS 可以通过以下方式添加到HTML中:

1、内联样式 ———— 在HTML元素中使用"style" 属性。

2、内部样式表 ———— 在HTML文档头部 <head> 区域使用<style> 元素 来包含CSS。

3、外部样式表 ———— 使用外部 CSS 文件。

最好的方式是通过外部引用CSS文件。

外部样式表
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

当样式需要被应用到很多页面的时候，外部样式表将是理想的选择。使用外部样式表，你就可以通过更改一个文件来改变整个站点的外观。
这样可以完全使结构和表现分离，这样使样式表可以在不同页面中使用，并且可以利用浏览器缓存加快用户访问的速度以提高了用户体验。

要求： 最大限度的使样式可以进行复用，将样式统一写在样式表中。

注: 网页不喜欢一个页面有太多的css代码，因为这样会影响搜索引擎的收录,因此选择外部样式表是绝大多数情况下的最佳选择。

**步骤**


1、首先将所需样式写在一个CSS文件中，该文件即为对应html文件的外部样式文件。（CSS教程详见第4，5，6章）

2、在html文件的head元素中写入link标签，表示以外部样式表形式导入CSS样式。

具体格式如下所示：

.. code-block:: html
   :linenos:


    <head>
        <link rel="stylesheet" type="text/css" href="mystyle.css">
    </head>

注：link标签： 用于定义资源引用地址。

rel定义当前文档与被链接文档之间的关系（"stylesheet"表示样式表）；

type规定被链接文档的 MIME 类型；

*（拓： MIME类型： 多用途互联网邮件扩展类型。
是设定某种扩展名的文件用一种应用程序来打开的方式类型，当该扩展名文件被访问的时候，浏览器会自动使用指定应用程序来打开。）*

href定义被链接文档的位置。

内部样式表
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

当单个文件需要特别样式时，就可以使用内部样式表。你可以在<head> 部分通过 <style>标签定义内部样式表。

例如：

.. code-block:: html
    :linenos:

    <head>
        <style type="text/css">
            body {
                background-color: yellow;
            }
            p {
                color: blue;
            }
        </style>
    </head>

**步骤**

1、指明style的类型（CSS）(这一步往往可以省略，直接写<style>即可）

2、在style元素中写下自己想设置的样式。

内联样式
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

当特殊的样式需要应用到个别元素时，就可以使用内联样式。 

以下实例显示出如何改变段落的颜色和左外边距。

.. code-block:: html
    :linenos:


    <p style="color: blue;margin-left: 20px;">这是一个段落。</p>

**步骤**

使用内联样式的方法是在相关的标签中使用样式属性，样式属性可以包含任何 CSS 属性。（注意：写在最开始的标签上）

**补充**

CSS修饰标签的样式，有 "内联" 和 "外引" 两种方式。

对于大部分标签，用"内联"和"外引"两种方法均可，且修改父级标签，子级标签特性也会改变。但某些标签却无法通过修改父级标签来改变子级标签特性，如a标签，修改其颜色特性，必须直接修改 a 标签的特性才可。

例如：修改a标签的颜色属性。

.. code-block:: html 
    :linenos:

    <a href="#" style="color: red;" rel="nofollow">只能使用"内联"方式</a>


**三者之间的优先级**

内联形式 > 内部样式表 > 外部样式表

但是内部样式表 > 外部样式表有一个前提：内部样式表的位置一定在外部样式表的后面。

共同的前提： 内联形式、内部样式表、外部样式表中css样式是在相同权值的情况下。（关于权值的定义详见： 第4.4节“优先级判断”）

<script></script>标签（标签内容里面写js语句）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

JavaScript使HTML页面具有更强的动态和交互性。

将脚本插入html文档中需要使用<script>。

HTML <script> 标签用于定义客户端脚本（JavaScript）。

<script> 元素即可包含脚本语句，也可通过 src 属性指向外部脚本文件。

JavaScript 的常见用途是图像处理、表单验证和内容的动态更改。

如需选取 HTML 元素，JavaScript 最常用 document.getElementById() 方法。然后获取元素ID后，再对元素进行下一步的处理。

例如：

.. code-block:: html
    :linenos:


    <h1>使用 JavaScript 更改文本</h1>
    <p>本例把 "Hello JavaScript!" 写入 id="demo" 的 HTML 元素内：</p>
    <p id="demo"></p>
    <script>
        document.getElementById("demo").innerHTML = "Hello JavaScript!";
    </script> 

运行结果如图1所示：

.. figure:: media/HTML中的CSS、Javascript/3.41.png
  :align: center
  :alt: error

  图1-运行结果

其中，getElementById()方法可返回对拥有指定 ID 的第一个对象的引用；innerHTML属性设置或返回表格行的开始和结束标签之间的 HTML。

**拓展**

HTML <noscript> 标签定义了替代内容，这些内容将显示给在浏览器中禁用了脚本或浏览器不支持脚本的用户。

例如： 

.. code-block:: html
    :linenos:

    <!DOCTYPE html>
    <html>
    <body>
    <p id="demo"></p>
    <script>
        document.getElementById("demo").innerHTML = "Hello JavaScript!";
    </script>
    <noscript>抱歉，您的浏览器不支持 JavaScript！</noscript>
    </body>
    </html>

在浏览器支持Javascript时呈现出“Hello Javascript！”，若浏览器不支持则显示“抱歉，您的浏览器不支持 JavaScript！”。