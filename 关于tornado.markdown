一. Tornado简介
考虑应用场景 :
    1.用户量大、高并发
    2.大量HTTP持久连接

C10K问题:
    -Concurrently handing ten thousand connections 即并发10000个连接
    对于单台服务器来说这个根本无法承担，对于多台服务器来说又提高成本
tornado(服务器与框架结合体)

1.1tornado是何物:
tornado全称Tornado Web Server,是一个用python语言写成的Web应用框架，由FriendFeed公司在自己的网站FriendFeed中使用，
被Facebook收购以后再2009年9月以开源软件的形式开放给大众

特点:
    作为Web框架，是一个轻量级的Web框架，类似于另一个Python web框架Web.py，其拥有异步非阻塞IO的处理方式。
    作为Web服务器，Tornado拥有出色的抗压负载能力，官方用Nginx反向代理的方式部署Tornado和其他Python Web应用框架进行对比，
    结果最大浏览量超过第二名近40%
性能:
    Tornado拥有优异的性能，他试图解决C10K问题
    Tornado框架和服务器一起组成一个Wsgi的全栈替代品。单独在WSGI容器中使用Tornado网络框架或者tornado http服务器，
    有一定的局限性，为了最大化利用tornado的性能，推荐同时使用tornado的网络框架和Http服务器。

主要模块:
    web - FriendFeed 使用的基础 Web 框架，包含了 Tornado 的大多数重要的功能
    escape - XHTML, JSON, URL 的编码/解码方法
    database - 对 MySQLdb 的简单封装，使其更容易使用
    template - 基于 Python 的 web 模板系统
    httpclient - 非阻塞式 HTTP 客户端，它被设计用来和 web 及 httpserver 协同工作
    auth - 第三方认证的实现（包括 Google OpenID/OAuth、Facebook Platform、Yahoo BBAuth、FriendFeed OpenID/OAuth、Twitter        OAuth）
    locale - 针对本地化和翻译的支持
    options - 命令行和配置文件解析工具，针对服务器环境做了优化
底层模块:
    httpserver - 服务于 web 模块的一个非常简单的 HTTP 服务器的实现
    iostream - 对非阻塞式的 socket 的简单封装，以方便常用读写操作
    ioloop - 核心的 I/O 循环