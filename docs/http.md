
# HTTP

> 内容来源于《图解http》

***

### 第一部分 Web及网络基础

3 项 `WWW（简称Web）` 构建技术，分别是：把 SGML（Standard Generalized Markup Language，标准通用标记语言）作为页面的文本标记语言的 HTML（HyperText Markup Language，超文本标记语言）；作为文档传递协议的 HTTP ；指定文档所在地址的 URL（Uniform Resource Locator，统一资源定位符）。 

不同的硬件、操作系统之间的通信，都需要一种规则。这种规则称为**协议（protocol）**。`TCP/IP` 是互联网相关的各类协议族的总称。

#### TCP/IP的分层

四层：应用层、传输层、网络层、和数据链路层。

> 分层的一些好处：1.分层即把整体部分化，当有某个地方出现问题时不必改一个大整体，可以只改出现问题的一小部分。2.简化设计。

**应用层**

应用层决定了向用户提供应用服务时通信的活动。

TCP/IP 协议族内预存了各类通用的应用服务。比如，FTP（File Transfer Protocol，文件传输协议）和 DNS（Domain Name System，域名系统）服务就是其中两类。
 
HTTP 协议也处于该层。
 
**传输层** 
 
传输层对上层应用层，提供处于网络连接中的两台计算机之间的数据传输。 

在传输层有两个性质不同的协议：TCP（Transmission Control Protocol，传输控制协议）和 UDP（User Data Protocol，用户数据报协议）。 
 
**网络层（又名网络互连层）**

网络层用来处理在网络上流动的数据包。数据包是网络传输的最小数据单位。该层规定了通过怎样的路径 （所谓的传输路线）到达对方计算机，并把数据包传送给对方。 

与对方计算机之间通过多台计算机或网络设备进行传输时，网络层所起的作用就是在众多的选项内选择一 条传输路线。 

**链路层（又名数据链路层，网络接口层）**

用来处理连接网络的硬件部分。包括控制操作系统、硬件的设备驱动、NIC（Network Interface Card，网络适配器，即网卡），及光纤等物理可见部分（还包括连接器等一切传输媒介）。硬件上的范 畴均在链路层的作用范围之内。 


<!-- 这里缺一个TCP/IP通信传输流（封装）的流程图 -->
发送端在层与层之间传输数据时，每经过一层时必定会被打上一个该层所属的首部信息。反之，接收端在 层与层传输数据时，每经过一层时会把对应的首部消去。 这种把数据信息包装起来的做法称为封装（encapsulate）。

#### 与http关系密切的协议：IP、TCP、DNS

##### 1.负责传输的 IP

**IP（Internet Protocol）** 网际协议,位于网络层，也即TCP/IP 协议族中的 IP。作用是把各种数据包传送给对方。

> tips：此``IP``是一种协议的名称，需要与``IP地址``区别开。

IP传送条件：IP 地址（指明了节点被分配到的地址），MAC 地址（指网卡所属的固定地址）。



##### 2.负责保障的 TCP

**TCP** 位于传输层，提供**可靠**的**字节流服务**。即TCP 协议为了更容易传送大数据才把数据分割，而且 TCP 协议能够确认数据最终是否送达到 对方。 

**三次握手**

用 TCP 协议把数据包送出去后，TCP 不会对传送后的情况置之不理，它一定会向对方确认是否成功送达。 握手过程中使用了 TCP 的标志（ﬂag） —— SYN（synchronize） 和 ACK（acknowledgement）。 

发送端首先发送一个带 SYN 标志的数据包给对方。``（一次）`` 接收端收到后，回传一个带有 SYN/ACK 标志的数据包以示传达确认信息。``(两次)`` 最后，发送端再回传一个带 ACK 标志的数据包，``（三次）`` 代表“握手”结束。


##### 3.负责域名解析的 DNS

DNS（Domain Name System），提供域名到 IP 地址之间的解析服务。位于应用层。

DNS 协议提供通过域名查找 IP 地址，或逆向从 IP 地址反查 域名的服务。

#### URI和URL

URL（Uniform Resource Locator，统一资源**定位符**）

URI（Uniform Resource Identiﬁer，统一资源**标识符**）

Uniform 规定统一的格式可方便处理多种不同类型的资源，而不用根据上下文环境来识别资源指定的访问方式。另 外，加入新增的协议方案（如 http: 或 ftp:）也更容易。 

Resource 资源的定义是“可标识的任何东西”。除了文档文件、图像或服务（例如当天的天气预报）等能够区别于其 他类型的，全都可作为资源。另外，资源不仅可以是单一的，也可以是多数的集合体。 

Identiﬁer 表示可标识的对象。也称为标识符。综上所述，URI 就是由某个协议方案表示的资源的定位标识符。协议方案是指访问资源所使用的协议类型名称。 

URL 是 URI 的子集。 


***

### 第二部分 http协议

#### 一 用于客户端和服务器之间的通信。 

#### 二 通过请求和响应的交换达成通信（报文）。

#### 三 不保存状态的协议。

#### 四 请求 ``URI定位的`` 资源。

#### 五 告知服务器意图的 **HTTP 方法**。

**HTTP方法：**
1. GET ：获取资源 
GET 方法用来请求访问已被 URI 识别的资源。指定的资源经服务器端解析后返回响应内容。


2. POST：传输实体主体
POST 方法用来传输实体的主体。与GET的差别在于POST主要目的不是**获取**响应的主体内容。


3. PUT：传输文件 
PUT 方法用来传输文件。就像 FTP 协议的文件上传一样，要求在请求报文的主体中包含文件内容，然后 保存到请求 URI 指定的位置。 


4. HEAD：获得报文首部
HEAD 方法和 GET 方法一样，只是不返回报文主体部分。用于确认 URI 的有效性及资源更新的日期时 间等。


5. DELETE：删除文件 
DELETE 方法用来删除文件，是与 PUT 相反的方法。DELETE 方法按请求 URI 删除指定的资源。


6. OPTIONS：询问支持的方法 
OPTIONS 方法用来查询针对请求 URI 指定的资源支持的方法。


7. TRACE：追踪路径
TRACE 方法是让 Web 服务器端将之前的请求通信环回给客户端的方法。 


8. CONNECT：要求用隧道协议连接代理 
CONNECT 方法要求在与代理服务器通信时建立隧道，实现用隧道协议进行 TCP 通信。主要使用 SSL（Secure Sockets Layer，安全套接层）和 TLS（Transport Layer Security，传输层安全）协议 把通信内容加 密后经网络隧道传输。 

#### 六 持久连接节省通信量（持久连接、管线化）

#### 七 使用 Cookie 的状态管理

Cookie 技术通过在请求和响应报文中写入 Cookie 信息来控制客户端的状态。

``` 
1. 请求报文（没有 Cookie 信息的状态）-> 
2. 响应报文（服务器端生成 Cookie 信息）-> 
3. 请求报文（自动发送保存着的 Cookie 信息）
```

### 第三部分 http报文内的http信息

#### http报文

用于 HTTP 协议交互的信息被称为 HTTP 报文。请求端（客户端）的 HTTP 报文叫做请求报文，响应端 （服务器端）的叫做响应报文。HTTP 报文本身是由多行（用 CR+LF 作换行符）数据构成的字符串文本。 HTTP 报文大致可分为报文首部和报文主体两块。通常，并不一定要有报文主体。

报文（message） 
是 HTTP 通信中的基本单位，由 8 位组字节流（octet sequence，其中 octet 为 8 个比 特）组成，通过 HTTP 通信传输。 

实体（entity） 
作为请求或响应的有效载荷数据（补充项）被传输，其内容由实体首部和实体主体组成。 

#### 其他

* 请求报文及响应报文的结构

* 编码提升传输速率 

* 发送多种数据的多部分对象集合

* 获取部分内容的范围请求

* 内容协商返回最合适的内容 


### 返回结果的HTTP状态码

HTTP 状态码负责表示客户端 HTTP 请求的返回结果、标记服务器端的处理是否正常、通知出现的错误等工作。比如404。

状态码的职责是当客户端向服务器端发送请求时，描述返回的请求结果。借助状态码，用户可以知道服务器端是正常处理了请求，还是出现了错误。

状态码类别：
|    | 类别 | 原因短语 |
|:--:| :--: | :--:    |
|1XX |Informational（信息性状态码） |接收的请求正在处理|
|2XX |Success（成功状态码） |请求正常处理完毕 |
|3XX |Redirection（重定向状态码） |需要进行附加操作以完成请求 |
|4XX |Client Error（客户端错误状态码） |服务器无法处理请求 |
|5XX |Server Error（服务器错误状态码） |服务器处理请求出错 |


#### 2XX 成功 

2XX 的响应结果表明请求被正常处理了。

* **200 OK**：表示从客户端发来的请求在服务器端被正常处理了。 

* **204 No Content**：请求已成功处理，但在返回的响应报文中不含实体的主体部分。另外，也不允许返回任何实体的主体。

* **206 Partial Content**：表示客户端进行了范围请求，而服务器成功执行了这部分的 GET 请求。

#### 3XX 重定向 

3XX 响应结果表明浏览器需要执行某些特殊的处理以正确处理请求。 

* **301 Moved Permanently**：永久性重定向，表示请求的资源已被分配了新的 URI，以后应使用资源现在所指的 URI。

* **302 Found**：临时性重定向，表示请求的资源已被分配了新的 URI，希望用户（本次）能使用新的 URI 访问。 

* **303 See Other**：表示由于请求对应的资源存在着另一个 URI，应使用 GET 方法定向获取请求的资源。 

* **304 Not Modiﬁed**：表示客户端发送附带条件的请求 2 时，服务器端允许请求访问资源，但未满足条件的情况。

* **307 Temporary Redirect**：临时重定向。该状态码与 302 Found 有着相同的含义。尽管 302 标准禁止 POST 变换成 GET，但实际使用时大家并不遵守。
307 会遵照浏览器标准，不会从 POST 变成 GET。但是，对于处理响应时的行为，每种浏览器有可能出现不同的情况。

#### 4XX 客户端错误 

4XX 的响应结果表明客户端是发生错误的原因所在。 

* **400 Bad Request**：表示请求报文中存在语法错误。另外，浏览器会像 200 OK 一样对待该状态码。 

* **401 Unauthorized**：表示发送的请求需要有通过 HTTP 认证（BASIC 认证、DIGEST 认证）的认证信息。另外若之前已进行过 1 次请求，则表示用户认证失败。 

* **403 Forbidden**：表明对请求资源的访问被服务器拒绝了。服务器端没有必要给出拒绝的详细理由，但如果想作说明的话，可以在实体的主体部分对原因进行描述，这样就能让用户看到了。 

* **404 Not Found**：表明服务器上无法找到请求的资源。除此之外，也可以在服务器端拒绝请求且不想说明理由时使用。

#### 5XX 服务器错误 

5XX 的响应结果表明服务器本身发生错误。 

* **500 Internal Server Error**：表明服务器端在执行请求时发生了错误。也有可能是 Web 应用存在的 bug 或某些临时的故障。

* **503 Service Unavailable**：表明服务器暂时处于超负载或正在进行停机维护，现在无法处理请求。

### 第五部分 