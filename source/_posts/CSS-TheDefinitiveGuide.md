title: 'CSS权威指南读书笔记'
date: 2015-10-29 20:05:39
tags: [CSS]
---
CSS权威指南（第三版）
![CSS:The Definitive Guide (The 3rd Edition)](http://img3.douban.com/lpic/s2921314.jpg)

## 选择器
### 属性选择器
简单属性选择	h1[class]{color:silver;}

根据部分属性选择  p[class~="warning"]{font-weight:bold;}
(子串匹配属性选择器 [foo^="bar"] \\ [foo$="bar" \\ foo*="bar"])
<!-- more -->
### 选择相邻兄弟元素
li+li{font-weight:bold;} 紧跟在一个li后面出现的所有兄弟li元素

### 伪类
#### 选择第一个子元素 
p:first-child{font-weight:bold;} **作为第一个子元素的p元素**
（将规则关联到**前一个**规则）
> :link :first-child ...

### 伪元素 
首字母样式 p:first-letter{color:red;}

第一行样式 p:first-line{color:blue;}

之前/之后样式 h2:before {content:"aa";color:silver;} 插入生成内容

>:first-line :first-letter :before :after 

***
## 结构和层叠
### 特殊性
特殊性值表述为四个部分：[0 0 0 0]
分别对应着 **内联样式 / ID属性 / 类、属性选择、伪类/元素、伪元素**
通配符
重要性 !important 放置声明之后

### 继承
继承值**无**特殊性
0特殊性 > 无特殊性

### 层叠
规则
<div style = "border:2px solid black;background:#FFF;">&nbsp;1.样式表来源和重要性 创作人员>读者>用户代理（浏览器）【!important读者最强】
&nbsp;2.特殊性排序
&nbsp;3.出现的顺序排序
</div>

>LVHA规则:  link visited hover active

第七章以后很多内容太枯燥、难以理解了。需要多动手实际操作，加深理解。