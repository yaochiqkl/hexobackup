title: 锋利的jQuery
date: 2015-11-06 20:12:02
tags: [jQuery]
---
![锋利的jQuery](http://img4.douban.com/lpic/s28026858.jpg)
每天都在图书馆查这本书，这两天终于等到别人还过来了，这几天借的书还不少，有十本，都快达上限了，就不能借一本自习看一本么！？
想起之前在一家IT公司实习的时候用jQuery的随意，殊不知jQuery是如此这般强大！看了两天图书馆已然有人归还第二版，速速换之。
书中很多实例很有趣，很值得自己去实现。
<!-- more -->
## 选择器
1.基本选择器
2.层次选择器 > + ~
3.过滤选择器
	1.基本过滤 :first :not() :qe() :qt() :animated
	2.内容过滤 :contains(text) :empty :has() :parent
	3.可见性过滤 :hidden :visible
	4.属性过滤 [attribute] [attribute^=value]
	5.子元素过滤 nth-child(index) :first-child
	6.表单对象过滤 :enabled :disabled 
4.表单选择器 :input(input+button+textarea) :hidden
***
## DOM操作
1.节点操作
	1.创建节点
	2.插入节点 append() prepend() apendTo() after() before()
	3.删除节点 remove() empty()
	4.复制节点 clone()
	5.替换节点 replaceWith() replaceAll()
	6.包裹节点 wrap()
2.属性操作 attr() removeAttr()
3.样式操作 addClass() removeClass() toggleClass() hasClass()
***
## 事件

1.DOM就绪后执行
```
	$(ducument).ready(function(){}) 
	$(function(){})
	$().ready(function(){})
```
2.事件绑定
```
$("#a").bind("mouseover",function(){});
$("#a").mouseover(function(){}); 简写
```
可以**一次性绑定多个事件**
```
$("#a").bind("mouseover mouseout",function(){
	$(this).toggleClass("over");
})
```
3.合成事件
```
hover(enter,leave)
toggle(f1,f2,...)
```
4.事件冒泡 

```
$('span').bind("click",function(event){
	event.stopPropagation(); 停止事件冒泡
	event.preventDefault();  阻止默认行为（如超链接的跳转）
})
```
5.事件对象
event.type
event.target
event.pageX  获取光标的坐标
event.which 鼠标单击的左中右键
6.移除事件
```
$('button').unbind();
最好在事件绑定时指定变量 
$('button').bind("click",myFun1=function(){
	...
})
```
One方法：触发一次，立即解绑
```
$('button').one("click",function(){
	...
})
```
7.模拟操作 触发函数
```
$('button').trigger("click")
```
**△添加命名空间 **方便管理
```
$('button').bind("click.plugin",function(){
	..
});
$('button').unbind(".plugin");
```
***
## 动画
1.show() & hide()
2.fadeIn() & fadeOut()
3.slideUp() & slideDown()
4.**animate()**
```
animate(params,speed,callback);
```
5.stop() & delay()
停止动画 stop()
```
stop(ClearQueue,gotoEnd)
Boolean值，前者清空队列，后者跳到当前动画的末状态
```
延迟动画 delay()
后借时间，单位**ms**
6.**其他**
```
toggle()
slideToggle()
fadeTo()
fageToggle()
```
<div class="a">
	<a href="/images/1.jpg" class="tip" title="Prompt1"><img src="/images/1.jpg" style="heiht:100px;width:200px;"></a><br>
	<a href="/images/2.jpg" class="tip" title="Prompt2"><img src="/images/2.jpg" style="heiht:100px;width:200px;"></a><br>
	<a href="/images/3.jpg" class="tip" title="Prompt3"><img src="/images/3.jpg" style="heiht:100px;width:200px;"></a>
</div>
<script src="http://lib.sinaapp.com/js/jquery/1.9.1/jquery-1.9.1.min.js"></script>
<script type="text/javascript">
$(function(){
	var x = 10;
	var y = 20;
	$(".tip").mouseover(function(e){
		this.myTitle = this.title;
		this.title = "";
		var imgTitle = this.myTitle? "<br/>this.myTitle":"";
		var tip = "<div id='tip'><img src='"+this.href+"' alt='fuckme'>"+imgTitle+"</div>";
		$("body").append(tip);
		$("#tip").css({
				"top":(e.pageY+y)+"px",
				"left":(e.pageX+x)+"px",
				"border":"1px solid black",
				"blackground":"yellow",
				"position":"absolute"
			}).show("slow");
	}).mouseout(function(){
		this.title = this.myTitle;
		$("#tip").remove();
	}).mousemove(function(e){
		$("#tip").css({
			"top":(e.pageY+y)+"px",
			"left":(e.pageX+x)+"px"
		});
	});
});
</script>