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
当我准备开始写我的第一个“真正的”Node.js应用的时候，我不但不知道怎么写Node.js代码，也不知道怎么组织这些代码。  
我应该把所有东西都放进一个文件里吗？网上有很多教程都会教你把所有的逻辑都放进一个用Node.js写的基础HTTP服务器里。但是如果我想加入更多的内容，同时还想保持代码的可读性呢？  

实际上，只要把不同功能的代码放入不同的模块中，保持代码分离还是相当简单的。  

这种方法允许你拥有一个干净的主文件（main file），你可以用Node.js执行它；同时你可以拥有干净的模块，它们可以被主文件和其他的模块调用。  

那么，现在我们来创建一个用于启动我们的应用的主文件，和一个保存着我们的HTTP服务器代码的模块。  

在我的印象里，把主文件叫做index.js或多或少是个标准格式。把服务器模块放进叫server.js的文件里则很好理解。  

让我们先从服务器模块开始。在你的项目的根目录下创建一个叫server.js的文件，并写入以下代码：  

    var http = require("http");
    
    http.createServer(function(request, response) {
    response.writeHead(200, {"Content-Type": "text/plain"});
      response.write("Hello World");
      response.end();
    }).listen(8888); 

搞定！你刚刚完成了一个可以工作的HTTP服务器。为了证明这一点，我们来运行并且测试这段代码。首先，用Node.js执行你的脚本：  

    node server.js

接下来，打开浏览器访问http://localhost:8888/ ，你会看到一个写着“Hello World”的网页。 

这很有趣，不是吗？让我们先来谈谈HTTP服务器的问题，把如何组织项目的事情先放一边吧，你觉得如何？我保证之后我们会解决那个问题的。  


<a name="analyzing-our-http-server"></a>
### 分析HTTP服务器  
那么接下来，让我们分析一下这个HTTP服务器的构成。  

第一行请求Node.js自带的*http*模块，并且把它赋值给*http*变量。  

接下来我们调用http模块提供的函数：*creatServer*。这个函数会返回一个对象，这个对象有一个叫做*listen*的方法，这个方法有一个数值参数，指定这个HTTP服务器监听的端口号。  

咱们暂时先不管*http.creatServer*的括号里的那个函数定义。  

我们本来可以用这样的代码来启动服务器并侦听8888端口：

    var http = require("http");    
    
    var server = http.createServer();   
    server.listen(8888);  

这段代码只会启动一个侦听8888端口的服务器，它不做任何别的事情，甚至连请求都不会应答。  

最有趣（而且，如果你之前习惯使用一个更加保守的语言，比如PHP，它还很奇怪）的部分是*createSever()*的第一个参数，一个函数定义。  

实际上，这个函数定义是*createServer()*的第一个也是唯一一个参数。因为在JavaScript中，函数和其他变量一样都是可以被传递的。  

<a name="passing-functions-around"></a>
### 进行函数传递  

举例来说，你可以这样做：

    function say(word) {
       console.log(word); 
    }
    
      function execute(someFunction, value) { 
      someFunction(value);
     }
    execute(say, "Hello");

请仔细阅读这段代码！在这里，我们把*say*函数作为*execute*函数的第一个变量进行了传递。这里返回的不是*say*的值，而是*say*本身！

这样一来，*say*就变成了*execute*中的本地变量*someFunction*，execute可以通过调用*someFunction()*（带括号的形式）来使用*say*函数。

当然，因为*say*有一个变量，*execute*在调用*someFunction*时可以传递这样一个变量。

我们可以，就像刚才那样，用它的名字把一个函数作为变量传递。但是我们不一定要绕这个“先定义，再传递”的圈子，我们可以直接在另一个函数的括号中定义和传递这个函数：

    function execute(someFunction, value) { 
      someFunction(value); 
    }
    
    execute(function(word){ console.log(word) }, "Hello");

我们在*execute*接受第一个参数的地方直接定义了我们准备传递给*execute*的函数。

用这种方式，我们甚至不用给这个函数起名字，这也是为什么它被叫做*匿名函数*。

这是我们和我所认为的“进阶”JavaScript的第一次亲密接触，不过我们还是得循序渐进。现在，我们先接受这一点：在JavaScript中，一个函数可以作为另一个函数接收一个参数。我们可以先定义一个函数，然后传递，也可以在传递参数的地方直接定义函数。

<a name="how-function-passing-makes-our-http-server-work"></a>
### 函数传递是如何让HTTP服务器工作的  

带着这些知识，我们再来看看我们简约而不简单的HTTP服务器：

    

<a name="event-driven-callbacks"></a>
### 基于事件驱动的回调  

<a name="how-our-server-handles-requests"></a>
### 服务器是如何处理请求的  

<a name="finding-a-place-for-our-server-module"></a>
### 服务端的模块放在哪里  