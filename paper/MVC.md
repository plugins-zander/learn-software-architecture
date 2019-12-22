<https://zh.wikipedia.org/wiki/MVC>





# MVC[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=0&summary=/*%20top%20*/%20)]



**MVC模式**（Model–view–controller）是[软件工程](https://zh.wikipedia.org/wiki/%E8%BD%AF%E4%BB%B6%E5%B7%A5%E7%A8%8B)中的一种[软件架构](https://zh.wikipedia.org/wiki/%E8%BD%AF%E4%BB%B6%E6%9E%B6%E6%9E%84)模式，把软件系统分为三个基本部分：模型（Model）、视图（View）和控制器（Controller）。

MVC模式最早由[Trygve Reenskaug](https://zh.wikipedia.org/w/index.php?title=Trygve_Reenskaug&action=edit&redlink=1)在1978年提出[[1\]](https://zh.wikipedia.org/wiki/MVC#cite_note-1)，是[施乐帕罗奥多研究中心](https://zh.wikipedia.org/wiki/%E5%B8%95%E7%BE%85%E5%A5%A7%E5%A4%9A%E7%A0%94%E7%A9%B6%E4%B8%AD%E5%BF%83)（Xerox PARC）在20世纪80年代为程序语言[Smalltalk](https://zh.wikipedia.org/wiki/Smalltalk)发明的一种软件架构。**MVC模式**的目的是实现一种动态的程序设计，使后续对程序的修改和扩展简化，并且使程序某一部分的重复利用成为可能。除此之外，此模式透过对复杂度的简化，使程序结构更加直观。软件系统透过对自身基本部分分离的同时也赋予了各个基本部分应有的功能。专业人员可以依据自身的专长分组：

- 控制器（Controller）- 负责转发请求，对请求进行处理。
- 视图（View） - 界面设计人员进行图形界面设计。
- 模型（Model） - 程序员编写程序应有的功能（实现算法等等）、数据库专家进行数据管理和数据库设计(可以实现具体的功能)。

![img](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f0/ModelViewControllerDiagramZh.png/200px-ModelViewControllerDiagramZh.png)

## 目录

[TOC]

## 组件的互动[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=1)]

![img](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a0/MVC-Process.svg/200px-MVC-Process.svg.png)

将应用程序划分为三种组件，模型 - 视图 - 控制器（MVC）设计定义它们之间的相互作用。[[2\]](https://zh.wikipedia.org/wiki/MVC#cite_note-posa-2)

- **模型（Model）** 用于封装与应用程序的业务逻辑相关的数据以及对数据的处理方法。“ Model ”有对数据直接访问的权力，例如对数据库的访问。“Model”不依赖“View”和“Controller”，也就是说， Model 不关心它会被如何显示或是如何被操作。但是 Model 中数据的变化一般会通过一种刷新机制被公布。为了实现这种机制，那些用于监视此 Model 的 View 必须事先在此 Model 上注册，从而，View 可以了解在数据 Model 上发生的改变。（比如：[观察者模式](https://zh.wikipedia.org/wiki/%E8%A7%82%E5%AF%9F%E8%80%85%E6%A8%A1%E5%BC%8F)（[软件设计模式](https://zh.wikipedia.org/wiki/%E8%BD%AF%E4%BB%B6%E8%AE%BE%E8%AE%A1%E6%A8%A1%E5%BC%8F)））
- **视图（View）**能够实现数据有目的的显示（理论上，这不是必需的）。在 View 中一般没有程序上的逻辑。为了实现 View 上的刷新功能，View 需要访问它监视的数据模型（Model），因此应该事先在被它监视的数据那里注册。
- **控制器（Controller）**起到不同层面间的组织作用，用于控制应用程序的流程。它处理事件并作出响应。“事件”包括用户的行为和数据 Model 上的改变。

## 优点[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=2)]

在最初的[JSP](https://zh.wikipedia.org/wiki/JSP)网页中，像[数据库](https://zh.wikipedia.org/wiki/%E6%95%B0%E6%8D%AE%E5%BA%93)查询语句(SQL query)这样的数据层代码和像[HTML](https://zh.wikipedia.org/wiki/HTML)这样的表示层代码是混在一起。虽然有着经验比较丰富的开发者会将数据从表示层分离开来，但这样的良好设计通常并不是很容易做到的，实现它需要精心地计划和不断的尝试。MVC可以从根本上强制性地将它们分开。尽管构造MVC应用程序需要一些额外的工作，但是它带给我们的好处是毋庸置疑的。

首先，多个 View 能共享一个 Model 。如今，同一个Web应用程序会提供多种用户界面，例如用户希望既能够通过浏览器来收发[电子邮件](https://zh.wikipedia.org/wiki/%E7%94%B5%E5%AD%90%E9%82%AE%E4%BB%B6)，还希望通过手机来访问[电子邮箱](https://zh.wikipedia.org/wiki/%E7%94%B5%E5%AD%90%E9%82%AE%E7%AE%B1)，这就要求Web网站同时能提供[Internet](https://zh.wikipedia.org/wiki/Internet)界面和[WAP](https://zh.wikipedia.org/wiki/WAP)界面。在MVC设计模式中， Model 响应用户请求并返回响应数据，View 负责格式化数据并把它们呈现给用户，业务逻辑和表示层分离，同一个 Model 可以被不同的 View 重用，所以大大提高了代码的可重用性。

其次，Controller 是自包含（self-contained,指高独立内聚）的对象，与 Model 和 View 保持相对独立，所以可以方便的改变应用程序的数据层和业务规则。例如，把数据库从[MySQL](https://zh.wikipedia.org/wiki/MySQL)移植到[Oracle](https://zh.wikipedia.org/wiki/Oracle)，或者把[RDBMS](https://zh.wikipedia.org/wiki/RDBMS)数据源改变成[LDAP](https://zh.wikipedia.org/wiki/LDAP)数据源，只需改变 Model 即可。一旦正确地实现了控制器，不管数据来自数据库还是[LDAP](https://zh.wikipedia.org/wiki/LDAP)服务器，View 都会正确地显示它们。由于MVC模式的三个模块相互独立，改变其中一个不会影响其他两个，所以依据这种设计思想能构造良好的少互扰性的构件。

此外，Controller 提高了应用程序的灵活性和可配置性。Controller 可以用来连接不同的 Model 和 View 去完成用户的需求，也可以构造应用程序提供强有力的手段。给定一些可重用的 Model 、 View 和Controller 可以根据用户的需求选择适当的 Model 进行处理，然后选择适当的的 View 将处理结果显示给用户。

## 评价、误解及适用范围[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=3)]

MVC模式在概念上强调 Model, View, Controller 的分离，各个模块也遵循着由 Controller 来处理消息，Model 掌管数据源，View 负责数据显示的职责分离原则，因此在实现上，MVC 模式的 Framework 通常会将 MVC 三个部分分离实现：

- Model 负责数据访问，较现代的 Framework 都会建议使用独立的数据对象 (DTO, POCO, POJO 等) 来替代弱类型的集合对象。数据访问的代码会使用 Data Access 的代码或是 ORM-based Framework，也可以进一步使用 Repository Pattern 与 Unit of Works Pattern 来切割数据源的相依性。
- Controller 负责处理消息，较高端的 Framework 会有一个默认的实现来作为 Controller 的基础，例如 Spring 的 DispatcherServlet 或是 ASP.NET MVC 的 Controller 等，在职责分离原则的基础上，每个 Controller 负责的部分不同，因此会将各个 Controller 切割成不同的文件以利维护。
- View 负责显示数据，这个部分多为前端应用，而 Controller 会有一个机制将处理的结果 (可能是 Model, 集合或是状态等) 交给 View，然后由 View 来决定怎么显示。例如 Spring Framework 使用 JSP 或相应技术，ASP.NET MVC 则使用 Razor 处理数据的显示。

也因为 MVC 模式强调职责分离，所以在发展 MVC 应用时会产生很多文件，在 IDE (集成开发环境) 不够成熟时它会是个问题，但在现代主流 IDE 都能使用类别对象的信息来组织代码编辑的情况下，多文件早已不是问题，而且 MVC 模式会要求开发者进一步思考应用程序的架构 (Application Architecture)，而非用大杂烩的方式开发应用程序，对于应用程序的生命周期以及后续的可扩展与可维护性而言有相当正面的帮助。另外，MVC 职责分离也带来了一个现代软件工程要求的重要特性：可测试性 (Testability)，MVC-based 的应用程序在良好的职责分离的设计下，各个部分可独立行使[单元测试](https://zh.wikipedia.org/wiki/%E5%8D%95%E5%85%83%E6%B5%8B%E8%AF%95)，有利于与企业内的自动化测试、[持续集成](https://zh.wikipedia.org/wiki/%E6%8C%81%E7%BA%8C%E6%95%B4%E5%90%88) (Continuous Integration) 与[持续发行](https://zh.wikipedia.org/w/index.php?title=%E6%8C%81%E7%BA%8C%E7%99%BC%E8%A1%8C&action=edit&redlink=1) (Continuous Delivery) 流程集成，减少应用程序改版部署所需的时间。

MVC 模式的应用程序的目的就是希望打破以往应用程序使用的大杂烩程序撰写方式，并间接诱使开发人员以更高的架构导向思维来思考应用程序的设计，因此对于一个刚入门的初学者来说，架构导向的思考会有一定的门槛，需要较多的实现与练习才能具备相应的能力，大多数的初学者还是较习惯于大杂烩式的程序撰写，所以可能会对 MVC 模式抱持着排斥或厌恶的心态，然而 MVC (或是其他的[Design Patterns](https://zh.wikipedia.org/w/index.php?title=Design_Patterns&action=edit&redlink=1)) 都是有助于应用程序长远的发展，虽然大杂烩式的程序也可以用来发展长生命周期的应用程序，但是相较于 MVC，大杂烩式的程序在可扩展性和可维护性 (尤其是可测试性) 上会远比 MVC 复杂很多，相反的，MVC 模式的应用程序是在初始开发时期必须先思考并使用软件架构，使得开发时期会需要花较多心力，但是一旦应用程序完成后，可扩展性、可维护性和可测试性反而会因为 MVC 的特性而变得容易。

因此，MVC 模式在已有众多优秀 Framework 的现代，早就已经没有不适合小型应用的问题，小型的应用还是可以由 MVC Framework 的应用来获取 MVC 的优点，同时它也能作为未来小型应用扩展到大型应用时的基础与入门砖。若一开始就想要做大型应用，那么 MVC 模式的职责分离以及要求开发的架构思考会更适合大型应用的开发。

## 实际范例[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=4)]

这里有一个通过 [JavaScript](https://zh.wikipedia.org/wiki/JavaScript) 所实现的基于 MVC 模型，需要注意的是：MVC 不是一种技术，而是一种理念。

```
/** 模擬 Model, View, Controller */
var M = {}, V = {}, C = {};

/** Model 負責存放資料 */
M.data = "hello world";

/** View 負責將資料輸出到螢幕上 */
V.render = (M) => { alert(M.data); }

/** Controller 作為一個 M 和 V 的橋樑 */
C.handleOnload = () => { V.render(M); }

/** 在網頁讀取的時候呼叫 Controller */
window.onload = C.handleOnload;
```

在这个简短的代码中就具有一个完整的 MVC 模式。

## 实现[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=5)]

### [MFC](https://zh.wikipedia.org/wiki/MFC)[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=6)]

[微软](https://zh.wikipedia.org/wiki/%E5%BE%AE%E8%BD%AF)所推出的[MFC](https://zh.wikipedia.org/wiki/MFC) Document/View架构是早期对于MVC模式的实现，[MFC](https://zh.wikipedia.org/wiki/MFC)将程序分成CView以及CDocument两大类别，其中的Document对应MVC中的 Model ，View 相当于MVC中的 View＋Controller，再加上CWinApp类别，合成三大项。但是基本上[MFC](https://zh.wikipedia.org/wiki/MFC)是一个失败的MVC模式作品。

由于[MFC](https://zh.wikipedia.org/wiki/MFC)之下的Document/View 定义过于模糊，未将Controller（MessageMap）部分取出，因此 Controller 可以置入 View 或Document，但不管置入哪一方面，都会与View或Document绑死，没有弹性。

### [Java](https://zh.wikipedia.org/wiki/Java)[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=7)]

#### [Java](https://zh.wikipedia.org/wiki/Java) 平台企业版 (J2EE)[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=8)]

和其他的各种框架不一样，J2EE为模型对象（Model Objects）定义了一个规范。

- 视图(View)

  在J2EE应用程序中，视图（View）可能由Java Server Page(JSP)担任。生成 View 的代码则可能是一个[servlet](https://zh.wikipedia.org/wiki/Servlet)的一部分，特别是在客户端服务端交互的时候。

- 控制器（Controller）

  [J2EE](https://zh.wikipedia.org/wiki/J2EE)应用中，Controller 可能是一个[servlet](https://zh.wikipedia.org/wiki/Servlet)。

  除了可直接以J2EE来撰写外，亦可用其他框架来撰写，常见的有[Struts2](https://zh.wikipedia.org/wiki/Struts2)、[Spring Framework](https://zh.wikipedia.org/wiki/Spring_Framework)……等等。

- 模型（Model）

  Model 则是由一个[实体Bean](https://zh.wikipedia.org/wiki/JavaBean)来实现。

#### Java [Swing](https://zh.wikipedia.org/wiki/Swing_(Java))[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=9)]

Swing是一个标准的MVC结构. ComponentUI代表 View, 负责描画组件. 组件尤其 Model 层, 比如JTextField的Document, JTable的TableModel, JTree的TreeModel等等. 而Control可能不是很明显, 我们或许可以简单的将其Event机制看作一个Swing团队开发给开发者的 Controller。

作为Java开发者, 如果想理解MVC的结构, 学习Swing的确是个不错的选择.

### [.NET](https://zh.wikipedia.org/wiki/.NET_Framework)[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=10)]

#### ASP.NET[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=11)]

在ASP.NET中，针对视图（View）和控制器（Controller）的模式没有被很好地定义。而模型（Model）则留给开发者去设计。

- 视图（View）

  ASPX和ASCX文件被用来处理 View 的职责。在这个设计中 View 实际上是从 Controller 继承而来。这个和Smalltalk的实施有所不同，在Smalltalk中不同的类都有指针互相指向对方.

- 控制器（Controllers）

  Controller 的职责被分割成两部分。事件（Event）的产生和传输是框架的一部分，更明确的说是Page和Control两个类。而事件的处理则在分离的代码中实现。

- 模型（Model）

  ASP.NET 不严格需要一个 Model。开发者可以自行选择创建一个 Model 类，但是很多人选择放弃这一步，直接把事件处理放在 Controller 里处理任何计算、数据保存等等。但用 Model 来包含商业逻辑和数据访问是可实现的。

#### ASP.NET MVC[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=12)]

- [ASP.NET MVC](https://zh.wikipedia.org/wiki/ASP.NET_MVC_Framework)，在2013年10月17日稳定版本已到5.0版。[[3\]](https://zh.wikipedia.org/wiki/MVC#cite_note-3)

此外，在ASP.NET MVC中，一般情况下Model通常搭配[LINQ to SQL](https://zh.wikipedia.org/wiki/%E8%AA%9E%E8%A8%80%E9%9B%86%E6%88%90%E6%9F%A5%E8%A9%A2)类别（使用O/R Designer工具所制作而成的DBML档）或ADO.NET实体数据模型（Entity Data Model，使用[ADO.NET Entity Framework](https://zh.wikipedia.org/wiki/ADO.NET_Entity_Framework)制作出的EDMX档）来实现。

#### [Windows](https://zh.wikipedia.org/wiki/Windows) Forms[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=13)]

在WinForms中，这个针对视图（View）和控制器（Controller）的模式已经很好的定义。而模型（Model）则留给开发者去设计。

- 视图（View）

  由Form或者Control类继承来的一个类处理 View 的职责。在WinForm这个例子中 View 和 Controller 被编译在同一个类中，这个和ASP.NET不同。

- 控制器（Controller）

  Controller 的职责被分割成三部分。事件（Event）的产生和传输是操作系统的一部分。在.Net框架中Form和Control类将不同的事件转发给相应的事件处理器。而事件的处理则在分离的代码中实现。

- 模型（Model）

  就像ASP.NET一样，WinForm不严格需要一个 Model。开发者可以自行选择创建一个 Model 类，但是很多人选择放弃这一步，直接把事件处理放在 Controller 里处理任何计算、数据保存等等。也就是说用Model来包含商业逻辑和数据访问。

### Perl[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=14)]

[Catalyst](https://zh.wikipedia.org/wiki/Catalyst)和[Jifty](https://zh.wikipedia.org/w/index.php?title=Jifty&action=edit&redlink=1)是透过[Perl](https://zh.wikipedia.org/wiki/Perl)语言所开发出来的Web Framework，都采用Model-View-Controller 架构。Catalyst 本身只是做了 Controller，View 和 Model 让开发者自由选用 CPAN 上的模块开发，例如 Template 和 Template Declare 都可用来产生视图。Jifty 将 MVC 完全实做完成，View 的部分在早期版本使用 Mason 实做，较新版本使用 Template Declare。

### Ruby on Rails[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=15)]

[Ruby on Rails](https://zh.wikipedia.org/wiki/Ruby_on_Rails)是透过[Ruby](https://zh.wikipedia.org/wiki/Ruby)语言所开发出来的 Web Framework，也是采用 Model-View-Controller 架构。Model 部分使用 [Active Record](https://zh.wikipedia.org/wiki/Active_Record) 概念实做，加上 Migration 机制，使得其 Model 结构非常容易控制。

### Python[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=16)]

[Python](https://zh.wikipedia.org/wiki/Python) 有许多的 MVC 架构。最常用的有 [Django](https://zh.wikipedia.org/wiki/Django) 和 [TurboGears](https://zh.wikipedia.org/wiki/TurboGears)。

### JavaScript[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=17)]

- [Backbone.js](https://zh.wikipedia.org/wiki/Backbone.js)
- [Angular.js](https://zh.wikipedia.org/wiki/AngularJS)
- [Ember.js](http://emberjs.com/)
- [JavaScriptMVC](https://zh.wikipedia.org/wiki/JavaScriptMVC)
- [Model-View-Controller (MVC) with JavaScript](https://web.archive.org/web/20070927183315/http://www.alexatnet.com/node/8)

### [PHP](https://zh.wikipedia.org/wiki/PHP)[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=18)]

- [CakePHP](http://cakephp.org/)
- [CodeIgniter](http://codeigniter.org.cn/)
- [prado](https://web.archive.org/web/20130531051303/http://www.pradosoft.com/)
- [symfony](http://www.symfony.com/)
- [Yii Framework](http://www.yiiframework.com/)
- [Zend Framework](http://framework.zend.com/)
- [Phalcon](http://phalconphp.com/)
- [Laravel](https://laravel.com/)
- [ThinkPHP](http://www.thinkphp.cn/)

### ActionScript 3[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=19)]

- [PureMVC Standard for ActionScript 3](https://web.archive.org/web/20081121204026/http://trac.puremvc.org/PureMVC_AS3#PureMVCStandardforAS3/)

## 参考[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=20)]

- [JSP model 2 architecture](https://zh.wikipedia.org/w/index.php?title=JSP_model_2_architecture&action=edit&redlink=1)

## 参考文献[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=21)]

1. **^** Reenskaug, Trygve. [THING-MODEL-VIEW-EDITOR: an Example from a planningsystem](http://heim.ifi.uio.no/~trygver/2007/MVC_Originals.pdf) (PDF).
2. **^** Buschmann, Frank (1996) *Pattern-Oriented Software Architecture*.
3. **^** [ASP.NET MVC 概观](http://msdn.microsoft.com/zh-tw/library/dd381412.aspx)

## 外部链接[[编辑](https://zh.wikipedia.org/w/index.php?title=MVC&action=edit&section=22)]

- [An overview of the MVC pattern in Java from the Sun website](http://java.sun.com/blueprints/patterns/MVC.html)
- [Model View Presenter with ASP.NET](https://web.archive.org/web/20080829142328/http://www.codeproject.com/aspnet/ModelViewPresenter.asp) CodeProject article.
- [History of the evolution of MVC and derivatives](http://www.martinfowler.com/eaaDev/uiArchs.html) by Martin Fowler.
- [ASP.NET MVC Framework](https://weblogs.asp.net/scottgu/archive/2007/10/14/asp-net-mvc-framework.aspx) Microsoft's Scott Guthrie on .NET MVC
- [Introduction to the ASP.NET Model View Controller (MVC) Framework](https://web.archive.org/web/20090705155110/http://download.microsoft.com/download/f/e/b/febedc0c-dd47-4062-ad53-40e34d556a5d/ScottHanselmanIntroToMVC.wmv) Scott Hanselman builds an application step-by-step using the first CTP of the ASP.NET MVC Framework in this Introductory Video
- Holub, Allen. [Building user interfaces for object-oriented systems](http://www.javaworld.com/javaworld/jw-07-1999/jw-07-toolbox.html). Java World. 1999.
- Greer, Derek. "[Interactive Application Architecture Patterns](https://web.archive.org/web/20081231140700/http://ctrl-shift-b.blogspot.com/2007/08/interactive-application-architecture.html)", Ctrl-Shift-B, 2007.
- [Building Graphical User Interfaces with the MVC Pattern in Java](http://pclc.pace.edu/~bergin/mvc/mvcgui.html)[*永久失效链接*]

分类

- [软件设计模式](https://zh.wikipedia.org/wiki/Category:%E8%BD%AF%E4%BB%B6%E8%AE%BE%E8%AE%A1%E6%A8%A1%E5%BC%8F)
- [MVC](https://zh.wikipedia.org/wiki/Category:MVC)