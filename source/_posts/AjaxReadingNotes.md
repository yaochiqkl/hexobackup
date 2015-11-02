title: Head First Ajax 读书笔记
date: 2015-10-27 22:36:49
tags:
---
Reading Notes
![Head First Ajax](http://img3.douban.com/lpic/s4245583.jpg)
===
总的来说，延续了一贯的HeadFirst风格，文章诙谐幽默，不适令人忍俊不禁，难得一见的好书。

## AJAX ( Asynchronous JacaScript and XML )
核心是XHR对象，以异步方式从服务器获取信息

**工具函数-创建请求对象（uils.js）** 
>DRY原则
```
function createRequest(){
	try{
	request = new XMLHttpRequest(); 兼容大多数非IE浏览器
    } catch (tryMS) {
    request = new ActiveXObject("Msxm12.XMLHTTP"); 兼容IE7以前的版本
    } catch (OtherMS) {
    request = new ActiveObject("Microsoft.XMLHTTP");兼容IE7以前的版本
    } catch (faild) {
    request = null
    }
}
```
**XHR用法**
```
request.open("get",url,false); 调用请求
request.send(null);            发送请求
request.responseTest;
request.responseXML;

request.status;                1、2、3、4
request.readyState;            HTTP状态码
request.onreadyStateChange;    回调函数
```

## XML && JSON  (还有罕见的CSV)

>**XML** (Extensive Markup Language)
创建无类型的XML-DOM树
>**JSON**（JavaScript Standard Object Notation)
对JavaScript友好，速度快，轻量级数据格式。创建标准的JS对象。

## 表单验证

正则表达式
>更详尽内容参考《精通正则表达式》

## GET && POST
GET  常用于查询信息。直接将数据追加到URL末尾，但必须经过正确的编码"encodeURIComponent()"。
```
function addURLparam(url,name,value){
    url += (url.indexOf("?")) == -1 ? "?" : "&" ); 问号是否存在
    url += encodeURIComponent(name) + "=" + encodeURIComponent(value);
    return url;
}
```
POST 常用于应被保存的数据。加密，在浏览器中编码，并在服务器上解码。传递到Request.send()之中。消耗资源比GET多。
额外添加*Content-Type*属性名/值对时使用**“application/x-www-form-urlencoded”**。


>等详尽内容参考JS红宝书
> 后记：适合入门，循序渐进。提供的相关的例子很经典，值得揣摩。