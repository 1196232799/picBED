# urllib.request.urlopen()函数

## 一.  简介

urllib.request.urlopen()函数用于实现对目标url的访问。

 

函数原型如下：urllib.request.urlopen(url, data=None, [timeout, ]*, cafile=None, capath=None, cadefault=False, context=None)　

url:  需要打开的网址

data：Post提交的数据

timeout：设置网站的访问超时时间

 

直接用urllib.request模块的urlopen（）获取页面，page的数据格式为bytes类型，需要decode（）解码，转换成str类型。

 

## 二.  函数参数介绍


1. url 参数：目标资源在网路中的位置。可以是一个表示URL的字符串（如：http://www.pythontab.com/）；也可以是一个urllib.request对象，详细介绍请跳转

2. data参数：data用来指明发往服务器请求中的额外的参数信息（如：在线翻译，在线答题等提交的内容），data默认是None，此时以GET方式发送请求；当用户给出data参数的时候，改为POST方式发送请求。

3. timeout：设置网站的访问超时时间

4. cafile、capath、cadefault 参数：用于实现可信任的CA证书的HTTP请求。（基本上很少用）

5. context参数：实现SSL加密传输。（基本上很少用）

 

## 三. 返回处理方法详解
urlopen返回对象提供方法：

read() , readline() ,readlines() , fileno() , close() ：对HTTPResponse类型数据进行操作

info()：返回HTTPMessage对象，表示远程服务器返回的头信息

getcode()：返回Http状态码。如果是http请求，200请求成功完成;404网址未找到

geturl()：返回请求的url



#### **urlopen方法**

```routeros
def urlopen(url, data=None, timeout=socket._GLOBAL_DEFAULT_TI
            MEOUT,*, cafile=None, capath=None, 
            cadefault=False, context=None):
```

urlopen是request的其中一个方法，功能是打开一个URL，URL参数可以是**一串字符串**（如上例子中一样），也可以是**Request对象**（后面会提到）。

- **url**：即是我们输入的url网址，（如：[http://www.xxxx.com/](https://link.segmentfault.com/?enc=J7OHLPqcKP0OBbsRC5WXCg%3D%3D.jVJO4mZgghEPc5Vl7xYIPAH3zqdY5MYGmrIGsFo2%2F50%3D)）；
- **data**：是我们要发给服务器请求的额外信息（比如登录网页需要主动填写的用户信息）。如果需要添加data参数，那么是POST请求，默认无data参数时，就是GET请求；
  - 一般来讲，data参数只有在http协议下请求才有意义
  - data参数被规定为byte object，也就是字节对象
  - data参数应该使用标准的结构，这个需要使用urllib.parse.urlencode()将data进行 转换，而一般我们把data设置成字典格式再进行转换即可；data在以后实战中会介绍如何使用
- **timeout**：是选填的内容，定义超时时间，单位是秒，防止请求时间过长，不填就是默认的时间；
- **cafile**：是指向单独文件的，包含了一系列的CA认证 （很少使用，默认即可）;
- **capath**：是指向文档目标，也是用于CA认证（很少使用，默认即可）；
- **cafile**：可以忽略
- **context**：设置SSL加密传输（很少使用，默认即可）；
