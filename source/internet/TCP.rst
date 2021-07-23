
TCP/IP协议
===========================

什么是 TCP/IP？
~~~~~~~~~~~~~~~~~~~~~

TCP/IP 是供已连接因特网的计算机进行通信的通信协议，也是是Internet最基本的协议、Internet国际互联网络的基础。TCP/IP 指传输控制协议/网际协议（Transmission Control Protocol / Internet Protocol）,其定义了电子设备（比如计算机）如何连入因特网，以及数据如何在它们之间传输的标准。

TCP/IP协议族
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

从字面意义上讲，有人可能会认为 TCP/IP 是指 TCP 和 IP 两种协议。实际生活当中有时也确实就是指这两种协议。然而在很多情况下，它是利用 IP 进行通信时所必须用到的协议群的统称。也就是说，它其实是个协议家族，由很多个协议组成，并且是在不同的层， 是互联网的基础通信架构。

常见基于 TCP 和 IP 这两个最初协议之上的通信协议如：http、https、ssl、smtp、mime、pop

TCP和IP协同工作
~~~~~~~~~~~~~~~~~~~~~~~~~~~

TCP/IP 意味着 TCP 和 IP 在一起协同工作，TCP 负责应用软件（比如您的浏览器）和网络软件之间的通信，IP 负责计算机之间的通信。

TCP 负责将数据分割并装入 IP 包，然后在它们到达的时候重新组合它们，IP 负责将包发送至接受者。

IP 路由器
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

当一个 IP 包从一台计算机被发送，它会到达一个 IP 路由器。IP 路由器负责将这个包路由至它的目的地，直接地或者通过其他的路由器。在一个相同的通信中，一个包所经由的路径可能会和其他的包不同。而路由器负责根据通信量、网络中的错误或者其他参数来进行正确地寻址。

http协议
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

HTTP协议，即超文本传输协议（英文：HyperText Transfer Protocol，缩写：HTTP）是一种用于分布式、协作式和超媒体信息系统的应用层协议。HTTP是万维网的数据通信的基础。

http协议是绝大部分网站所使用的协议，对http协议的报文格式以及参数要有个基本的了解

**1. 请求报文**

- **请求行**    GET、POST等请求方法 / url
- **头**        
            Host: baidu.com

            Cookie:  name=bai

            Content-type: application/x-www-from-urlencoded

            Use-Agent: chrome 83     
- **空行**
- **请求体**    usename=admin&password=1234


**2. 响应报文**

- **响应行**     HTTP/1.1 200 OK
            常见的响应状态码有：200、404、403、
- **头**        
            Content-Type: text/html;charset=utf-8
            
            Content-length: 2048
            
            Content-encoding: gzip
- **空行**
- **响应体**  
    .. code-block:: html
        :linenos:

        <html>
            <head>
            </head>
            <body>
                <h1>响应体</h1>
            </body>
        </html>
 
