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
```JSP
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