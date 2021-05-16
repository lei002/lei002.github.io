---
abbrlink: 1
---
# 学习方法

看视频的过程中，千万不要只是眼睛在看，脑袋没有在看。看视频的过程中，最好还能够自己去记一些笔记。

自己勤加复习、总结。

编程如果有捷径的话，那么一定就是反复的敲代码、多敲代码。



bug：随手整理bug-list.学习过程中遇到的各种各样的bug，相应的解决方案。

NullPointException-----一个引用或者对象为null，但是从里面取东西。

ClassCastException-----类转换异常.多态

FileNotFoundException----没有找到对应的文件。

debug：

清楚代码的执行逻辑，从程序的执行入口开始一步一步分析。

打断点。

建议大家先要自己去思考，把相关的问题描述清楚。

# EE

JavaEE:Enterprise Edition.企业版，是给企业使用的

JavaSE:Standard Edition.个人版，独立开发者使用的



企业需要哪些？

服务器（服务器硬件（云服务器）、服务器软件----将本地的资源文件发布到网络上面）

域名

网页

用户群、流量----数据库



# HTTP

Hyper Text Transfer Protocol. HTML.同门。

bernese lee为了不同研究人员之间的论文共享问题，发明了HTTP和HTML

HTML是显示文章，HTTP是传输文章。

HTTP协议 **超文本****传输****协议**，主要是用来传输文本、音频、视频、图片等资源信息。

协议就是一个条款，甲方应该尽什么样的义务，有什么权力；乙方应当尽什么样的义务，有什么洋的权利

通讯双方应当遵循的一个准则。发送方应该怎么去发送，按照一定的准则，接收方就可以顺利的接收到；接收方做出响应，响应也应当遵循响应的准则，同样，发送方再接收到响应方发送回来的数据时，也可以正常的解析。

## HTTP工作流程

对于网络有一个认识。

IP：网络上面的机器，如果要能够进行沟通，每一台机器都需要IP地址。ip地址就是你的门牌号。

TCP：传输协议。可靠的传输协议  UDP

### 网络模型

网络其实是一个很复杂、庞大的组合体。为了将各个部分尽可能的简化，对于网络提出一个模型，模型的话将网络分为很多个层次，每个层次只需要关注自己这部分内容即可，然后向外提供给其他层来使用。

HTTP协议位于应用层。



工作流程：

以在浏览器窗口输入http://www.baidu.com为例



1.域名解析（）：最终结果就是将域名转成ip地址。

2.建立一个可靠连接：TCP三次握手。为什么要进行三次握手？网络通讯的不可靠性。

3.发送HTTP请求（HTTP请求和HTTP协议是什么关系呢？**HTTP协议就是用来规范HTTP请求应该怎么发，HTTP响应应该怎么发，应该具有某种规则，这样才可以正常地进行解析**），比如

发送了一个请求，里面包含了很多的学生信息

110405199506103467 张三  25 北京

110405199506103467 李四  25 北京

110405199506103467 王五  25 北京

110405199506103467 李艮隶  25 北京



规则：

身份证号码  姓名  年龄  籍贯 \r\n

4.服务器接收到请求信息，并解析出客户端的真实意图，接下来做出HTTP响应（HTTP协议就是用来规范HTTP响应应该怎么发，不能乱发）

5.客户端拿到HTTP响应，解析，取出里面的html文档页面

6.浏览器对html进行渲染，显示页面。



**进一步完善**：

1.域名解析（）：最终结果就是将域名转成ip地址。

2.建立一个可靠连接：TCP三次握手。为什么要进行三次握手？网络通讯的不可靠性。

3.发送HTTP请求（HTTP请求和HTTP协议是什么关系呢？**HTTP协议就是用来规范HTTP请求应该怎么发，HTTP响应应该怎么发，应该具有某种规则，这样才可以正常地进行解析**）

4.发出的HTTP请求，交给TCP层，TCP将HTTP请求信息给它拆解成为一个一个的片段，同时加上TCP头部

5.TCP将处理后的数据交给IP层，IP层将这些信息加上IP头部

6.IP层将数据交给链路层，经过网卡出去，在网络上一边中转一边传输。

7.到达目标机器之后，通过链路层进去，进而到达IP层，信息会脱去IP头部

8.处理完之后再次交给TCP，会将原先的信息重新拼接组装，脱去TCP头部（目的是什么?为什么要先拆解再组装呢？大片段在网络上不易传输，你邮寄了一个大包裹，快递公司会将你的包裹分为几个小包）

9.服务器接收到请求信息，并解析出客户端的真实意图，接下来做出HTTP响应（HTTP协议就是用来规范HTTP响应应该怎么发，不能乱发）

10.响应信息也会经过TCP层，拆解，加上TCP头部

11.经过IP层，加上IP头部，经过网卡出去

12.客户端主机拿到响应信息之后，再次经过相同的步骤，先脱去IP头部，再重新组装，脱去TCP头部，形成原始的响应信息

6.浏览器对html进行渲染，显示页面。

## HTTP协议

HTTP协议其实就是对于请求和响应应当怎么发的一个具体规范和要求。

请求一般也称之为请求报文

响应一般也称之为响应报文



### 请求报文

格式如下：

请求行:请求方法  请求资源  HTTP协议版本

请求头：若干请求头

空行

请求体:可以有，也可以无



![image-20201125112705705](HTTP&Tomcat.assets/image-20201125112705705.png)



#### 请求行

分为三部分，请求方法、请求资源、版本协议

##### 请求方法

用什么请求方法发送了当前的请求。常用的请求方法有哪些呢？

​					最常用的请求方法其实只有GET、POST。

​					GET和POST有什么样的区别呢？

对于浏览器来说

​					GET请求如果携带请求参数，那么请求参数是附着再地址栏后面的（也就是再请求报文的请求资源后面，以?来进行分隔开，如果有多个请求参数，那么以&进行连接，形式key1=value1&key2=value2）

​					POST请求携带请求参数，请求参数是再请求体（正文）里面的

如何模拟GET、POST请求

GET：1.form表单设置method=get 

​		    2.a标签的href，如果点击，那么默认情况下浏览器会帮我们发送GET请求

![image-20201125114105177](HTTP&Tomcat.assets/image-20201125114105177.png)

GET请求报文：

GET http://www.cskaoyan.com/?username=zsong&password=asdsad HTTP/1.1
Host: www.cskaoyan.com
Connection: keep-alive
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.66 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Referer: http://localhost:63342/
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: cZBD_2132_saltkey=O3HTwAwH; cZBD_2132_lastvisit=1605840864; Hm_lvt_2504f1c08c3a31e74bbfb16ecaff376b=1605844466; cZBD_2132_sid=gb92n2; cZBD_2132_lastact=1606275643%09home.php%09misc; cZBD_2132_sendmail=1; Hm_lvt_2504f1c08c3a31e74bbfb16ecaff376b=1605844466,1606275644; Hm_lpvt_2504f1c08c3a31e74bbfb16ecaff376b=1606275644

POST请求报文：

POST http://www.cskaoyan.com/ HTTP/1.1
Host: www.cskaoyan.com
Connection: keep-alive
Content-Length: 29
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Origin: http://localhost:63342
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.66 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Referer: http://localhost:63342/
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: cZBD_2132_sid=qlfVwV; cZBD_2132_lastact=1606275715%09home.php%09misc; Hm_lvt_2504f1c08c3a31e74bbfb16ecaff376b=1605844466,1606275716; Hm_lpvt_2504f1c08c3a31e74bbfb16ecaff376b=1606275716

username=zsong&password=asdas



GET和POST请求方式的区别就在这吗？

注意，GET和POST请求方式的区别不是因为这个，这个仅仅是浏览器的行为。

**真正的区别是在于语义的区别**。

制定这两个请求方法的时候，就规定

GET的语义就是用来获取资源，比如说你看到一个商品想分享给别人

POST的语义就是用来提交数据，注册、登录



##### 请求资源

其实就是告诉给服务器，我需要哪个资源



##### 版本协议

昨天：HTTP/0.9  HTTP/1.0

今天：HTTP/1.1(目前还是以1.1为主要的)

明天:   HTTP/2.0  HTTP/3.0

1.0和1.1的HTTP协议最大的区别在于什么地方呢？

1.1默认支持长连接。含义默认再一个TCP连接内可以发送多个HTTP请求，而无需中断当前TCP连接

但是1.0不支持，发送完一个HTTP请求，必须要断开当前TCP连接，下一次如果需要重新发送HTTP请求，需要重新进行TCP连接。

#### 请求头

客户端携带的传递给服务器的一些额外的信息。

Accept 表示的是客户端可以接收的资源类型，一般使用MIME类型来表示？

MIME其实就是将互联网上面的资源进行一个分类，一个大分类/一个小分类

比如对于文本 text/html  text/txt等

比如图片  image/jpeg  image/png

比如音频 audio/mp3

比如视频  video/mp4 	video/mkv



Accept:浏览器可接受的    MIME类型 */*   (大类型)/(小类型)
Accept-Charset: 浏览器通过这个头告诉服务器，它支持哪种字符集
Accept-Encoding:浏览器能够进行解码的数据编码方式，比如gzip 
Accept-Language: 浏览器所希望的语言种类，当服务器能够提供一种以上的语言版本时要用到。 可以在浏览器中进行设置。
Host:初始URL中的主机和端口 
Referer:包含一个URL，用户从该URL代表的页面出发访问当前请求的页面 （防盗链）

​	比如从1.html跳转至2.html和直接访问2.html，通过请求报文，能不能看出来？

从1.html通过form表单跳转至2.html

POST http://localhost:63342/http/demo1/2.html HTTP/1.1
Host: localhost:63342
Connection: keep-alive
Content-Length: 30
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Origin: http://localhost:63342
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.66 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
**Referer**: http://localhost:63342/http/demo1/1.html?_ijt=h6e4ktek2k4qohnho1u382koto
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Cookie: Idea-31d5f4eb=af750744-2158-4f3c-bba9-e7eae63a38fd

username=zsong&password=asdsad



直接访问2.html

GET http://localhost:63342/http/demo1/2.html HTTP/1.1
Host: localhost:63342
Connection: keep-alive
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.66 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Cookie: Idea-31d5f4eb=af750744-2158-4f3c-bba9-e7eae63a38fd



Content-Type:内容类型



If-Modified-Since: Wed, 02 Feb 2011 12:04:56 GMT 服务器利用这个头与服务器的文件进行比对，如果一致，则告诉浏览器从缓存中直接读取文件。自从某个时间点以来，资源有没有发生修改，如果没有直接从缓存中取，如果发生了修改，则返回最新内容。
User-Agent:浏览器类型.
Content-Length:表示请求消息正文的长度 。一般是表示请求体的长度。
Connection:表示是否需要持久连接。如果服务器看到这里的值为“Keep -Alive”，或者看到请求使用的是HTTP 1.1（HTTP 1.1默认进行持久连接 
Cookie:这是最重要的请求头信息之一 。里面可以存储用户相关的数据信息。
Date：Date: Mon, 22 Aug 2011 01:55:39 GMT请求时间GMT



### 响应报文

​	服务器发送给客户端的响应信息。

#### 响应行

​	协议版本  状态码  原因短语

##### 状态码

​	表示这个请求对应的响应状态是什么样的，是成功还是失败，还是其他什么原因

​	200   OK

​	301、302、307 重定向

​	以访问http://www.bing.com为例

​	一定会搭配着一个Location响应头，需要知道往哪个地址去跳转

​	404 没有找到

​	500 服务器内部错误

#### 响应头

Location: http://www.cskaoyan.com/指示新的资源的位置，一般和302、307状态码搭配使用 
Server: apache tomcat 指示服务器的类型
Content-Encoding: gzip 服务器发送的数据采用的编码类型
Content-Length: 80 告诉浏览器正文的长度
Content-Language: zh-cn服务发送的文本的语言
Content-Type: text/html;  服务器发送的内容的MIME类型
Last-Modified: Tue, 11 Jul 2000 18:23:51 GMT文件的最后修改时间
Refresh: 1;url=http://www.cskaoyan.com指示客户端刷新频率。单位是秒

Content-Disposition: attachment; filename=aaa.zip指示客户端保存文件
Set-Cookie: SS=Q0=5Lb_nQ; path=/search服务器端发送的Cookie
Expires: 0
Cache-Control: no-cache (1.1)  
Connection: close/Keep-Alive   
Date: Tue, 11 Jul 2000 18:23:51 GMT

空行

响应体



## HTTPS

HTTPS并不是一个全新的协议，而是再HTTP的基础上做了一层包装 Secure

HTTPS = HTTP + 加密  + 证书 + 完整性验证

HTTP存在的一些弊端：

1.传输过程完全是明文传输

​	加密。

​	加密算法：

​		对称加密：加密和解密使用同一把钥匙(速度很快)

​		非对称加密：公钥加密之后，只能使用私钥进行解密(速度很慢)



2.通讯的另一方没有验证身份，有可能是伪装者

​		证书：是一个权威机构版本的一个凭证。

3.如果请求报文或者响应报文再传输途中遭遇了更改，无从发现



http部分的要求：

1.HTTP协议的理解，请求报文、响应报文的格式

2.学会使用fiddler、chrome去抓包

检验学习成果：

浏览器地址栏输入一个网址，经历了哪些过程，呈现出最终的页面 http://www.bing.com



# Tomcat

## Web开发概述

web其实就是网，网页、网站。客户端和服务器之间的通讯。通讯使用的就是HTTP协议。

架构可以大体上分为两大类：

B/S:browser/Server.浏览器/服务器

C/S:client/Server. 客户端/服务器



服务器就是将本地的资源发布到网络上面，供网络上的其他用户来访问。

## 手动编写Server

![image-20201125162015515](HTTP&Tomcat.assets/image-20201125162015515.png)

```java
import java.io.*;
import java.net.ServerSocket;
import java.net.Socket;

/**
 * 实现一个简易版的服务器
 * 功能：接收请求，做出响应
 * 监听某一端口号
 * ServerSocket Socket
 */
public class Server {

    public static void main(String[] args) {
        ServerSocket serverSocket = null;
        try {
            serverSocket = new ServerSocket(8088);
            while (true){
                //这一步默认情况下是阻塞的，没有请求到来会一直阻塞再这一步
                Socket socket = serverSocket.accept();
                //下面我们需要使用多线程，原因在于如果处理socket的步骤含有阻塞步骤
                //那么主程序就无法持续监听可能连接来的客户端了
                new Thread(new Runnable() {
                    @Override
                    public void run() {
                        try {
                            //客户端发送过来的信息，都已经帮我们封装好了，再inputStream中
                            //比如客户端就是浏览器，会发送HTTP请求报文过来，请求报文就再inputStream里面
                            Request request = new Request(socket);
                            //System.out.println("当前请求方法为：" + request.getMethod());
                            //System.out.println("当前请求资源为：" + request.getRequestURI());
                            //System.out.println("当前请求版本协议为：" + request.getProtocol());
                            //如果我们希望向客户端发出响应，只需要往outputStream里面写入数据即可
                            //请求的资源文件 如果存在的话，则将文件流写出去，如果不存在返回404响应报文
                            String requestURI = request.getRequestURI();
                            OutputStream outputStream = socket.getOutputStream();
                            Response response = new Response(outputStream, requestURI);
                            response.responde();
                        } catch (IOException e) {
                            e.printStackTrace();
                        }
                    }
                }).start();
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
        //接收到的每一个客户端信息
    }
}
```

```java
import java.io.ByteArrayOutputStream;
import java.io.IOException;
import java.io.InputStream;
import java.net.Socket;

public class Request {

    private Socket socket;

    /**
     * 代表解析之后的请求报文
     */
    private String reqeustText;
    /**
     * 请求方法
     */
    private String method;
    /**
     * 请求资源
     */
    private String requestURI;
    /**
     * 版本协议
     */
    private String protocol;

    public String getMethod() {
        return method;
    }

    public String getRequestURI() {
        return requestURI;
    }

    public String getProtocol() {
        return protocol;
    }

    public Request(Socket socket) {
        this.socket = socket;
        try {
            parseRequest();
            if(reqeustText != null && !reqeustText.equals("")){
                //如果不为空，接下来将其解析出来
                parseRequestLine();
                parseRequestHeader();
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    /**
     * 将请求报文里面的请求头解析出来
     * 可以将解析出来的请求头键值对放入map中，然后向外暴露一个方法
     * 比如request.getHeader(name) 取出对应的value值
     */
    private void parseRequestHeader() {

    }

    /**
     * 解析请求报文，返回一个字符串
     * 每次如果我都希望从请求报文中取出请求资源，非常不方便，将整个请求报文拆解成一个一个部分
     * 利用\r\n可以将请求行拆解出来
     * 其次利用 \r\n 和 \r\n\r\n中间的是请求头
     */
    private void parseRequest() throws IOException {
        InputStream inputStream = socket.getInputStream();
        //FileOutputStream fileOutputStream = new FileOutputStream();
        byte[] bytes = new byte[1024];
        int length = inputStream.read(bytes);
        this.reqeustText = new String(bytes, 0, length);
        System.out.print(reqeustText);
    }

    /**
     * 解析请求行
     */
    private void parseRequestLine(){
        int index = reqeustText.indexOf("\r\n");
        String requestLine = reqeustText.substring(0, index);
        //System.out.print(requestLine);
        String[] strings = requestLine.split(" ");
        this.method = strings[0];
        this.requestURI = strings[1].substring(1);
        this.protocol = strings[2];
    }
}
```

```java
import java.io.*;

public class Response {

    private OutputStream outputStream;

    private String requestURI;

    public Response(OutputStream outputStream, String requestURI) {
        this.outputStream = outputStream;
        this.requestURI = requestURI;
    }

    /**
     * 发送响应报文
     */
    public void responde() {
        File file = new File(requestURI);
        StringBuffer stringBuffer = new StringBuffer();
        if(file.exists() && !file.isDirectory()){
            //file是一个文件
            try {
                FileInputStream inputStream = new FileInputStream(file);
                byte[] bytes = new byte[1024];
                int length = 0;
                stringBuffer.append("HTTP/1.1 200 OK\r\n");
                stringBuffer.append("Content-Type: text/html\r\n");
                stringBuffer.append("\r\n");
                //将响应行和响应头返回给客户端
                outputStream.write(stringBuffer.toString().getBytes("utf-8"));
                while ((length = inputStream.read(bytes)) != -1){
                    outputStream.write(bytes, 0, length);
                }
            } catch (FileNotFoundException e) {
                e.printStackTrace();
            } catch (IOException e) {
                e.printStackTrace();
            }
            return;
        }
        //不是文件  404
        stringBuffer.append("HTTP/1.1 404 Not Found\r\n");
        stringBuffer.append("Content-Type: text/html\r\n");
        stringBuffer.append("\r\n");
        stringBuffer.append("<h1 style='color:red'>File Not Found</h1>");
        try {
            outputStream.write(stringBuffer.toString().getBytes("utf-8"));
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

## JavaEE规范

服务器，很多厂家，都可以设计服务器产品，供企业来选择使用。

比如服务器需要能够解析HTTP请求报文，拿到请求资源，然后才能针对性的做出响应

一家公司服务器产品，获取请求资源的API叫做request.getRequestURI

另外一家可能叫做reqeust.getRequestResource



切换服务器，对于企业来说，他的成本非常大，所有的代码全部都要更换一遍。制定一个标准， 做一个统一。

比如sun制定了一个标准，关于请求报文的话，提供了一个接口叫做ServletRequest，里面提供了很多的API，其中有一个叫做getRequestURI,接下来服务器生产厂商需要做的事情就是实现这个接口。



## Tomcat目录结构

logs目录非常有用，如果启动的时候发生错误，logs目录里面的文件肯定会记录下来错误日志信息。

bin目录叫做二进制文件存放目录，启停tomcat的文件再当前目录下

conf配置文件目录，如果需要配置tomcat，需要再该目录下

webapps，如果希望部署静态资源，需要再该目录下

## Tomcat启停

启动

​	1.直接双击startup.bat文件

​		直接访问http://localhost:8080即可

​    2.通过cmd进入到tomcat的安装目录/bin目录下，执行startup即可

常见报错信息：

**如果没有正确的配置JAVA_HOME，那么双击startup.bat会一闪而过，一般情况下是JAVA_HOME环境变量失效**



停止

​		1.双击shutdown.bat

​		2.通过cmd进入到tomcat的安装目录/bin目录下，执行shutdown即可

​		3.直接再tomcat的启动窗口上面执行ctrl + c



## Tomcat部署资源

如果希望将一个资源文件部署再tomcat中，那么一定要再tomcat里面新建一个应用，将资源文件放在应用里面才可以。tomcat里面最小的单元是应用。

新建一个应用最简单的一个方式，其实就是再tomcat的webapps目录下新建一个目录，那么这个目录就是一个应用，当前目录的名称就是应用的名称。

tomcat部署资源有两种方式

### 直接部署

#### 开放式目录

直接再tomcat的webapps目录下新建一个目录，然后将资源文件放置再该目录中即可。

如何访问到部署的资源文件呢？

当你输入http://localhost:8080,这个时候tomcat会到webapps目录，接下来如何希望访问某个资源，**只需要指明它和webapps的相对路径关系即可**。

#### 打成war包

war包就是类似于压缩包，直接放置再tomcat的webapps目录下，tomcat启动会自动将其解压缩成为一个开放式目录，目录的名称就是你的war包的名称。

### 虚拟映射

虚拟映射的概念是说如果不希望再webapps目录下部署，但是也希望资源能够被访问到，那么tomcat给我们提供了一种方式，虚拟映射到某个位置，叫做虚拟映射。

#### conf/Catalina/localhost目录下新增 应用名.xml文件（非常重要）

比如新增app2.xml文件

<?xml version="1.0" encoding="UTF-8"?>
<Context docBase="D:\app" />

当访问http://localhost:8080/app2时，相当于一定定位到docBase指向的路径了。那么需要访问某个资源，只需要指出它和docBase的相对路径关系即可。



#### conf/server.xml文件增加配置项

需要再**Host节点下面新增一个Context节点**

<Context docBase="D:\app" path="/app3" />

注意事项：Context注意大小写；



需要特别注意的时不管哪种虚拟映射，还是可以通过部署开放式目录或者war包，都可以。



## Tomcat的请求处理流程

Tomcat是组件化的应用，可以对server.xml文件进行相应的修改，那么tomcat再启动的时候就会读取server.xml文件里面的配置项，利用这些配置项，生成对应的组件对象。

组件对象类似于**俄罗斯套娃**，大娃娃套着小娃娃。

http://localhost:8080/app/1.txt

1.请求到达服务器之后，被监听8080端口号的HTTP/1.1的Connector接收到，它的主要职责就是将请求报文解析成为一个Request对象，同时还会给我们提供一个Response对象

2.它会将这两个对象交给Engine来处理，Engine的主要职责就是来选择一个合适的Host来处理接下来的请求（**行政区域**）,选择一个Host将这两个对象进行进一步的下发，如果没有找到合适的Host，那么请求依然会交给localhost来处理

3.Host的主要职责依然是选择一个合适的Context来处理，（Context来源于哪？webapps下面的每一个目录，conf/server.xml里面的Context节点、conf/Catalina/localhost下面  xml文件，这些再tomcat启动的时候都会被扫描，然后形成一个一个Context对象）

4.Host选择合适的Context之后，将这两个对象交给对应的Context对象来处理，寻找当前应用下有没有一个1.txt文件。如果找到，则将1.txt的文件流写入到Response中，如果没有找到，则写入一个404信息到response中

5.这两个对象再次从Context、Host、Engine、Connector返回，Connector会读取Response里面的内容，按照HTTP协议对于响应报文的要求，组织形成一个HTTP响应报文，发送出去。



## Tomcat配置

### 配置默认端口号

我们经常访问网站会看到并没没有携带端口号，比如http://www.cskaoyan.com

http://localhost:8080

对于HTTP协议来说，有一个默认端口号80

### 配置默认访问应用

对于绝大多数的应用访问的话都是/应用名来访问，但是有一个特例，ROOT应用，如果希望访问ROOT应用里面的资源，不需要写应用名，直接省略即可。



### 配置默认访问资源

比如访问http://localhost也可以正常访问到页面，那么它访问的是谁呢？首先访问的肯定是ROOT应用里面的，那么该应用里面的哪个资源呢？如果没有指明访问的资源，那么其实访问的是系统配置的默认访问资源。

再tomcat的conf/web.xml文件中有如下配置

```xml
   <welcome-file-list>
        <welcome-file>index.html</welcome-file>
        <welcome-file>index.htm</welcome-file>
        <welcome-file>index.jsp</welcome-file>
    </welcome-file-list>
```

表示的是如果没有指明具体的访问资源，那么tomcat会从里面配置的文件去查找，找到则结束，找不到则显示404.

比如访问http://localhost,首先肯定访问的是ROOT应用，接下来，会再ROOT应用里面寻找index.html  index.htm  index.jsp依次去查找，如果找到，则结束，不会再继续，如果没有找到，继续往下找，直至找到最后。



提问：如果希望直接访问localhost来访问到你的资源文件，应该怎么做。

