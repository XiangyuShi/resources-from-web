---
title: IE6下常见的兼容性问题
date: 2016-08-08 21:20:43
tags: 
  - CSS
  - csshack
categories: Front-End
---

#### 常见问题一：在Ie6下，内容会把父元素设置好的宽高撑开。计算一定要精确
---

```css
.box{width:400px;}
.left{width:200px;height:210px;background:red;float:left}
.right{width:200px;float:right;overflow:hidden;}
.div{width:180px;height:180px;background:blue;padding:25px;}
```

```html
<div class="box">
	<div class="left"></div>
	<div class="right">
		<div class="div"></div>
	</div>
</div>
```
<!--more-->

![](http://7xq6al.com1.z0.glb.clouddn.com/1-1.png)

![](http://7xq6al.com1.z0.glb.clouddn.com/1-2.png)

---

#### 常见问题二：在IE6元素浮动，如果宽度需要内容撑开，里面块级元素的内容也要加浮动
---

```css
.box{width:400px;}
.left{background:red;float:left;}
.right{background:blue;float:right;}
h3{height:30px;float:left;}
 ```
 
 ```html
 <div class="box">
   <div class="left">
      <h3>左侧</h3>
   </div>
   <div class="right">
      <h3>右侧</h3>
   </div>
</div>
```

![](http://7xq6al.com1.z0.glb.clouddn.com/2-1.png)

![](http://7xq6al.com1.z0.glb.clouddn.com/2-2.png)

---

#### 常见问题三：p里面不要套用p标签或者标题标签
---

![](http://7xq6al.com1.z0.glb.clouddn.com/3-1.png)

#### 常见问题四：IE6下最小高度问题
---

- 当`height<19px`的时候会被当作19px来处理

- 解决办法：`overflow:hidden`

```html
.box{height:2px;background:red;overflow:hidden}

<div class="box"></div>
```

![](http://7xq6al.com1.z0.glb.clouddn.com/4-1.png)


#### 常见问题五：`border:1px dotted `; `IE6`不支持
---

- 解决办法：切背景平铺

```html
.box{width:100px;height:100px;border:1px dotted red;margin:100px auto;}
        
<div class="box"></div>
```
![](http://7xq6al.com1.z0.glb.clouddn.com/5-1.png)

![](http://7xq6al.com1.z0.glb.clouddn.com/5-2.png)


#### 常见问题六：IE6下，父元素用边框，子元素的margin会消失 
---

- 解决办法：触发父元素的`haslayout`;

```css
.box{background:red;border:1px solid red;zoom:1;
/*padding:1px;*/}
.div{width:200px;height:200px;background:blue;margin:100px}
```

```html
<div class="box">
	<div class="div"></div>
</div>
 ```
 
 ![](http://7xq6al.com1.z0.glb.clouddn.com/6-1.png)
 
 ![](http://7xq6al.com1.z0.glb.clouddn.com/6-2.png)
  

#### 常见问题七：`IE6`双边距`bug`：横向的`margin`值会被放大为两倍
---

- 解决方法：`display:inline`;

```html
.box{width:200px;height:200px;background:red;float:left;margin:100px;display:inline;}
        
<div class="box"></div>
```

![](http://7xq6al.com1.z0.glb.clouddn.com/7-1.png)

![](http://7xq6al.com1.z0.glb.clouddn.com/7-2.png)

---


#### 常见问题八：IE6下外边距消失：当父元素的宽度和一行内容的宽度的差别`>3px`的时候 
---

- IE6双边距bug：横向的`margin`值会被放大为两倍
- 解决方法：`display:inline;`

```html
.box{float:left;border:10px solid #000;width:600px;}
.box div{
    width:100px;height:100px;background:red;margin:20px;
    border:5px solid blue;float:left;display:inline;
}
<div class="box">
      <div>1</div>
      <div>2</div>
      <div>3</div>
      <div>4</div>
      <div>1</div>
      <div>2</div>
      <div>3</div>
      <div>3</div>
</div>
```

![](http://7xq6al.com1.z0.glb.clouddn.com/8-1.png)

![](http://7xq6al.com1.z0.glb.clouddn.com/8-2.png)


#### 常见问题九：`IE6，7`下 `li`本身没有浮动，但是`li`里面的内容有浮动，每个`li`下边就会产生一个间距
---

- 解决办法：
  - 1、给`li`添加 `vertical-align:top`
  - 2、给`li`添加浮动

```css
ul{width:}
li{list-style:none;height:30px;border:1px solid #000;
/*vertical-align:top*/;float:left;}
a{width:100px;height:30px;float:left;background:red;}
span{width:100px;height:30px;float:right;background:blue;}
 ```

```html
<ul>
    <li>
        <a href="#"></a>
        <span></span>
    </li>
    <li>
        <a href="#"></a>
        <span></span>
    </li>
    <li>
        <a href="#"></a>
        <span></span>
    </li>
    <li>
        <a href="#"></a>
        <span></span>
    </li>
    <li>
        <a href="#"></a>
        <span></span>
    </li>
<ul>
```

![](http://7xq6al.com1.z0.glb.clouddn.com/9-1.png)

![](http://7xq6al.com1.z0.glb.clouddn.com/9-2.png)

---

