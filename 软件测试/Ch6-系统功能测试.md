<!-- Slide number: 1 -->

![](img/Ch6_图片1.jpg)
# 软件测试方法和技术
第6章 系统功能测试
同济大学  朱少民
版权所有©️ 仅限于教学使用

### Notes:

<!-- Slide number: 2 -->
6.1 功能测试方法与过程
6.2 功能测试自动化
6.3 回归测试
6.4 精准测试
版权所有©️ 仅限于教学使用

### Notes:
重难点小结
测试需求分析、探索式测试、SBTM、自动化测试脚本开发与维护
课后实践练习
基于Selenium的系统功能测试实验
部署自动化测试框架

<!-- Slide number: 3 -->

![](img/Ch6_图片3.jpg)
# 6.1 功能测试方法与过程

### Notes:
列写本课时的学习要点，依次开始深入讲解。
如有学习要求，请列写在课时要点之后。
在保持内容版式整洁的前提下，重点的学习内容，请尽量详细的列写在讲义中，让大家在单独看讲义时也可以学习。
讲义非语音讲解辅助，而是学习的一个主体。

概念，学习要点的概念介绍，以及在工作中什么场景会用到
讲解，工作中胜任这个能力，需要掌握的知识、技术能详细讲解
举例，举一个案例或demo 帮助大家更好理解要学习的内容，以及知道怎么用
分享经验，你对这个学习要点的工作应用心得。特别是理论和实际的差异的部分。
学习建议，给出一些相关学习或工作场景中使用的建议
实用工具，这个学习要点对应的一些工具模板（如果有）

<!-- Slide number: 4 -->
# 功能测试方法与应用
功能测试要求和基本思路
测试需求分析方法
探索式测试及其测试实践
SBTM
回归测试及其策略
精准测试

![See the source image](img/Ch6_Picture2.jpg)

### Notes:
十、功能测试方法与过程
功能测试要求和基本思路
测试需求分析方法
探索式测试及其测试实践
SBTM
回归测试及其策略
精准测试

<!-- Slide number: 5 -->
# 系统功能测试究竟测什么？
功能（Function）
逻辑（Logic）
接口（API）
界面（UI）
数据（Data）
操作（Operation）
平台（Platform

![查看源图像](img/Ch6_Picture2.jpg)

### Notes:
十、功能测试方法与过程
功能测试要求和基本思路
测试需求分析方法
探索式测试及其测试实践
SBTM
回归测试及其策略
精准测试

<!-- Slide number: 6 -->
# 系统功能测试应该考虑哪些问题？

![屏幕快照 2017-04-25 下午4.36.49.png](img/Ch6_图片4.jpg)

![屏幕快照 2017-04-25 下午4.36.29.png](img/Ch6_图片2.jpg)

### Notes:
十、功能测试方法与过程
功能测试要求和基本思路
测试需求分析方法
探索式测试及其测试实践
SBTM
回归测试及其策略
精准测试

<!-- Slide number: 7 -->
# 系统功能测试的基本思路

![屏幕快照 2017-04-25 下午4.39.15.png](img/Ch6_图片3.jpg)

![屏幕快照 2017-04-25 下午4.42.00.png](img/Ch6_图片5.jpg)

### Notes:
十、功能测试方法与过程
功能测试要求和基本思路
测试需求分析方法
探索式测试及其测试实践
SBTM
回归测试及其策略
精准测试

<!-- Slide number: 8 -->

![屏幕快照 2017-04-25 下午4.40.11.png](img/Ch6_图片2.jpg)
# 系统功能测试的基本思路

### Notes:
十、功能测试方法与过程
功能测试要求和基本思路
测试需求分析方法
探索式测试及其测试实践
SBTM
回归测试及其策略
精准测试

<!-- Slide number: 9 -->
# 面向接口的功能测试

![](img/Ch6_图片5.jpg)

<!-- Slide number: 10 -->
# HTTP协议

![](img/Ch6_图片10.jpg)
＜request-line＞＜headers＞＜blank line＞[＜request-body＞
请求
＜status-line＞＜headers＞＜blank line＞[＜response-body＞]
响应
https://www.w3.org/Protocols/
10

### Notes:

<!-- Slide number: 11 -->
# Webservice接口
WebService是一个不依赖于语言、平台的SOA的架构，可以实现基于Http协议、不同语言（通过 xml 描述）间的相互调用、网络应用间的交互。
Soap(Simple Object Access Protocol)，XML Web Service 的通信协议（调用方法的规范），支持不同的底层接口，如HTTP(S)、SMTP
WSDL(Web Services Description Language) ， XML 文档——用于说明一组 SOAP 消息以及如何交换这些消息
UDDI (Universal Description, Discovery, and Integration) 根据描述文档来引导系统查找相应服务的机制。UDDI利用SOAP消息机制（标准的XML/HTTP）来发布、编辑、浏览以及查找注册信息。采用XML格式来封装各种不同类型的数据，发送到注册中心或者由注册中心返回所需数据
11

<!-- Slide number: 12 -->
# 面向UI的功能测试

![See the source image](img/Ch6_Picture2.jpg)
重点测试功能逻辑，按功能、子功能、功能点等层次展开测试
基于输入域和组合测试等方法（见第3章）进行输入的设计，驱动测试，并观察输出
扮演用户角色，从应用场景来遍历用户使用产品的主要操作路径
针对不同设置进行测试
用户界面测试

<!-- Slide number: 13 -->

![](img/Ch6_图片2.jpg)
# 6.2 功能测试自动化

### Notes:
十一、功能测试自动化
面向接口的自动化测试
Web客户端的UI自动化测试
基于Cypress的UI自动化测试
Android应用的UI自动化测试
数据驱动/关键字驱动
自动化测试框架

<!-- Slide number: 14 -->
# 功能测试自动化

![](img/Ch6_图片2.jpg)
面向接口的自动化测试
Web客户端的UI自动化测试
基于Cypress的UI自动化测试
Android应用的UI自动化测试
iOS 和 Appium 内容，可以在第9章进行讨论
或让学生参考教材6.2.5和6.2.6 小节在课外实践、自主学习

### Notes:

<!-- Slide number: 15 -->
# 分层自动化测试
单元测试更容易实现自动化测试，RoI也更高（收益显著）
API自动化测试也基本能做到100%
适当加强手工端到端测试（业务层）
概括起来：以底层测试、接口测试、功能逻辑测试等为主，尽量避免UI测试

![http://blog.goneopen.com/wp-content/uploads/2010/08/crispin-test-automation-pyramid.png](img/Ch6_Picture4.jpg)
缺陷更易定位
效率更高
更加接近业务
反映真实需求

### Notes:

<!-- Slide number: 16 -->
API自动化测试

<!-- Slide number: 17 -->
# API的TA架构

回归
执行
触发回归
结果展示
定时回归
即时触发
事件触发
按需回归

用例
验证
场景设定
选择和组装API
手工组装
HAR 批量生成
代码迁移
基于场景的测试用例
API的来源
文档化工具
手工录入
程序扫描
HAR导入
RAML
Swagger
Markdown
API定义
RAML：RESTful API描述性语言；HAR：基于JSON、储存HTTP请求/响应信息的文件格式

<!-- Slide number: 18 -->
# API 测试流程

![](img/Ch6_图片3.jpg)

API的接入步骤-批量生成
脚本的修改
过滤与保存
HAR文件

动态测试
Thrift
Thrift code_gen
Dynamic Class
Loading
Dynamic Call Method

<!-- Slide number: 19 -->
# Swagger UI测试示例

![](img/Ch6_图片3.jpg)

![](img/Ch6_图片4.jpg)

<!-- Slide number: 20 -->
# API 测试示例

![](img/Ch6_图片4.jpg)

![](img/Ch6_图片5.jpg)
20

<!-- Slide number: 21 -->
# 基于API的TA工具

![](img/Ch6_图片3.jpg)

<!-- Slide number: 22 -->
# 基于API的TA工具 -续
Mockbin：可从HAR文件生成一个模拟桩
RAP：淘宝开发的API管理工具
Swagger：流行的API定义工具、规范
Easy Mock：从swagger生成数据
Doclever：编写REST接口文档，生成测试数据
Mocky：无需登录，直接生成response
kristofa/mock-http-server
wiremock
SoapUI
Rest-Assured
SOAtest
APIfortress

<!-- Slide number: 23 -->
# Rest-Assured
http://rest-assured.io/
http://localhost:8080/lotto/{id}
{ "lotto":
   { "lottoId":5,
"winning-numbers":[2,45,34,23,7,5,3], "winners":[
{
"winnerId":23, "numbers":[2,45,34,23,3,5]
},
{
"winnerId":54, "numbers":[52,3,12,11,18,22]
 }
]
}
}
REST-assured 是一个用于测试和验证RESTful服务的Java DSL, 使得为基于HTTP的RESTful服务编写测试变得更加简单
@Test public void lotto_resource_returns_200_with_expected_id_and_winners()
 {
when().
get("/lotto/{id}", 5).
then().
statusCode(200).
body("lotto.lottoId", equalTo(5),
"lotto.winners.winnerId", hasItems(23, 54));
}
https://github.com/rest-assured/rest-assured
23

<!-- Slide number: 24 -->
# Rest-Assured 参数化
given().
param("param1", "value1").
param("param2", "value2").
when().
get("/something");
given().
formParam(“formParamName”, “value1”). queryParam(“queryParamName”, “value2”).
when().
      post(“/something”);

..when().get("/name?firstName=John&lastName=Doe");
24

<!-- Slide number: 25 -->
# Rest-Assured + JUnit

![屏幕快照 2015-08-28 下午10.04.57.png](img/Ch6_图片4.jpg)

![](img/Ch6_图片3.jpg)

<!-- Slide number: 26 -->
# REST API测试

![屏幕快照 2016-12-20 下午10.37.02.png](img/Ch6_图片3.jpg)

![屏幕快照 2016-12-20 下午10.37.14.png](img/Ch6_图片4.jpg)

### Notes:

<!-- Slide number: 27 -->
UI自动化测试
Web客户端的UI自动化测试
基于Cypress的UI自动化测试
Android应用的UI自动化测试

<!-- Slide number: 28 -->
# Web UI的自动化测试
启动Chrome的插件
Selenium IDE

![](img/Ch6_图片4.jpg)
设定：
Project name
Base URL

![](img/Ch6_图片10.jpg)
28

### Notes:
，有时绕不过去，有时无需绕过去

<!-- Slide number: 29 -->
# Web UI的自动化测试 –续

![](img/Ch6_图片5.jpg)
29

### Notes:
，有时绕不过去，有时无需绕过去

<!-- Slide number: 30 -->
# Selenium 支持不同脚本语言

![](img/Ch6_图片6.jpg)

![](img/Ch6_图片10.jpg)

### Notes:

<!-- Slide number: 31 -->
# Selenium + WebDriver

![](img/Ch6_图片1.jpg)

### Notes:

<!-- Slide number: 32 -->
# WebDriver 架构

![](img/Ch6_图片4.jpg)
32

<!-- Slide number: 33 -->
# UI Object

![屏幕快照 2013-07-06 下午9.00.18.png](img/Ch6_图片4.jpg)

### Notes:

<!-- Slide number: 34 -->
# Page Objects

![屏幕快照 2013-07-27 下午9.37.14.png](img/Ch6_图片1.jpg)
http://code.google.com/p/selenium/wiki/PageObjects

### Notes:
http://blog.activelylazy.co.uk/2011/07/09/page-objects-in-selenium-2-0/

Tests with Page Objects
The page object encapsulates all the logic about how to perform certain actions. Our test now only needs to deal with what to actually do – so what does our test look like now?
AmazonHomePage homePage = AmazonHomePage.navigateTo(driver);
AmazonSearchResultsPage resultsPage =
    homePage.searchFor("iain banks");
assertThat(resultsPage.getTopResultTitle(), is("Transition"));
This is a pretty neat specification for our test: given a user on the amazon home page, when the user searches for ‘iain banks’, then the title of the top result is ‘Transition’.
There’s no implementation details in our test now. If any of the implementation details around searching change – we only need to change our page object.

<!-- Slide number: 35 -->
# PageFactory

![屏幕快照 2013-07-27 下午9.51.30.png](img/Ch6_图片8.jpg)

![屏幕快照 2013-07-27 下午9.51.41.png](img/Ch6_图片9.jpg)
http://code.google.com/p/selenium/wiki/PageFactory

### Notes:
In order to support the PageObject pattern, WebDriver's support library contains a factory class.

<!-- Slide number: 36 -->
# 基于Cypress的UI自动化测试

![](img/Ch6_图片4.jpg)
https://www.cypress.io/

<!-- Slide number: 37 -->
# Cypress 架构

![](img/Ch6_图片4.jpg)

<!-- Slide number: 38 -->
# 安装和使用简单

![Cypress with the Create new empty spec button highlighted](img/Ch6_Picture2.jpg)
cd /your/project/path
npm install cypress --save-dev

![The new spec confirmation dialog](img/Ch6_Picture4.jpg)
安装
https://docs.cypress.io/_nuxt/videos/installing-cli.3465fe6.mp4
打开： npx cypress open

![](img/Ch6_图片12.jpg)
https://docs.cypress.io/guides

<!-- Slide number: 39 -->
# Cypress 脚本

![](img/Ch6_图片4.jpg)

![](img/Ch6_图片6.jpg)

<!-- Slide number: 40 -->
# Cypress执行

![](img/Ch6_图片4.jpg)

<!-- Slide number: 41 -->
# Android App UI自动化测试
Robotium （native/web)
UIAutomator
MonkeyRunner （Android SDK tool）
Appium
Espresso
Selendroid （native）
ATAF
TestComplete

![espresso_lockup1-289x300.png](img/Ch6_图片9.jpg)

![appium 的图像结果](img/Ch6_Picture2.jpg)

![robotium1.png](img/Ch6_图片2.jpg)

![屏幕快照 2017-02-03 下午4.34.00.png](img/Ch6_图片7.jpg)

### Notes:

<!-- Slide number: 42 -->
# 两种基本的自动化测试机制
Appium是基于UIAutomator框架实现的。Appium测试进程与目标应用进程是分开的，所以不能直接访问目标应用元素属性进行操作，只能模拟触发事件对目标应用进行操作

Robotium、Espresso、Seledroid是基于Instrumentation框架的，其测试进程与目标应用是在同一个进程中作为两个不同的线程运行的

![屏幕快照 2017-02-03 下午8.07.18.png](img/Ch6_图片2.jpg)

### Notes:
Appium是基于UIAutomator框架实现的。Appium测试进程与目标应用进程是分开的，所以Appium不能直接访问目标应用的各种element属性进行copy&paste，而只能模拟触发相应的事件对目标应用进行操作。这就好比触摸屏监控驱动和目标应用的关系：驱动监控到用户点击屏幕的事件后，驱动就会去判断点击的位置是否是一个文本框，如果是的话，就去打开系统键盘给用户进行输入。
　　Robotium是基于Instrumentation框架的。Robotium测试进程与目标应用是在同一个进程中作为两个不同的线程运行的。也就是说Robotium测试线程是有办法直接访问目标应用的各种element属性的，可以访问浮层，Intent之类的。所以它根本不需要触发任何事件，直接就可以在内部修改相应的数据

<!-- Slide number: 43 -->
# 几款常见的测试工具比较

![查看源图像](img/Ch6_Picture2.jpg)

### Notes:
Appium是基于UIAutomator框架实现的。Appium测试进程与目标应用进程是分开的，所以Appium不能直接访问目标应用的各种element属性进行copy&paste，而只能模拟触发相应的事件对目标应用进行操作。这就好比触摸屏监控驱动和目标应用的关系：驱动监控到用户点击屏幕的事件后，驱动就会去判断点击的位置是否是一个文本框，如果是的话，就去打开系统键盘给用户进行输入。
　　Robotium是基于Instrumentation框架的。Robotium测试进程与目标应用是在同一个进程中作为两个不同的线程运行的。也就是说Robotium测试线程是有办法直接访问目标应用的各种element属性的，可以访问浮层，Intent之类的。所以它根本不需要触发任何事件，直接就可以在内部修改相应的数据

<!-- Slide number: 44 -->
# Instrumentation框架

![查看源图像](img/Ch6_Picture2.jpg)
以通过从签名来实现让系统认为测试App和被测App是同一个进程

myAppTests.apk通过Instrumentation 技术控制被测myApp.apk

myAppTests.apk文件是由InstrumentationTestRunner 进行控制各种方法运行

<!-- Slide number: 45 -->
# InstrumentationTestRunner
编写 TestCases，对软件包中的类进行单元/功能/性能测试。一般来说，这些都是从下列类继承而来 :
ActivityInstrumentationTestCase2、ActivityUnitTestCase
AndroidTestCase 、ApplicationTestCase
InstrumentationTestCase
ProviderTestCase、ServiceTestCase
SingleLaunchActivityTestCase
 在测试包的清单中设置<instrumentation>元素的android:targetPackage属性，将该属性值设置为AUT的包名
 使用 "adb shell am instrument -w "运行instrumentation ，没有可选参数，以运行所有测试（除了性能测试）
 参数为'-e func true'，运行所有功能测试。这些是源自  InstrumentationTestCase的测试
 参数'-e unit true'运行所有单元测试。这些是不从 I InstrumentationTestCase派生的测试（不是性能测试）
 参数'-e class'设置为运行单个TestCase
AUT：App under test
https://developer.android.com/reference/android/test/InstrumentationTestRunner

<!-- Slide number: 46 -->
# 示例1：Monkeyrunner
基于python脚本实现复杂测试用例的UI测试工具，通过坐标、控件ID来操作应用的UI元素，截取测试执行的UI界面，进行图像比较分析来发现问题
InstrumentationTestRunner 是针对被测app而运行测试脚本的执行器
Test tools：即与Eclipse IDE集成的、构建测试的SDK tools
MonkeyRunner: 提供API开发测试脚本，以便能在Android 代码之外来控制设备
Test package被组织在测试项目中，遵守命名空间
Test case classes

### Notes:

<!-- Slide number: 47 -->
# 示例1：Monkeyrunner - 续
monkeyrunner API 可以跨多个设备或模拟器应用一个或多个测试套件，可以基于API和python开发一整套自动化系统
MonkeyRunner：此class提供了用于将 monkeyrunner 连接到设备或模拟器的方法，也提供了用于为 monkeyrunner 程序创建界面以及显示内置帮助的方法。
MonkeyDevice：代表设备或模拟器，提供了用于安装和卸载软件包、启动 Activity 以及向应用发送键盘或轻触事件的方法、运行测试软件包。
MonkeyImage：提供了用于截屏、将位图转换为各种格式、比较两个 MonkeyImage 对象以及将图片写入文件的方法。

### Notes:

<!-- Slide number: 48 -->
# 示例1：Monkeyrunner - 续

![](img/Ch6_图片5.jpg)

### Notes:

<!-- Slide number: 49 -->
# 示例2： Robotium
https://github.com/RobotiumTech/robotium
能够对各种控件进行操作，模拟各种手势操作、查找和断言机制的API
支持对native和WebView 的操作
能自动的支持多个安卓Activities；
有单独的录制回放工具
可以和Mave、Gradle、Ant等工具进行集成

![http://cdn.guru99.com/images/image019%283%29.png](img/Ch6_图片5.jpg)

### Notes:

<!-- Slide number: 50 -->
# Robotium 脚本示例

![屏幕快照 2017-02-03 下午4.41.21.png](img/Ch6_图片3.jpg)

![robotium1.png](img/Ch6_图片7.jpg)

### Notes:

<!-- Slide number: 51 -->
# UI Automator 测试框架
用于检查布局层次结构的查看器
用于检索状态信息并在目标设备上执行操作的 API
支持跨应用界面测试的 API

<!-- Slide number: 52 -->
# UI Automator Viewer

![屏幕快照 2017-02-03 下午4.39.52.png](img/Ch6_图片3.jpg)

![sayalee_6.png](img/Ch6_图片2.jpg)

### Notes:

<!-- Slide number: 53 -->
# 访问设备状态
UI Automator 测试框架提供了一个 UiDevice 类，用于在运行目标应用的设备上访问和执行操作，包括设备属性（屏幕方向或显示屏尺寸等），还能执行以下操作：
改变设备的旋转
按硬件键，如“音量调高按钮”
按返回、主屏幕或菜单按钮
打开通知栏
截取当前窗口的屏幕截图
https://developer.android.google.cn/reference/androidx/test/uiautomator/UiDevice?hl=zh-cn

<!-- Slide number: 54 -->
# UI Automator
https://developer.android.com/tools/testing-support-library/index.html
Espresso 可以写出类似白盒测试那样的、更美观的自动化测试脚本，可充分利用被测app所实现的程序代码，而且能够实现UI 线程同步，解决了可能存在的并发问题，能够改进测试的可靠性。

View matching（ViewMachers）：为View 构建的、灵活的API，借助onView方法来定位UI layout view，且支持多层次view的定位。
Action APIs （ViewActions）：一系列扩展的、以完成UI交互操作API集，即借助ViewInteraction.perform方法来完成view的操作。
ViewAssertions: 借助ViewInteraction.check方法来判定当前所选定view的状态，以完成测试所需的验证。

### Notes:

<!-- Slide number: 55 -->
# UI Automator API
UiCollection：枚举容器的界面元素，目的是为了计数，或者按可见文本或内容说明属性来定位子元素。
UiObject：表示设备上可见的界面元素。
UiScrollable：支持搜索可滚动界面容器中的项目。
UiSelector：表示对设备上的一个或多个目标界面元素的查询。
Configurator：可设置用于运行 UI Automator 测试的关键参数。

<!-- Slide number: 56 -->
# UI Automator代码示例

![屏幕快照 2017-02-03 下午5.21.25.png](img/Ch6_图片1.jpg)

![屏幕快照 2017-02-03 下午5.22.02.png](img/Ch6_图片2.jpg)

### Notes:

<!-- Slide number: 57 -->

![](img/Ch6_图片2.jpg)
# 6.3 回归测试

### Notes:
十一、功能测试自动化
面向接口的自动化测试
Web客户端的UI自动化测试
基于Cypress的UI自动化测试
Android应用的UI自动化测试
数据驱动/关键字驱动
自动化测试框架

<!-- Slide number: 58 -->
# 为什么需要进行回归测试？

![](img/Ch6_图片5.jpg)
以前都正常的，新的版本反而不正常了
—— 回归缺陷 (Regression bug)
58

<!-- Slide number: 59 -->
# 为什么要有回归测试？

![屏幕快照 2017-04-25 下午9.00.03.png](img/Ch6_图片2.jpg)

### Notes:

<!-- Slide number: 60 -->
# 回归测试
Regression Testing
一旦程序某些区域被修改了，就可能影响原来正常工作的区域，导致受影响的区域出现回归缺陷。
回归缺陷：原来正常工作的功能，没有发生需求变化，而由于受其它改动影响而产生的问题。
回归测试就是为了发现回归缺陷而进行的测试。如果没有回归测试，产品就带着回归缺陷被发布出去了，造成严重后果。

### Notes:

<!-- Slide number: 61 -->
# 如何进行回归测试？

![](img/Ch6_图片2.jpg)
范围？
 策略？
61

<!-- Slide number: 62 -->
# 回归测试策略

![http://www.softservsolutions.com/new/images/qualityassurance.jpg](img/Ch6_Picture2.jpg)
再测试全部用例
基于风险选择测试
基于操作剖面选择测试
再测试修改的部分
……

### Notes:

<!-- Slide number: 63 -->

![](img/Ch6_图片2.jpg)
# 6.4  精准测试

### Notes:
十一、功能测试自动化
面向接口的自动化测试
Web客户端的UI自动化测试
基于Cypress的UI自动化测试
Android应用的UI自动化测试
数据驱动/关键字驱动
自动化测试框架

<!-- Slide number: 64 -->
# 精准测试
测试覆盖率分析
代码和测试用例之间的关系
代码依赖性分析
基于上述工作，可以精准地完成回归测试

![](img/Ch6_图片4.jpg)

<!-- Slide number: 65 -->
# 测试用例与代码映射关系

![](img/Ch6_图片4.jpg)

![](img/Ch6_图片12.jpg)
代码测试用例
测试用例代码

<!-- Slide number: 66 -->
# 代码依赖性分析

![](img/Ch6_图片10.jpg)

<!-- Slide number: 67 -->
# 测试覆盖率分析

![](img/Ch6_图片8.jpg)

<!-- Slide number: 68 -->
# 本讲小结
基于需求、启发式测试策略进行功能测试需求分析
先要明确测试目标，再进行测试范围、测试项和风险等进行分析，采用分解方法，内容涉及功能、场景、数据等
探索式测试四要素、IAPE、生态建设以及SBTM
回归测试策略、精准测试

<!-- Slide number: 69 -->
# 提问与思考
自动化测试中录制脚本轻松搞定，为何没有成为功能测试自动化脚本开发的主流？
采用开源自动化测试框架还是自己开发自动化测试框架好呢？
大家都重视自动化测试，但往往效果不够好，问题在哪里？

### Notes:
重点学习内容，可以通过留实操作业或提问的方式，巩固学习成果

<!-- Slide number: 70 -->
实验3: 针对某web应用系统进行功能测试
实验要求
基于本模块所学的测试方法，进行测试需求分析，按优先级列出主要的测试项以及识别出测试风险
设计20+个相对关键的测试用例，以发现更多的缺陷，并能说明测试用例的设计思路和方法。
基于Selenium＋webdriver 将之前设计的10个测试用例转化为测试脚本，如Java格式的脚本，在JUnit框架上执行和调试这些脚本。

![](img/Ch6_图片2.jpg)
https://www.saucedemo.com/

<!-- Slide number: 71 -->
学习资源推荐
《接口自动化测试项目实战》，清华大学出版社，2021.11
《从零开始学Selenium自动化测试》，机械工业出版社，2020
《前端自动化测试框架——Cypress 从入门到精通》，电子工业出版社，2020.4
《Robot Framework自动化测试精解》 ，人民邮电出版社，2020.4

<!-- Slide number: 72 -->
# 感 谢 聆 听
朱少民 / 同济大学

### Notes:
每课结束时使用“以上是本节课的内容”“这一章讲到这里”