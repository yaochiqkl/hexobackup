title: js实用的跨域方法及原理详解
date: 2015-12-20 15:41:02
tags: [ajax]
---
这里说的js跨域是指通过js在不同的域之间进行数据传输或通信，比如用ajax向一个不同的域请求数据，或者通过js获取页面中不同域的框架中(iframe)的数据。只要协议、域名、端口有任何一个不同，都被当作是不同的域。

下表给出了相对http://store.company.com/dir/page.html同源检测的结果:
![](http://images.cnitblog.com/blog/130623/201307/15184525-747de461b3b14f938b443e72ea25b25a.png)
<!-- more -->

## 一、通过jsonp跨域

在js中，我们直接用XMLHttpRequest请求不同域上的数据时，是不可以的。但是，在页面上引入不同域上的js脚本文件却是可以的，jsonp正是利用这个特性来实现的。

比如，有个a.html页面，它里面的代码需要利用ajax获取一个不同域上的json数据，假设这个json数据地址是http://example.com/data.php,那么a.html中的代码就可以这样：

![](http://images.cnitblog.com/blog/130623/201307/15184526-bcc1971f27094439b746cb1f52a715be.png)
***
