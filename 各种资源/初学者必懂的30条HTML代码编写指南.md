---
title: 初学者必懂的30条HTML代码编写指南
date: 2016-06-25 18:23:24
tags: 规范
categories: Front-End
---



> 本文总结了30条html代码编写指南，只要在编写HTML代码的过程中牢记它们，灵活运用，你一定会写出一手漂亮的代码，早日迈入专业开发者的行列。

### 1. 一定要闭合HTML标签
     
     在以往的页面源代码里，经常看到这样的语句：
     
    <li>Some text here.
    <li>Some new text here.
    <li>You get the idea.

<!--more-->

也许过去我们可以容忍这样的非闭合HTML标签，但在今天的标准来看，这是非常不可取的，是必须百分百避免的。一定要注意闭合你的HTML标签，否则将无法通过验证，并且容易出现一些难以预见的问题。

---
### 2. 声明正确的文档类型( DocType )

建议首先做两件事：

1. 验证CSS文件，解决所有可见的错误
2. 加上文档类型 Doctype

      `DOCTYPE` 定义在HTML标签出现之前，它告诉浏览器这个页面包含的是HTML，XHTML，还是两者混合出现，这样浏览器才能正确的解析标记。

**通常有四种文档类型可供选择：**

-  `<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN""[url=http://www.w3.org/TR/html4/strict.dtd]http://www.w3.org/TR/html4/strict.dtd[/url]">`

-  `<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "[url=http://www.w3.org/TR/html4/loose.dtd]http://www.w3.org/TR/html4/loose.dtd[/url]">`
-  `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN""[url=http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd]http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd[/url]">`

- `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "[url=http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd]http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd[/url]">`

> 关于该使用什么样的文档类型声明，一直有不同的说法。通常认为使用最严格的声明是最佳选择，但研究表明，大部分浏览器会使用普通的方式解析这种声明，所以很多人选择使用HTML4.01标准。选择声明的底线是，它是不是真的适合你，所以你要综合考虑来选择适合你得项目的声明。

---

### 3. 不要使用嵌入式CSS样式

当你在埋头写代码时，可能会经常顺手或偷懒的加上一点嵌入式css代码，就象这样：
 `<p style="color: red;">W3CFuns.com</p>`

这样看起来即方便又没有问题，但是它会在你得代码中产生问题。
     
在你开始写代码时，最好是在内容结构完成之后再开始加入样式代码。
这样的编码方式就像打游击，是一种很山寨的做法。——Chris Coyier

更好的做法是，把这个P的样式定义在样式表文件里：

    [code]someElement > p {
    color: red;
    }
    
---

### 4、在页面head标签中引入所有的样式表文件

理论上讲，你可以在任何位置引入CSS样式表，但HTML规范建议在网页的head标记中引入，这样可以加快页面的渲染速度。
  
在雅虎的开发过程中，我们发现，在head标签中引入样式表，会加快网页加载速度，
因为这样可以使页面逐步渲染。 —— ySlow团队

    <head>
    <title>My Favorites Kinds of Corn</title>
    <link rel="stylesheet" type="text/css" media="screen" href="path/to/file.css" />
    <link rel="stylesheet" type="text/css" media="screen" href="path/to/anotherFile.css" />
    </head>

---

### 5、在页面底部引入javascript文件

要记住一个原则，就是让页面以最快的速度呈现在用户面前。当加载一个脚本时，页面会暂停加载，直到脚本完全载入。所以会浪费用户更多的时间。

如果你的JS文件只是要实现某些功能，（比如点击按钮事件），那就放心的在body底部引入它，这绝对是最佳的方法。

举例：

    <p>And now you know my favorite kinds of corn. </p>
    <script type="text/javascript" src="path/to/file.js"></script>
    <script type="text/javascript" src="path/to/anotherFile.js"></script>
    </body>
    </html>
    
---

### 6、不要使用嵌入式JavaScript，这都21世纪了！

许多年以前，还存在一种这样的方式，就是直接将JS代码加入到HTML标签中。尤其是在简单的图片相册中非常常见。本质上讲，一个“onclick”事件是附加在标签上的，其效果等同于一些JS代码。不需要讨论太多，非常不应该使用这样的方式，应该把代码转移到一个外部JS文件中，然后使用“ addEventListener / attachEvent ”加入时间侦听器。或者使用jquery等框架，之需要使用其“clock”方法。

    $('a#moreCornInfoLink').click(function() {
    alert('Want to learn more about corn?');
    });

---

### 7. 开发中随时进行标准验证

很多人并不真正理解标准验证的意义和价值，笔者在一篇博客中详细分析了这个问题。一句话，标准验证是为你服务的，不是给你找麻烦的。

如果你刚开始从事网页制作，那强烈建议你下载这个网页开发工具条 ，并在编码过程中随时使用”HTML标准验证”和“CSS标准验证”。如果你认为CSS是一种非常好学的语言，那么它会把你整的死去活来。你的不严谨的代码会让你的页面漏洞百出，问题不断，一个好的方法就是—— 验证，验证，再验证。

---

### 8. 下载Firebug

Firebug是当之无愧的网页开发最佳插件，它不但可以调试JavaScript，还可以直观的让你了解页面标记的属性和位置。不用多说， 下载它！

---

### 9. 使用Firebug！

大部分的使用者仅仅使用了Firebug 20%的功能，那真是太浪费了，你不妨花几个小时的时间来系统学习这个工具，相信会让你事半功倍。

---
### 10. 使用小写的标记
理论上讲，你可以像这样随性的书写标记：

```
<DIV>
<P>Here's an interesting fact about corn. </P>
</DIV>
```

最好不要这样写，费力气输入大些字母没有任何用处，并且会让代码很难看，这样子就很好：
```
<div>
<p>Here's an interesting fact about corn. </p>
</div>
```
---

### 11.使用H1 – H6标签

笔者建议你在网页中使用其中全部六种标记，虽然大部分人只会用到前四个，但使用最多的H会有很多好处，比如设备友好、搜索引擎友好等，不妨把你的P标签都替换成H6。

---

### 12. 如果是博客，那把H1留给文章标题

今天笔者在Twitter上发起一次讨论：是该把H1定义到LOGO上还是定义到文章标题上，有80%的人选择了后者。

当然具体如何使用要看你的需求，但我建议你在建立博客的时候，将文章题目定为H1，这对搜索引擎优化(seo)是非常有好处的。

---

### 13. 下载ySlow

在过去几年里，雅虎的团队在前端开发领域做了许多伟大的工作。前不久，它们发布了一个叫ySlow的Firebug扩展，它会分析你的<网页，并返回 一个“成绩单”，上面细致分析了这个网页的方方面面，提出需要改进的地方，虽然它有点苛刻，但它绝对会对你有所帮助，强烈推荐—— ySlow！

---

### 14. 使用UL列表布局导航菜单

通常网站都会有导航菜单，你可以用这样的方式定义：

```
<div id="nav">
<a href="#">Home </a>
<a href="#">About </a>
<a href="#">Contact </a>
</div>
```

如果你想书写优美的代码，那最好不要用这种方式，
为什么要用UL布局导航菜单？
——因为UL生来就是为定义列表准备的

最好这样定义：

```
<ul id="nav"><li><a href="#">Home</a></li><li><a href="#">About</a></li><li><a href="#">Contact</a></li></ul>
```

---

### 15. 学会怎样对付IE

IE一直以来都是前端开发人员的噩梦！

如果你的CSS样式表基本定型了，那么可以为IE单独建立一个样式表，然后这样仅对IE生效：
```        
<!--[if lt IE 7]>
<link rel="stylesheet" type="text/css" media="screen" href="path/to/ie.css" />
<![endif]-->
```

这些代码的意思是：如果用户浏览器是IE6及以下，那这段代码才会生效。如果你想把IE7也包含进来，那么就把“[if lt IE 7]”改为“[if lt IE 7]”。

---

### 16. 使用一个好的代码编辑器

不论你是Windows还是Mac用户，这里都有很多优秀的编辑器供你选择：

- Mac 用户

     ?Coda     
     ?Espresso
     ?TextMate
     ?Aptana
     ?DreamWeaver CS4

- PC 用户

     ?InType
     ?E-Text Editor
     ?Notepad++
     ?Aptana
     ?Dreamweaver CS4
     
     
---


### 17. 压缩前端代码！

Javascript 压缩服务

     ?Javascript Compressor
     ?JS Compressor

CSS Compression Services

 - ?CSS Optimiser
 - ?CSS Compressor
 - ?Clean CSS

---

### 18. 缩减，缩减，缩减

回望我们大多数人写的第一个页面，一定会发现严重的 “DIV癖”( divitis )，通常初学者的本能就是把一个段落用DIV包起来，然后为了控制定位而套上更多的DIV。—— 其实这是一种低效而有害的做法。

网页写完后，一定要多次回头检查，尽量的减少元素的数量。
能用UL布局的列表就不要用一个个的DIV去布局。

正如写文章的关键是“缩减，缩减，缩减”一样，写页面也要遵循这个标准。

---

### 19. 为所有的图片加上Alt属性

为图片加上alt属性的好处是不言而喻的 —— 这样可以让禁用图片或者使用特殊设备的用户无障碍得了解你的王爷信息，并且对图像搜索引擎友好。

firefox不支持显示图像Alt属性，可以加入title属性：

    <img src="cornImage.jpg" alt="W3CFuns.com" title="W3CFuns.com" />

---

### 20. 学会熬夜

我经常不知不觉的学习工作到凌晨，我认为这是个很好的状况。

---

### 21. 查看源代码

没有什么比模仿你的偶像能让你更快的学习HTML。起初，我们都要甘做复印机，然后慢慢得发展自己的风格。研究你喜欢的网站页面代码，看看他们是怎么实现的。这是高手的必经之路，你一定要试一下。注意：只是学习和模仿他们的编码风格，而不是抄袭和照搬！

留意网络上各种炫酷的JavaScript效果，如果看上去是使用了插件，那根据它源码中head标签内的文件名，就可以找到这个插件名称，然后就可以学习它据为己用。

---

### 22. 为所有的元素定义样式

这一条在你制作其他公司企业网站时尤为必要。你自己不使用blockquote标记？那用户可能会用，你自己不使用OL？用户也可能会。花时间做一个页面，显示出ul, ol, p, h1-h6, blockquotes, 等等元素的样式，检查一下是否有遗漏。

---

### 23. 使用第三方服务


 现在互联网上流行着许多可以免费加在网页中的API，这些工具非常强大。它可以帮你实现许多巧妙的功能，更重要的是可以帮你宣传网站。

---

### 24. 学习photoshop

Photoshop是前端工程师的一个重要工具，如果你已经熟练掌握HTML和CSS，那不妨多学习一下Photshop。

- 1.Psdtuts+上有许多英文的饰品教程：Videos section
- 2.Lynda.com 也有大量教程，不过要支付$25美元
- 3.“You Suck at Photoshop” 系列教程
- 4.花费几个小时的时间学习Photoshop的快捷键操作

---

### 25. 学习每一个HTML标签

虽然有些HTML标签很少用到，但你依然应该了解他们。比如“abbr”、“cite”等，你必须学习它们以备不时之需。

---

### 26. 参与社区讨论

网络上有许许多多优秀的资源，而社区中也隐藏着许多高手，这里你既可以自学，也能请教经验丰富的开发者。

---

### 27. 使用CSS Reset

Css Reset也就Reset Css ,就是重置一些HTML标签样式，或者说默认的样式。

关于是否应该使用CSS Reset，网上也有激烈的争论，笔者是建议使用的。你可以先选用一些成熟的CSS Reset，然后慢慢演变成适合自己的。

---

### 28. 对齐元素

简单来说，你应该尽可能的对齐你的网页元素。可以观察一下你喜欢的网站，它们的LOGO、标题、图表、段落肯定是对得非常整齐的。否则就会显得混乱和不专业。

---

### 29. 关于PSD切片

现在你已经掌握了HTML、CSS、Photoshop知识，那么你还需要学习如何把PSD转换为网页上的图片和背景，下面有两个不错的教程：

- Slice and Dice that PSD
- From PSD to HTML/CSS

---

### 30. 不要随意使用框架

Javascript和CSS都有许多优秀的框架，但如果你是初学者，不要急于使用它们。如果你还没能熟练的驾驭CSS，使用框架会混淆你的知识体系。

CSS框架是为熟练开发者设计的，这样会节省它们大量的时间。