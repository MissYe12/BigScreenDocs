
URL
============


url简介
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

URL是(Uniform Resource Locators)的缩写，意为统一资源定位器。URL是 Web 中的一个核心概念，它是浏览器用来检索 web 上公布的任何资源的机制。。

简单来说，每个URL指向一个资源的地址，比如一个HTML网页，一幅图像，等等。而在实际中，也有一些例外，最常见的情况就是一个 URL 指向了不存在的或是被移动过的资源。由于通过 URL 呈现的资源和 URL 本身由 Web 服务器处理，因此 web 服务器的拥有者需要认真地维护资源以及与它关联的URL。

url的组成
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

URL可以由字母组成，如"baidu.com"，或互联网协议（IP）地址： 192.68.20.50。

一个URL由不同的部分组成，其中一些是必须的，而另一些是可选的。让我们以下面这个URL为例看看其中最重要的部分

以这段网址为例：http://www.example.com:80/path/to/myfile.html?key1=value1&key2=value2#SomewhereInTheDocument

- **http 是协议**:它表明了浏览器必须使用何种协议。它通常都是HTTP协议或是HTTP协议的安全版，即HTTPS。Web需要它们二者之一，但浏览器也知道如何处理其他协议
- **www.example.com 是域名**:它表明正在请求哪个Web服务器。或者，可以直接使用IP 地址, 但是因为IP地址不太方便，在网络上不经常使用
- **:80  是端口**:它表示用于访问Web服务器上的资源的技术“门”。如果Web服务器使用HTTP协议的标准端口（HTTP为80，HTTPS为443）来授予其资源的访问权限，则通常会被忽略。否则是强制性的。
- **/path/to/myfile.html 是网络服务器上资源的路径**:在Web的早期阶段，像这样的路径表示Web服务器上的物理文件位置。如今，它主要是由没有任何物理现实的Web服务器处理的抽象。
- **?key1=value1&key2=value2 是提供给网络服务器的额外参数**: 这些参数是用 & 符号分隔的键/值对列表。在返回资源之前，Web服务器可以使用这些参数来执行额外的操作。每个Web服务器都有自己关于参数的规则，唯一可靠的方式来知道特定Web服务器是否处理参数是通过询问Web服务器所有者。
- **#SomewhereInTheDocument 是资源本身的另一部分的锚点** 锚点表示资源中的一种“书签”，给浏览器显示位于该“加书签”位置的内容的方向。例如，在HTML文档上，浏览器将滚动到定义锚点的位置;在视频或音频文档上，浏览器将尝试转到锚代表的时间。值得注意的是，＃后面的部分（也称为片段标识符）从来没有发送到请求的服务器。

URL 字符编码
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

URL 只能使用 ASCII 字符集来通过因特网进行发送。由于 URL 常常会包含 ASCII 集合之外的字符，URL 必须转换为有效的 ASCII 格式。

URL 编码使用 "%" 其后跟随两位的十六进制数来替换非 ASCII 字符。

URL 不能包含空格，所以编码通常使用 + 来替换空格。

URL的使用
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

可以直接在浏览器的地址栏里输入任何URL，来获得后台的资源(如 http://www.baidu.com 或者 14.215.177.38 ，这两种方式都能够进入百度首页)，这只是最简单的一种应用。

HTML语言对URL有大量的使用，比如：

Web浏览器通过URL从Web服务器请求页面。当您点击 HTML 页面中的某个链接时，对应的 <a> 标签指向万维网上的一个地址。

一个统一资源定位器(URL) 用于定位万维网上的文档。

一个网页地址实例: http://www.runoob.com/html/html-tutorial.html 语法规则:

scheme://host.domain:port/path/filename

绝对URL和相对URL(HTML文档中)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. 绝对 URL（Absolute URL）只靠 URL 本身就能确定资源的位置。这意味着，URL 必须带有资源的完整信息，包含协议、主机、路径等部分。前面的例子都是绝对 URL。绝对示例：

**完整网址**

https://developer.mozilla.org/en-US/docs/Learn

**隐去协议的形式**

//developer.mozilla.org/en-US/docs/Learn

在这种情况下，浏览器将使用与用于加载该URL的文档相同的协议来调用该URL。
    
**隐去域名的形式**

/en-US/docs/Learn

这是HTML文档中绝对URL最常见的用例。浏览器将使用与用于加载托管该URL的文档相同的协议和相同的域名。注意：不可能省略该域名而不省略协议。

1. 相对 URL（Relative URL）不包含资源位置的全部信息，必须结合当前网页的位置，才能定位资源。。相对URL示例：

为了更好地了解以下示例，我们假设从位于以下URL的文档中调用URL： https://developer.mozilla.org/en-US/docs/Learn

**子资源**

Skills/Infrastructure/Understanding_URLs

因为该URL不以/开头，浏览器将尝试在包含当前资源的子目录中查找文档。所以在这个例子中，我们真的想要达到这个URL 

https://developer.mozilla.org/en-US/docs/Learn/Skills/Infrastructure/Understanding_URLs

**回到目录树中**

../CSS/display

在这种情况下，我们使用从UNIX文件系统世界继承的../写入约定来告诉我们要从一个目录上升的浏览器。

在这里，我们要达到以下URL：https://developer.mozilla.org/en-US/docs/Learn/../CSS/display

可以将其简化为：https://developer.mozilla.org/en-US/docs/CSS/display







