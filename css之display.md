---
title: css之display
date: 2016-08-21 01:10:08
tags: CSS
categories: Front-End
---

### 引言
---

网页的所有元素，除了“块”就是“流”，而且“流”都是包含在“块”里面的（最外层的body就是一个“块”）
<!--more-->
![](http://images.cnitblog.com/blog2015/138012/201503/060814201807518.png)

在网上查找出`display`所有的属性，你会发现它有很多，但是不是每个都常用，甚至大部分你都没有用过

![](http://images.cnitblog.com/blog2015/138012/201503/060814397278889.png)

看上图。常用的属性有：`none`、`block`、`inline`、`inline-block`、`inherit`，其中`inherit`是继承父元素的样式

-` list-item`：通过它可以模拟li列表样式；
- `table`：也是一个“块”，但和`block`相比，`table`具有包裹性；
- `table-cell`：最新的多列布局解决方案；

###  inline
---

常用的`inline`就是文字和图片，其实`inline`真没什么好说的，大家可以把它想象成一个杯子里的水，它是“流”，是没有大小和形状的，它的宽度取决于父容器的宽度。

因此，针对	`inline`的标签，你设置宽度和高度是无效的，通过监控可以知道，该元素实际的宽度和高度都是`auto`，并不是我们设定的值

![](http://images.cnitblog.com/blog2015/138012/201503/060815408991678.png)

一个很基础的问题：如何把`inline`元素转换成“块”元素？相信绝大部分人的回答是`display:block`，但是你应该知道这不是一个唯一的答案。至少我设置`display:table`也是可以的吧？

还有两种情况你应该去了解

#### 第一，对inline元素设置float
---

我们对`span`元素添加一个`float:left`，运行看看效果，你就会大吃一惊。从显示的效果和监控的结果上看来，`span`元素已经“块”化。不要忘记`float`的“破坏性”、“包裹性”，在这里同样适用。

![](http://images.cnitblog.com/blog2015/138012/201503/060816212111595.png)

####  第二，对inline元素设置position:absolute/fixed
---

 还是有同一个例子做演示，这次在`span`元素上加上`absolute/fixed`，效果大家应该能猜到，和加上`float`的效果相同。
 
 ### inline-block
 
 浏览器默认样式中规定了几个`html`元素为`display:inline-block`，回顾一下
 
 ![](http://images.cnitblog.com/blog2015/138012/201503/060817421642526.png)
 
 因此，`inline-block`的特点可以总结为：外部看来是“流”，但是自身确实一个“块”。
 
