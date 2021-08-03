
DOM
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

什么是DOM
-----------------------------------
DOM是一项W3C标准，全称Document Object Model(文档对象模型)：

- 文档：整个HTML网页
- 对象：网页中的每一个部分都转换为了一个对象
- 模型：对象间的关系，便于获取对象

W3C DOM 标准被分为 3 个不同的部分：

- Core DOM - 所有文档类型的标准模型
- XML DOM - XML 文档的标准模型
- HTML DOM - HTML 文档的标准模型


构成网页最基本的组成部分是节点Node，网页中的每一部分都可以称为是一个节点。常用的具体节点类型：

- 标签——元素节点
- 属性——属性节点
- 文本——文本节点
- 文档——文档节点

节点通用属性

.. list-table::     
    :widths: 15 10 20 10
    :header-rows: 1

    * - 
      - nodeName
      - nodeType(返回节点类型)
      - nodeValue
    * - 文档节点
      - #document
      - 9
      - null
    * - 元素节点
      - 标签名
      - 1
      - null
    * - 属性节点
      - 属性名
      - 2
      - 属性值
    * - 文本节点
      - #text
      - 3
      - 文本内容


DOM查询
-----------------------------------
查找HTML元素

===================================== ======================================
方法                                    描述
document.getElementById         	      通过元素 id 来查找元素
document.getElementsByTagName           通过标签名来查找元素
document.getElementsByClassName         通过类名来查找元素
document.getElementByName               通过name属性来查找一组元素
document.querySelectorAll()             通过CSS选择器查找元素
===================================== ======================================

获取元素节点的子节点、父节点、兄弟节点

================== ============================================
属性                    描述
childNodes              表示当前节点的所有子节点(包括文本节点)
firstChild              表示当前节点的第一个子节点(包括文本节点)
lastChild               表示当前节点的最后一个子节点(包括文本节点)          
parentNode              表示当前节点的父节点
previousSibling         表示当前节点的前一个兄弟节点(包括文本节点)
nextSibling             表示当前节点的后一个兄弟节点(包括文本节点)
================== ============================================

查找 HTML 对象

===================================== ============================================
属性                                    描述
document.anchors                        返回拥有 name 属性的所有 <a> 元素
document.applets                        返回所有 <applet> 元素（HTML5 不建议使用）
document.baseURI                        返回文档的绝对基准 URI
document.body                           返回 <body> 元素
document.cookie                         返回文档的 cookie
document.doctype                        返回文档的 doctype
document.documentElement                返回 <html> 元素
document.documentMode                   返回浏览器使用的模式
document.documentURI                    返回文档的 URI
document.domain                         返回文档服务器的域名
document.embeds                         返回所有 <embed> 元素
document.forms                          返回所有 <form> 元素
document.head                           返回 <head> 元素
document.images                         返回所有 <img> 元素
document.implementation                 返回 DOM 实现
document.inputEncoding                  返回文档的编码（字符集）
document.lastModified                   返回文档更新的日期和时间
document.links                          返回拥有 href 属性的所有 <area> 和 <a> 元素
document.readyState                     返回文档的（加载）状态
document.referrer                       返回引用的 URI（链接文档）
document.scripts                        返回所有 <script> 元素
document.strictErrorChecking            返回是否强制执行错误检查
document.title                          返回 <title> 元素
document.URL                            返回文档的完整 URL
===================================== ============================================

示例：

.. code-block:: html
    :linenos:

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Document</title>
    </head>
    <body>
        <div id='total'> 
            <div id='inner'>
                <p>饮料：</p>
                <ul id='drinks'> 
                    <li class='Carbonated'>可乐</li>
                    <li class='Carbonated'>雪碧</li>
                    <li>牛奶</li>
                    <li>咖啡</li>
                </ul>    
            </div>      
        </div>
    
        <button id='button1'>通过元素 id 来查找元素</button><br>
        <button id='button2'>通过标签名来查找元素</button><br>
        <button id='button3'>通过类名来查找元素</button><br>
        <button id='button4'>通过选择器来查找元素</button><br>
        <button id='button5'>表示当前节点的所有子节点</button><br>
        <button id='button6'>表示当前节点的最后一个子节点</button><br>
        <script>
            //创建单击响应函数
            function clickResponse(idString, action) {
                var buttonVariable = document.getElementById(idString);
                buttonVariable.onclick = action;
            }
    
            //通过元素 id 来查找元素
            clickResponse('button1', function() {
                var but1 =  document.getElementById('button1');
                alert(but1.innerHTML);
            });
    
            //通过标签名来查找元素
            clickResponse('button2', function() {
                var but2 =  document.getElementsByTagName('li')
                alert(but2[2].innerHTML);
            });
    
            //通过类名来查找元素
            clickResponse('button3', function() {
                var but3 =  document.getElementsByClassName('Carbonated');
                alert(but3[0].innerHTML);
            });
    
            //通过选择器来查找元素
            clickResponse('button4', function() {
                var but4 =  document.querySelectorAll('li.Carbonated');
                alert(but4[0].innerHTML);
            });
    
            //表示当前节点的所有子节点
            clickResponse('button5', function() {
                var but5 =  document.getElementById('drinks');
                var but5Child = but5.childNodes;
                for(var i = 0; i < but5Child.length; i++)
                alert(but5Child[i].innerHTML);
            });
    
            //表示当前节点的最后一个子节点
            clickResponse('button6', function() {
                var but6 =  document.getElementById('drinks');
                var but6Child1 = but6.lastChild;
                var but6Child2 = but6.lastElementChild;
                alert(but6Child1.innerHTML);
                alert(but6Child2.innerHTML);
            });
    
        </script>
    </body>
    </html>

DOM的增删改
-----------------------------------
改变HTML元素

======================================= ============================================
方法                                        描述
element.innerHTML = new html content        改变元素的 inner HTML
element.attribute = new value               改变 HTML 元素的属性值
element.setAttribute(attribute, value)      改变 HTML 元素的属性值
element.style.property = new style          改变 HTML 元素的样式
======================================= ============================================

增加和删除元素

======================================= ============================================
方法                                        描述
document.createElement(标签名)               创建元素节点
document.TextNode(文本内容)                  创建文本节点
removeChild(refChild)                       删除元素节点
appendChild(newChild)                       向父节点中添加新的子节点
replaceChild(newChild,refChild)             替换元素子节点
insertBefore(newChild,refChild)             在指定的子节点前面插入新的子节点
======================================= ============================================


示例：

.. code-block:: html
    :linenos:

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Document</title>
    </head>
    <body>
        <div id='total'> 
            <div id='inner'>
                <p>饮料：</p>
                <ul id='drinks'> 
                    <li class='Carbonated' id="cola">可乐</li>
                    <li class='Carbonated'>雪碧</li>
                    <li id="milk">牛奶</li>
                    <li id="coffee">咖啡</li>
                </ul>    
            </div>      
        </div>
        <button id='button1'>创建一个节点到'drinks'下</button><br>
        <button id='button2'>创建一个节点到'可乐'前</button><br>
        <button id='button3'>用一个节点替换'咖啡'并删除'牛奶'</button><br>
        <script>
            //创建单击响应函数
            function clickResponse(idString, action) {
                var buttonVariable = document.getElementById(idString);
                buttonVariable.onclick = action;
            }

            //创建一个节点到'drinks'下
            clickResponse('button1', function() {
                var juice = document.createElement('li');
                var drinks = document.getElementById('drinks');
                juice.innerHTML = '果汁';

                //向父节点中添加新的子节点
                drinks.appendChild(juice);
            });

            //创建一个节点到'可乐'前
            clickResponse('button2', function() {
                var milky_tea = document.createElement('li');
                var drinks = document.getElementById('drinks');
                var cola = document.getElementById('cola');
                milky_tea.innerHTML = '奶茶';
                drinks.insertBefore(milky_tea,cola);
            });

            //用一个节点替换'咖啡'并删除'牛奶'
            clickResponse('button3', function() {
                var soda = document.createElement('li');
                var drinks = document.getElementById('drinks');
                var coffee = document.getElementById('coffee');
                var milk = document.getElementById('milk');
                soda.innerHTML = '苏打水';
                drinks.replaceChild(soda,coffee);

                //与drinks.removeChild(milk);等效
                milk.parentNode.removeChild(milk);
            });

        </script>
    </body>
    </html>