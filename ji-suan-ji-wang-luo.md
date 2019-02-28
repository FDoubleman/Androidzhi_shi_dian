### 网络基础

#### 一、计算机网络体系结构

定义：计算机网络的各层 + 其协议的集合

* 计算机网络体系结构分为3种:OSI 体系结构、**TCP/IP 体系结构 、五层体系结构**

![](/assets/944365-8f04f1321143fd6a.png)

![](/assets/12.png)

#### 二、TCP协议

> * `Transmission Control Protocol`，即 传输控制协议  。属于传输层协议
> * 基于TCP的应用层协议有HTTP、SMTP、FTP、Telnet、POP3

**特点：面向连接、面向字节流、全双工通信、可靠**

![](/assets/tcp12.png)

**建立链接过程：**

* 三次握手

![](/assets/woshou1.png)![](/assets/woshou2.png)

#### 三、UDP协议

> * `User Datagram Protocol`，即 用户数据报协议 。属于传输层协议
>
> * 基于UDP的应用层协议有 TFTP、SNMP、DNS

**特点：无连接的、不可靠的、面向报文、无拥塞控制**

![](/assets/udp.png)

**TCP 和UDP的区别：**

![](/assets/tcp.png)

#### 四、HTTP协议

4.1、**HTTP请求报文结构：**

![](/assets/http1.png)

**HTTP请求方式 GET 和 POST区别：**

![](/assets/2.png)

通用请求头部（一）：

![](/assets/3.png)

常用请求头部（二）：

![](/assets/4.png)**4.2、HTTP响应报文**

![](/assets/5.png)

**通用相应Header:**

* 同请求Header

**常见响应Header**

![](/assets/6.png)

**4.3、HTTP1.1 与 HTTP1.0 的区别**

* 引入持久连接，既在同一个TCP的连接中可传送多个HTTP请求&响应
* 多个请求&响应可以同时进行、可重叠
* 引入更多的请求头 & 响应头

> 如 与身份认证、状态管理 &`Cache`缓存等机制相关的、`HTTP1.0`无`host`字段

**4.4、HTTP处理长连接的方式**

![](/assets/8.jpg)

#### 五、Socket

套接字，**是应用层 与`TCP/IP`协议族通信的中间软件抽象层，表现为一个封装了 TCP / IP协议族 的编程接口（API）**

#### 六、其他

##### 6.1、在浏览器中输入`url`地址 -&gt;&gt; 显示主页的过程

![](/assets/9.png)

**6.2、Cookie 与 Session**

简介：![](/assets/11.png)

区别：![](/assets/tiajfaf.png)

