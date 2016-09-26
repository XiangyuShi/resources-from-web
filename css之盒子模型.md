---
title: css之盒子模型
date: 2016-08-21 00:18:08
tags: CSS
categories: Front-End
---

### 盒子的宽度
---

在盒子模型中，我们设置的宽度都是内容宽度，不是整个盒子的宽度
盒子的宽度=`margin-right+margin-left+border-left+padding-left+width+padding-right+border-right`
<!--more-->
#### 设置了固定宽度的情况下
---

![](http://images.cnitblog.com/blog/138012/201502/120828055113043.png)

因此，在盒子模型中，我们设置的宽度都是内容宽度，不是整个盒子的宽度。而整个盒子的宽度是：（`内容宽度 + border宽度 + padding宽度 + margin宽度`）之和。这样我们改四个中的其中一个，都会导致盒子宽度的改变。这对我们来说不友好

#### 充满父容器的情况下
---

默认情况下，`div`的`display:block`，宽度会充满整个父容器。如下图：

![](http://images.cnitblog.com/blog/138012/201502/120829117619136.png)

这个`div`是个盒子模型，它的整个宽度包括（`内容宽度 + border宽度 + padding宽度 + margin宽度`），整个的宽度充满父容器。

问题就在这里。如果父容器宽度不变，我们手动增大`margin`、`border`或`padding`其中一项的宽度值，都会导致内容宽度的减少。

极端情况下，如果内容的宽度压缩到不能再压缩了（例如一个字的宽度），那么浏览器会强迫增加父容器的宽度。这可不是我们想要看到的

#### 包裹内容的情况下
---

这种情况下比较简单，内容的宽度按照内容计算，盒子的宽度将在内容宽度的基础上再增加（`padding宽度 + border宽度 + margin宽度`）之和

![](http://images.cnitblog.com/blog/138012/201502/120829483089838.png)

### 再看盒子的宽度
---

前面提到，为盒子模型设置宽度，结果只是设置了内容的宽度，这个不合理。如何解决这一问题？**答案就是**：`box-sizing:border-box`

![](http://images.cnitblog.com/blog/138012/201502/120830294011050.png)

如上图，`div`设置了`box-sizing:border-box`之后，`300px`的宽度是内容 + `border `+ 边框的宽度（不包括`margin`），这样就比较符合我们的实际要求了。

建议大家在为系统写`css`时候，第一个样式是

![](http://images.cnitblog.com/blog/138012/201502/120830507768619.png)


### 纵向margin的重叠
---

如下图，`<p>`的纵向`margin`是`16px`，那么两个`<p>`之间纵向的距离是多少？

按常理来说应该是 `16 + 16 = 32px`，但是答案仍然是` 16px`。因为纵向的`margin`是会重叠的，大的会把小的“吃掉”

![](http://images.cnitblog.com/blog/138012/201502/120831356517143.png)

### 用div画“三角”
---

　“三角”在日常的网页中是很常见的，例如百度首页：
 
 ![](http://images.cnitblog.com/blog/138012/201502/120832351362371.png)

你当然可以使用背景图片来实现这一效果，但是你也可以用`div`来实现这一效果，很简单，而且可以封装通用：

![](http://images.cnitblog.com/blog/138012/201502/120832509339145.png)










