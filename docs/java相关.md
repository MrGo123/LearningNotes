# Java

### JSP

#### JSP简介
JSP全称Java Server Pages，是一种动态网页开发技术。它使用JSP标签在HTML网页中插入Java代码。标签通常以<%开头以%>结束。
JSP是一种Java servlet，主要用于实现Java web应用程序的用户界面部分。网页开发者们通过结合HTML代码、XHTML代码、XML元素以及嵌入JSP操作和命令来编写JSP。
JSP通过网页表单获取用户输入数据、访问数据库及其他数据源，然后动态地创建网页。
JSP标签有多种功能，比如访问数据库、记录用户选择信息、访问JavaBeans组件等，还可以在不同的网页中传递控制信息和共享信息。

#### JSP处理
以下步骤表明了Web服务器是如何使用JSP来创建网页的：

就像其他普通的网页一样，您的浏览器发送一个HTTP请求给服务器。
Web服务器识别出这是一个对JSP网页的请求，并且将该请求传递给JSP引擎。通过使用URL或者.jsp文件来完成。
JSP引擎从磁盘中载入JSP文件，然后将它们转化为servlet。这种转化只是简单地将所有模板文本改用println()语句，并且将所有的JSP元素转化成Java代码。
JSP引擎将servlet编译成可执行类，并且将原始请求传递给servlet引擎。
Web服务器的某组件将会调用servlet引擎，然后载入并执行servlet类。在执行过程中，servlet产生HTML格式的输出并将其内嵌于HTTP response中上交给Web服务器。
Web服务器以静态HTML网页的形式将HTTP response返回到您的浏览器中。
最终，Web浏览器处理HTTP response中动态产生的HTML网页，就好像在处理静态网页一样。

#### JSP示例

```jsp
<!--
  <%--这是JSP注释--%>
 -->
<html>
<head>
<title>Hello World</title>
</head>
<body>
Hello World!<br/>
<%
out.println("Your IP address is " + request.getRemoteAddr());
%>
</body>
</html>
```


### 单元测试Junit

**黑盒白盒**

“盒”：介于输入与输出之间。运行时“盒”可视为白盒，不可视为黑盒。（即看不看得见流程）。

**测试（建议）**

1. 定义测试类
* 包名定义为：XXX.XXX.test   eg：com.zy68.test
* 类名为XXXTest    eg：CalculatorTest

2. 定义测试方法
* 方法命名：testXXX    eg：testAdd()
* 返回值：void
* 参数列表：空参

3. 给方法加注解 \@Test
4. 导入Junit依赖环境

5. 处理结果：可以用断言

```java
Assert.assertEquals(期望的结果,将要判断的结果);
Assert.assertEquals(3,testAdd(1+2));
/*断言正确：无返回结果；
*/
```
6. 补充的注解

\@Before 
在所有的方法实现前都先实现有\@Before注解修饰的方法

\@After
（与\@before对应）在所有的方法都实现后才实现\@After注解修饰的方法。

### 反射

框架设计的灵魂（即主要用于设计框架）

反射：将类的各个组成部分封装为其他对象，即反射机制。

好处：
* 可在程序运行中操作对象，如在编码时：System.out.…… 每一个点之后显示的就是对象，即整个IDE在运行中，可以操作对象来使用
* 可以解耦，提高程序可扩展性。
