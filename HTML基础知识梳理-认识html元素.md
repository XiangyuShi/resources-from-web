---
title: HTML基础知识梳理-认识html元素
date: 2016-06-25 18:21:43
tags: XHTML
categories: Front-End
---


认识一个html文档的基本结构：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Here is title</title>
</head>
<body>
    Here is content.
</body>
</html>

```
<!--more-->

> HTML 文档是由 HTML 元素 定义的，而HTML 元素指的是从开始标签（start tag）到结束标签（end tag）的所有代码。

**首先，HTML元素从闭合属性上可分为2类：**

- 自闭和标签

自闭和标签在html元素中的比例不大，常用的就以下几个：

    <img /> <br /> <input /> <hr />


- 手动闭合标签

**常用的标签：**
---

```html
<h1></h1>....
<p></p>
<div></div>
<a></a>
<button></button>
<span></span>
<label></label>
<textarea></textarea>
<table></table>
<thead></thead>
<tbody></tbody>
<tr></tr>
<th></th>
<td></td>
<ul></ul>
<li></li>
<dl></dl>
<dt></dt>
<dd></dd>
<form></form>
```

### 一、块级元素
---

**div**

含义：页面内容的一个独立组成部分。

常见的用途有三种：

- 划分页首、页尾、页边栏或导航栏等等；
- 表示页面的分栏；
- 将文章进一步分成几个部分，比如正文、评论、文章的元数据等等。

示例：

    <div>这里面可以只放文本，也可以放其他任何标签，当然可以放自己</div>


![此处输入图片的描述][1]

**h1, h2, h3, h4, h5, h6**

含义：内容的标题。

h1是最高一级的标题，下一层标题使用h2，依次类推。除了h1以外，其他5个级别标题在一个页面中都可以出现多次，h1只能出现一次。

示例：

    <h1>一级标题</h1>
    <h2>二级标题</h2>


**p**

含义：表示段落。

它是文章内容的基本组成部分，也可以用来表示诗歌中的一节。p与div的主要区别是，前者表示文本段落，后者表示更广义的段落
    
在P标签中，不应该再包含其他块级元素。此外，也不应该使用空的p标签。标签具有确切的语义，用于定义段落

示例：

    <p>这是一个段落。</p>


**blockquote**

含义：表示一段引用自其他来源的独立文本。

它引用的文本通常有一定的长度，以块级元素的形式出现。
blockquote应该总是与cite标签配合使用，cite用来指明引用材料的来源。

示例：

    <blockquote>
    不是在沉默中爆发，就是在沉默中灭亡。
    <cite>鲁迅《为了忘却的纪念》</cite>
    </blockquote>

在浏览器的默认样式中，blockquote有文本缩进的效果，但是不要单单因为这个原因，而使用它。

blockquote有两个属性，第一个是cite属性，用来指明引用材料的URI地址；第二个是title属性，用于提供引用材料的相关信息。
示例：

    <blockquote cite="http://w3c.org/" title="文章的标题，作者，发表日期">"我正在此处引用W3C的标准。"</blockquote>


### 二、行内元素
---

**a**

含义：与href属性搭配使用时，链接至外部链接，或者同一页的某个锚点。

示例：

    <a href="chapter2.html">第二章</a>


**abbr**
含义：表示内容是某个术语或短语的缩写形式，它有一个title属性，用来指明缩写所代表的原始词组。
示例：

    <abbr title="Europe">Eur</abbr>


**acronym**

含义：表示内容是一个词组的首字母简称，比如BBC、WTO。

它有一个title属性，用来指明属性所代表的原始词组。
acronym与abbr的主要区别是，前者往往是一个可以独立使用的词，而后者不是。这意味着acronym肯定是abbr，但是abbr不一定是acronym。
示例：

    <acronym title="World Wide Web">WWW</acronym>
    

**em**

含义：表示强调。

em所指明的内容，应该比其周围的内容更重要。
注意，如果你只是想表示斜体或者引用书名，那就不要使用em标签，而是用CSS命令（font-style:italic）。

示例：

    <em>我正在强调这句话。</em>

**strong**

含义：表示比em更强的强调。

示例：

    <strong>我正在以更大的强度，强调这句话。</strong>


**address**

含义：表示某个特定文档或文档的某个部分的联系信息或联络方式。
**注意：**

- 所有的联络方式都可以用这个标签表示，而不仅仅是地址。
- 它是一个块级元素，不要用它来单独标识某个Email地址或电话号码。

示例：

    <address>
    <a href="../People/张三/">张三</a>, 
    <a href="../People/李四/">李四</a>, 
    $ 日期：1999/12/24 23:37:50 $
    </address>


**cite**

含义：表示引述的来源。

它用来指明书目信息、个人引语、或者参考文献中的外部资源。
示例：

`<cite>《哈利波特系列小说》</cite>`的作者是J.K.罗琳。


**dfn**

含义：用来表示一个定义。
示例：

    <dfn>Internet Explorer</dfn>是最常见的浏览器。


**del**

含义：表示该信息已被删除。
通常用于日期和时间，表示文档已经发生了变化。

**ins**

含义：与del的作用正好相反，表示修订后插入的内容。


**code**

含义：表示程序代码。

**samp**

含义：表示程序代码的输出结果。

**kbd**
含义：表示由用户键入的文本。

它很少使用，但是在某些场合，你想演示如何使用一个程序，它就会有用。它通常与code和samp结合使用。

**var**

含义：表示程序中的变量或参数，与code, samp, kbd结合使用。

**q**
含义：表示一个较短的引语。
注意：浏览器对这个标签的支持很不好，因此不推荐使用


**sub/sup**

含义：表示下标/上标。

**span**

含义：用来标识其他标签不适合表示的内容，是一个通用型的行内标签。


### 三、列表元素
---

    ul, ol, li

含义：表示一组相同格式的信息。
当你有一张清单的时候，就应该使用列表元素。ul是无序列表，通常前面有一个强调符号；ol是有序列表，前面通常采用数字编号。


**ul标签**

    <ul>
    <li>Coffee</li>
    <li>Tea</li>
    <li>Milk</li>
    </ul>
    <ul></ul> 标签定义无序列表。

![此处输入图片的描述][2]


**ol标签**
```html
<ol>
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ol>
<ol start="50">
  <li>咖啡</li>
  <li>牛奶</li>
  <li>茶</li>
</ol>
<ol type="A">
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ol>
```

- <ol> </ol>标签定义有序列表。
- ol上有以下几个常用属性：
- start规定有序列表的起始值，默认为1。
- type规定在列表中使用的标记类型。

![此处输入图片的描述][3]


dl, dd, dt
含义：表示一个术语列表。
dt表示术语，dd表示该术语的定义，可以为单个术语提供多个定义。
示例：
```html
<dl>
   <dt>各个学院</dt>
   <dd>风景园林学院</dd>
   <dd>家具设计学院</dd>
  <dd>林学院</dd>
  <dd>艺术设计学院</dd>
  <dd>信息科学与技术学院</dd>
</dl>
```
- `<dl>` 标签定义了定义列表（definition list）。
- `<dl>` 标签用于结合dt（定义列表中的项目）和 dd (描述列表中的项目）。

![此处输入图片的描述][4]


### 四、表单元素
---

**form标签**

<form> 标签用于为用户输入创建 HTML 表单，在页面中用户看不到form元素的显示效果。
表单能够包含 input 、label、button、select等等元素。

**input**

`<input />` 标签用于搜集用户信息。
根据不同的 type 属性值，输入字段拥有很多种形式:
输入字段可以是文本字段、复选框、掩码后的文本控件、单选按钮、按钮等等。

**文本框**

    <input type="text" value=""  placeholder="" />
    <input type="text" value="这是value"  placeholder="" />
    <input type="text" value=""  placeholder="这里是提示文字" />
    value代表此文本框中显示的值,placeholder设置的值表示当value为空时，给用户的提示文字。

**密码框**

    <input type="password" value="" />
    <input type="password" value="123456" />
    <input type="password" value="" placeholder="请输入密码" />

![此处输入图片的描述][5]


**单选框**

    <input type="radio" value="male" checked name="gender" /> 男
    <input type="radio" value="female" name="gender" /> 女
    value:在界面上不会显示出来；
    checked:如果存在，则表示默认选中；
    name： 当多个<input type="radio" />的name属性值相同时，表示这多个单选框，同时只能有一个选中；
![此处输入图片的描述][6]



**复选框**


    <input type="checkbox" value="footballl" checked name="hobbies" /> 足球
<input type="checkbox" value="basketball" name="hobbies" /> 篮球
多个复选框的name即使相同，也可以同时选中；
![此处输入图片的描述][7]

**textarea元素**

    <textarea rows="10" cols="30">
    在这篇文章中，你可以对html元素有基本的了解。
    </textarea>
    <textarea> 标签定义多行的文本输入控件,上面介绍的<input type="text">是单行文本框。
    可以通过 cols 和 rows 属性来规定 textarea 的尺寸，不过更好的办法是使用 CSS 的 height 和 width 属性。

![此处输入图片的描述][8]


**select标签**


    <select>
      <option value="">请选择学院名称</option>
      <option value="1">风景园林学院</option>
      <option value="2">家具设计学院</option>
      <option value="3">林学院</option>
      <option value="4">艺术设计学院</option>
      <option value="5">信息科学与技术学院</option>
    </select>
    <select></select> 元素可创建单选或多选菜单；
    select元素中的<option></option>标签用于定义列表中的可用选项。

![此处输入图片的描述][9]


**表格元素**


    <table border="1">
    <thead>
      <tr>
        <th>姓名</th>
        <th>性别</th>
      </tr>
    </thead>
    <tbody> 
      <tr>
        <td>abcdefg</td>
        <td>男</td>
      </tr>
      <tr>
        <td>殷晓飞</td>
        <td>男</td>
      </tr>
    </tbody>
    </table>
    表格一般由多个子元素构成：
    <table></table>：最外层容器（可以通过设置border属性来控制表格边框）；
    <thead></thead>：表格头——用于包裹表格的顶部信息;
    <tbody></tbody>: 表格主题内容;
    <tr></tr>表示一行记录；
    <td></td>表示一列，但嵌套在tbody标签的tr标签内；
    <th></th>也表示一列，但嵌套在thead标签的tr标签内；
    注意：
    一个表格只有一个table标签；
    一个table标签内只有一个thead和一个tbody;
    一个thead内只有一个tr,thead中的tr中可以有多个th（可以有多列）;
    一个tbody中可以有多个tr（可以有多行记录）,每个tr中可以有多个td（可以有多列）；
![此处输入图片的描述][10]
![此处输入图片的描述][11]
---
**button元素**

    <button type="button">提交按钮</button>

![此处输入图片的描述][12]


**label元素**

    <label for="male">Male</label>
    <input type="radio" name="sex" id="male" />
    <br />
    <label for="female">Female</label>
    <input type="radio" name="sex" id="female" />
    <label> 标签为 input 元素定义标注（标记）。
    label 元素不会向用户呈现任何特殊效果。不过，它为鼠标用户改进了可用性。
    如果您在 label 元素内点击文本，就会触发此控件。
    就是说，当用户选择该标签时，浏览器就会自动将焦点转到和标签相关的表单控件上。
    <label> 标签的 for 属性应当与相关元素的 id 属性相同。
![此处输入图片的描述][13]


### 五、分割元素
---

**br**

含义：表示换行。

注意，除了少数场合（比如诗歌中的分行），应该尽量避免使用这个标签，因为它并没有特别的语义含义，而且分行的视觉效果完全可以通过p标签、列表标签和CSS命令达到。


**hr**

含义：表示两个部分之间用一根水平直线分割。
事实上，不用这个标签，也有办法显示水平直线。这个标签的唯一优势，也许就是在没有CSS的场合，它可以产生视觉分割的效果。

### 六、不建议使用的元素
---

以下的标签都没有明确的语义，只涉及到视觉效果，很可能在以后版本的HTML语言中被废除。建议不要使用。

* big
* small
* b
* i
* tt
* pre


### 七、已经被废除的标签
---

**下面的标签已经被废除，不应该继续使用了。**

- `applet`
- `center`
- `font`
- `dir`
- `isindex`
- `menu`
- `s`
- `strike`
- `u`

  [1]: http://upload-images.jianshu.io/upload_images/712523-36e772d7c9db4fe1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
  [2]: http://upload-images.jianshu.io/upload_images/712523-41aac667827ef04c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
  [3]: http://upload-images.jianshu.io/upload_images/712523-6ffe8311971c2361.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
  [4]: http://upload-images.jianshu.io/upload_images/712523-ae3949d9d4043e10.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
  [5]: http://upload-images.jianshu.io/upload_images/712523-1e87a670229cb326.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
  [6]: http://upload-images.jianshu.io/upload_images/712523-1e5e35cf2861dd16.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
  [7]: http://upload-images.jianshu.io/upload_images/712523-7097ba4c2b4dcdcd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
  [8]: http://upload-images.jianshu.io/upload_images/712523-1c58c399783b0396.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
  [9]: http://upload-images.jianshu.io/upload_images/712523-96071bd21321b02e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
  [10]: http://upload-images.jianshu.io/upload_images/712523-99a6518b38b9b57a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
  [11]: http://upload-images.jianshu.io/upload_images/712523-b59b79d93ad2623a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
  [12]: http://upload-images.jianshu.io/upload_images/712523-0ae24d958cfa9219.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
  [13]: http://upload-images.jianshu.io/upload_images/712523-2ca56a9ba293220b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240