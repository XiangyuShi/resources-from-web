---
title: css样式来源与层叠规则
date: 2016-08-20 22:10:08
tags: CSS
categories: Front-End
---

### “层叠”的概念
---

`CSS`——层叠样式表，其中的“层叠”是什么意思呢？层叠就是浏览器对多个样式来源进行叠加，最终确定结果的过程
<!--more-->
![enter description here][1]

 上图中有两个样式来源，第一个是引用的css1.css，第二个是自己在style中编写的样式。“层叠”是个叠加的过程，可通过下图表示：
 
 ![enter description here][2]

层叠是CSS的核心机制，理解了它才能以最经济的方式写出最容易改动的`CSS`，让文档外观在达到设计要求的同时，也给用户留下一些空间，让他们根据需要更改文档的显示效果，例如调整字号

### 样式来源
---

`css`之所以有“层叠”的概念，是因为有多个样式来源。其实`css`的样式来源有5个，开发人员只能接触到前面3个

![enter description here][3]

- 第一，浏览器默认样式表

浏览器自带一个默认的样式，如果`html`中没有为标签设置样式，则浏览器会按照自己的样式来显示。但是浏览器默认样式的级别是最低的，一旦有其他地方设置了标签样式，浏览器默认样式就会被冲掉

 注意，不同浏览器的默认样式有些地方是不一样的。例如，我们在写css时，都会首先设置 `* {margin:0; padding:0;}`这是为何？就是因为有浏览器兼容性问题。干脆，全部弄成0，这样各个浏览器就都统一了
 
 ```css
 html, address,blockquote,body, dd, div,dl, dt, fieldset, form,frame, frameset,h1, h2, h3, h4,h5, h6, noframes,ol, p, ul, center,dir, hr, menu, pre { display: block }/*以上列表元素默认状态下一块状显示，未显示的将以内联元素显示，该列表针对HTML4版本，部分元素在XHTML1中将废弃*/
li { display: list-item }/*默认以列表显示*/
head { display: none }/*默认不显示*/
table { display: table }/*默认为表格显示*/
tr { display: table-row }/*默认为表格行显示*/
thead { display: table-header-group }/*默认为表格头部分组显示*/
tbody { display: table-row-group }/*默认为表格行分组显示*/
tfoot { display: table-footer-group }/*默认为表格底部分组显示*/
col { display: table-column }/*默认为表格列显示*/
colgroup { display: table-column-group }/*默认为表格列分组显示*/
td, th { display: table-cell; }/*默认为单元格显示*/
caption { display: table-caption }/*默认为表格标题显示*/
th { font-weight: bolder; text-align: center }/*默认为表格标题显示，呈现加粗居中状态*/
caption { text-align: center }/*默认为表格标题显示，呈现居中状态*/
body { margin: 8px; line-height: 1.12 }
h1 { font-size: 2em; margin: .67em 0 }
h2 { font-size: 1.5em; margin: .75em 0 }
h3 { font-size: 1.17em; margin: .83em 0 }
h4, p, blockquote, ul, fieldset, form, ol, dl, dir, menu { margin: 1.12em 0 }
h5 { font-size: .83em; margin: 1.5em 0 }
h6 { font-size: .75em; margin: 1.67em 0 }
h1, h2, h3, h4, h5, h6, b,strong { font-weight: bolder }
blockquote { margin-left: 40px; margin-right: 40px }
i, cite, em,var, address { font-style: italic }
pre, tt, code, kbd, samp { font-family: monospace }
pre { white-space: pre }
button, textarea, input, object, select { display:inline-block; }
big { font-size: 1.17em }
small, sub, sup { font-size: .83em }
sub { vertical-align: sub }/*定义sub元素默认为下标显示*/
sup { vertical-align: super }/*定义sub元素默认为上标显示*/
table { border-spacing: 2px; }
thead, tbody, tfoot { vertical-align: middle }/*定义表头、主体表、表脚元素默认为垂直对齐*/
td, th { vertical-align: inherit }/*定义单元格、列标题默认为垂直对齐默认为继承*/
s, strike, del { text-decoration: line-through }/*定义这些元素默认为删除线显示*/
hr { border: 1px inset }/*定义分割线默认为1px宽的3D凹边效果*/
ol, ul, dir, menu, dd { margin-left: 40px }
ol { list-style-type: decimal }
ol ul, ul ol, ul ul, ol ol { margin-top: 0; margin-bottom: 0 }
u, ins { text-decoration: underline }
br:before { content: "A" }/*定义换行元素的伪对象内容样式*/
:before, :after { white-space: pre-line }/*定义伪对象空格字符的默认样式*/
center { text-align: center }
abbr, acronym { font-variant: small-caps; letter-spacing: 0.1em }
:link, :visited { text-decoration: underline }
:focus { outline: thin dotted invert }
 /* Begin bidirectionality settings (do not change) */
BDO[DIR="ltr"] { direction: ltr; unicode-bidi: bidi-override }/*定义BDO元素当其属性为DIR="ltr"时的默认文本读写显示顺序*/
BDO[DIR="rtl"] { direction: rtl; unicode-bidi: bidi-override }/*定义BDO元素当其属性为DIR="rtl"时的默认文本读写显示顺序*/
*[DIR="ltr"] { direction: ltr; unicode-bidi: embed }/*定义任何元素当其属性为DIR="ltr"时的默认文本读写显示顺序*/
*[DIR="rtl"] { direction: rtl; unicode-bidi: embed }/*定义任何元素当其属性为DIR="rtl"时的默认文本读写显示顺序*/
@media print { /*定义标题和列表默认的打印样式*/
    h1 { page-break-before: always }
    h1, h2, h3,    h4, h5, h6 { page-break-after: avoid }
    ul, ol, dl { page-break-before: avoid }
}

```

### 层叠的规则
---

由于样式的来源不同，浏览器在加载样式时，需要计算出最终的样式值，这样才能显示出正确的界面效果——浏览器会通过叠加和覆盖这两种方式来生成最终的样式值。

![](http://images.cnitblog.com/blog/138012/201502/062013043288083.png)

不同来源的两个样式，第一个样式设置了`font-weight`，第二个没有，浏览器会把它叠加在一起，即浏览器会把各个零散的整合成一个整体。第一个样式`color:red`，第二个样式`color:blue`，浏览器会让后者覆盖前者，最终结果还是`color:blue`

 覆盖的默认规则是后者覆盖前者，但是又一个特殊情况——`!important`
 
 ![](http://images.cnitblog.com/blog/138012/201502/062013470937714.png)
 
 虽然`color:blue`是后来者，但是它没有居上，因为前者`color:red`跟着`!important`

  [1]: http://images.cnitblog.com/blog/138012/201502/062009519846753.png
  [2]: http://images.cnitblog.com/blog/138012/201502/062010034216948.png
  [3]: http://images.cnitblog.com/blog/138012/201502/062011145462444.png
