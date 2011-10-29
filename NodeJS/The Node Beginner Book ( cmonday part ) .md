# Node入门


<a name="about"></a>
## 关于
本书致力于教会你如何用Node.js来开发应用，过程中会传授你所有所需的“高级”JavaScript知识。本书绝不是一本“Hello World”的教程。  


<a name="status"></a>
### 状态
你正在阅读的已经是本书的最终版。因此，只有当进行错误更正以及针对新版本Node.js的改动进行对应的修正时，才会进行更新。  

本书中的代码案例都在Node.js 0.4.9版本中测试过，可以正确工作。  

<a name="intended-audience"></a>
### 读者对象
本书最适合与我有相似技术背景的读者： 至少对一门诸如Ruby，Python，PHP或者Java这样面向对象的语言有一定的经验；对JavaScript处于初学阶段，并且完全是一个Node.js的新手。  

这里指的适合对其他编程语言有一定经验的开发者，意思是说，本书不会对诸如数据类型、变量、控制结构等等之类的非常基础的概念做介绍。要读懂本书，这些基础的概念我都默认你已经会了。 

然而，本书还是会对JavaScript中的函数和对象做详细介绍，因为它们与其他同类编程语言中的函数和对象有很大的不同。  


<a name="structure"></a>
### 本书结构  
读完本书之后，你将完成一个完整的web应用，该应用允许用户浏览页面以及上传文件。  

当然了，应用本身并没有什么了不起的，相比为了实现该功能书写的代码本身，我们更关注的是如何创建一个框架来对我们应用的不同模块进行干净地剥离。
是不是很玄乎？稍后你就明白了。  

本书先从介绍在Node.js环境中进行JavaScript开发和在浏览器环境中进行JavaScript开发的差异开始。  

紧接着，会带领大家完成一个最传统的“Hello World”应用，这也是最基础的Node.js应用。  

最后，会和大家讨论如何设计一个“真正”完整的应用，剖析要完成该应用需要实现的不同模块，并开始一步一步介绍如何来实现这些模块。  

可以确保的是，在这过程中，大家会学到JavaScript中一些高级的概念、如何使用它们以及为什么使用这些概念就可以实现而其他编程语言中同类的概念就无法实现。  

该应用所有的源代码都可以通过[本书Github代码仓库](https://github.com/ManuelKiessling/NodeBeginnerBook/tree/master/code/application)来获取。  


### 目录
*  [关于](#about)  
    * [状态](#status)   
    * [读者对象](#intended-audience)   
    * [本书结构](#structure)  
*  [JavaScript与Node.js](#javascript-and-nodejs)  
    * [JavaScript与你](#javascript-and-you)  
    * [简短申明](#a-word-of-warning)  
    * [服务器端JavaScript](#server-side-javascript)  
    * [“Hello World”](#hello-world)  
*  [一个完整的基于Node.js的web应用](#a-full-blown-web-application-with-nodejs)  
    * [用例](#the-use-cases)  
    * [应用不同模块分析](#the-application-stack)  
*  [构建应用的模块](#building-the-application-stack)  
    * [一个基础的HTTP服务器](#a-basic-http-server)  
    * [分析HTTP服务器](#analyzing-our-http-server)  
    * [进行函数传递](#passing-functions-around)  
    * [函数传递是如何让HTTP服务器工作的](#how-function-passing-makes-our-http-server-work)  
    * [基于事件驱动的回调](#event-driven-callbacks)  
    * [服务器是如何处理请求的](#how-our-server-handles-requests)  
    * [服务端的模块放在哪里](#finding-a-place-for-our-server-module)  
    * [如何来进行请求的“路由”](#whats-needed-to-route-requests)  
    * [行为驱动执行](#execution-in-the-kindom-of-verbs)  
    * [路由给真正的请求处理器](#routing-to-real-request-handlers)  
    * [让请求处理器作出响应](#making-request-handlers-respond)  
        * [如何不这样做](#how-to-not-do-it)  
        * [阻塞与非阻塞](#blocking-and-non-blocking)  
        * [以非阻塞操作进行请求响应](#responding-request-handlers-with-non-blocking-operations)  
    * [更有用的场景](#serving-something-useful)  
        * [处理POST请求](#handling-post-requests)  
        * [处理文件上传](#handling-file-uploads)  
* [总结与展望](#conclusion-and-outlook)  


<a name="building-the-application-stack"></a>
## 构建应用的模块  

<a name="a-basic-http-server"></a>
### 一个基础的HTTP服务器  

<a name="analyzing-our-http-server"></a>
### 分析HTTP服务器  

<a name="passing-functions-around"></a>
### 进行函数传递  

<a name="how-function-passing-makes-our-http-server-work"></a>
### 函数传递是如何让HTTP服务器工作的  

<a name="event-driven-callbacks"></a>
### 基于事件驱动的回调  

<a name="how-our-server-handles-requests"></a>
### 服务器是如何处理请求的  

<a name="finding-a-place-for-our-server-module"></a>
### 服务端的模块放在哪里  