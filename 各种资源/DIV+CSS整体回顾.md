---
title: DIV+CSS整体回顾
date: 2016-07-30 16:35:08
tags: 
    - CSS
    - XHTML
categories: Front-End
---

## 第一节 基本标签样式
---

- 非可视化标签：`head`  `meta`  `style`  `scrpit.`..
- 可视化标签：`img`  `div` `span` `a` `ul` `li`...
- 只有可视化标签，才能用`css`改变它
- 单标签：`meta`  `link`  `base`  `img`  `input` `br` `hr`
- 双标签：`html` `head` `body`  `div`  `a`  `p`  `span` ..`ul` `li` `ol` ` dl` 
<!--more-->

- **常用可视化标签**

	- **div** 
		- 一般用它来布局
	- **a**  超链接标签
		- `href`*属性：设置跳转的网页地址
		- `target`属性：设置跳转的目标
		- 结论：凡事页面可以点击跳转或者表单提交的文字，都用`a`标签
	- **img**
		- `src`*属性用来设置图片的url数据
		- `alt`提供给搜索引擎搜索的
		- `width`
		- `height`
		- 结论 ：显示图片
	- **ul li**
		- 列表
		- 结论：只要将来设计页面中有固定样式的列表，就用ul和li
	- **table caption tr td (th)**
		- 慢慢已经被淘汰了 被ul li代替
		- 如果是合并竖排的就是合并行（`rowspan`）
		- 如果是合并横排的就是合并列（`colspan`）


 - **知识点：**
---

    - **css概念**
        - 层叠样式表
        - 作用：它的作用是让页面中的可视化标签变得漂亮
    - **css的三种书写方法以及优先级**
        - a.内联式：通过标签的`style`属性设置样式（不用）
        - b.嵌入式：写在`head`标签里的style标签里面来改变选择器选择中标签样式（不用）
        - c.引用式：携程一个`XXX.css`文件通过`link`标签的`href`属性去引入（只准用这种方式）-`css`文件中有可能用中文 造成字符集编码的问题 解决方法：在`css`文件中最上面 加上一句` @charset "UTF-8"`
        -  d、导入式 (只做了解)  `@import url(my.css)`

        - **结论**：推荐使用引用式 用内联式的时候通常是调试盒子的时候
        - **层叠次序**  浏览器默认<外联式<内联式<内嵌式

        - 	优先级是就近原则

    - **css的选择器**
        - a.id选择器  标签设置id属性    `css` ` #id`值 （不常用） 优先级最高
        - b.标签选择器` div  span  em  a  p	`（不用，例外：`html,body`）
        - c.类选择器	标签设置class属性  `css`  `.class`值  （不常用） 
        - d.混合选择器  （推荐使用）  优先级第二（越详细优先级越高）
        - **结论**：能把选择器描述越详细越好

      
```css
 /**雅虎工程师提供的CSS初始化示例代码,在html头文件中直接引用，从而避免浏览器的不兼容带来的错误**/

body,div,dl,dt,dd,ul,ol,li,h1,h2,h3,h4,h5,h6,pre,code,form,fieldset,legend,input,button,textarea,p,blockquote,th,td { margin:0; padding:0; }
body { background:#fff; color:#555; font-size:14px; font-family: Verdana, Arial, Helvetica, sans-serif; }
td,th,caption { font-size:14px; }
h1, h2, h3, h4, h5, h6 { font-weight:normal; font-size:100%; }
address, caption, cite, code, dfn, em, strong, th, var { font-style:normal; font-weight:normal;}
a { color:#555; text-decoration:none; }
a:hover { text-decoration:underline; }
img { border:none; }
ol,ul,li { list-style:none; }
input, textarea, select, button { font:14px Verdana,Helvetica,Arial,sans-serif; }
table { border-collapse:collapse; }
html {overflow-y: scroll;} 

.clearfix:after {content: "."; display: block; height:0; clear:both; visibility: hidden;}
.clearfix { *zoom:1; }

```

### 第二节 常用css属性
---

#### 知识点：
- .**常用css属性**
	- a.width,元素的宽度
	- b.height,元素的高度
	- c.color,元素里的内容文本的颜色
   - **结论**：`css`的样式属性`99%`的具有继承性 （a标签没有继承性）
	- d.`border`边框,通过`border`属性设置元素的边框
		- `border`分为上下左右边框
		- `border-top\bottom\left\right`:像素 实线|虚线 颜色;
	- e.`background`
		- `background-color:#00FF00`;/*背景的颜色*/
		- `background-image:url("../images/chrome.gif");`/*背景的图片*/（加引号目的 防止路径出现空格）
		- `background-repeat:no-repeat `不重复 `repeat-x` 在`x`轴重复 `repeat-y `在`y`轴重复 `repeat`重复（默认）
		- `background-position:`((`top bottom`) (`left right`) `center`)  (`100% 100%`)不常用  (`200px 300px`)常用；
		- **`background-size`**: `cover  contain` 不能跟在`background`后面；单独设置 `100% 100%`（相对于他的容器的宽高度） `100px 100px`;
		- `background-attachment:scroll(默认) fixed`(背景图片固定定位)


- **.display属性**
	- 所有的元素分为两种元素
		- a.块级元素（`display:block`）` div  p`
			- 特点：占一行，贪婪
		- b.行内元素（`display:inline`）`span   display:inline-block `既可以设置宽高又可以和行内元素一样显示 不兼容IE7以下
			- 特点：不占一行，老实
	 - **总结:**
		- `display`用来设置元素的显示的方式
			- 1.`block`
			- 2.`inline`
			- 3.`inline-block`
			- 4.`none` //隐藏


### 第三节 控制文本字体
---

- **i** 字体斜体 
- **em**(强调`seo`) 
- **i**  经常不用来做字体的倾斜 常用来做小图标
- **b** 字体加粗 `strong`(强调)


#### 控制文本
---

- 1、`text-decoration` 修饰文本  

   - `none` 默认 啥都没有
   - `underline` 下划线 a标签默认
   - `overline` 文本上面
   - ` line-through` 文本中间插一条横线
   - `blink` 让文本闪烁

- 2、`text-indent:`首行缩进 单位：`px`  `em` `mm` `cm` ` %`（相对于其父元素的宽度）

- 3、`text-align:`文本的对齐方式
    - `left `左对齐 默认
    - `rigth` 右对齐
    - `center` 居中
    - `justify` 两端对齐
		
- 4、`word-spacing`:单词间距 `+` `-` `px `
		

- 5、`letter-spacing`:字间距 `+` `-` `px`

- 6、`text-transform: capitalize `文本中每个单词首字母大写
		  - `uppercase` 大写
		  - `lowercase` 小写
		  - `none` 默认


#### 控制字体
---

- **`color`**：字体颜色 三种 
    - 第一种：`red` `blue` `green`  一般只用做测试
    - 第二种：`rgb();`不常用 `rgba()`  `css3` 背景透明
    - 第三种：十六进制 `#ffffff=#fff #000000=#000  #ffaa00 =#fa0 `常用

- **`font-family`:**"微软雅黑",Aril 

- `font-weight`字体加粗 `100` `200 ` `300` `400` `500` `600` `700` `800` `900`
     - `normal `默认值=500

      - `bold` 加粗=700

      - `bolder `更粗

      - `lighter` 更细


 - **`font-size:`** 文字的大小  偶数 `14px 2em %`基于父元素的字体的尺寸
     - `smaller`:设置为比父元素更小一级 2px

     - `largter` :设置为比父元素更大一级 2px

- **`font-style: normal`** 默认值 正常值
		
    - `italic` 文本字体倾斜 对文字、单词的正常结构有一定的倾斜改变

    - `oblique` 文本倾斜显示 仅仅是让文本正常的情况变倾斜而已


- **`line-height`**:行高；
  - `px % ` 元素必须得有高度
  - `%`基于当前字体的大小尺寸

- `font`和`background`一样 

- **`font`:设置的顺序**
	- `font-style`
	- `font-variant:small-caps` 显示小型大写字母
	- `font-weight`
	- `font-size/line-height` 常用
	- `font-family`


### 第四节 盒子模型
---

- **css盒子模型**
	- a.`padding` 内边距
		- `padding:10px`;//上下左右都是10px的内边距
		- `padding:10px 20px`;//上下10像素左右20像素内边距
		- `padding:10px 20px 30px 40px`;//上10，右20px，下30px，左40px
	- b.`border`
        -  `border-style:none` 没有边框 = `hidden`（用于表格除外，用来解决表格边框冲突）
            - solid 实现型
            - dotted 点状 
            - dashed 虚线 
            - double 双线
    - c、**`outline`** 轮廓 属性值和`border`一样

	- d.**`margin`**
		- `margin:10px;`//上下左右都是10px的外边距
		- `margin:10px 20px;`//上下10像素左右20像素外边距
		- `margin:10px 20px 30px 40px;`//上10，右20px，下30px，左40px
	- **结论**：`width`和`height`只能设置盒子中内容的高度和宽度，盒子实际的高度和宽度应该加上`border`和`padding`
	- 盒子的实际宽度= `border-left+padding-left+width+border-right+padding-right`
	
**最重要：**

- 1、行内元素的上下内外边距设置没用

	- **`margin`**:浏览器默认为没设置  `padding` 设置了但是没起到效果

-  2、外边距合并

    - a、当一个元素出现在另外一个元素上面时，第一个元素的下外边距和第二个元素的上外边距会产生合并。两个盒子之间的上下间距为大的数值

    - b、当一个子元素包含在另外一个父元素（假设没有内边距 没有边框）中时，他们的的上外边距会发生合并 也是取大的数值

### 第五节 定位与浮动

#### 定位
---

- **position**  //定位属性
	- **`static`**:默认值 静态定位 元素处于普通文档流（画板） 
	- **`relative `** //相对自己（盒子的顶点）的 可以移动（通过top和left属性）
	- **`fixed `** 固定定位 元素框从文档流删除，漂浮起来了，原来所占据的空间删除了，相对于浏览器窗口定位（通过`top、left、right、bottom`）
	   - 我们盒子有两种方式存在在浏览器中
		- 第一种方式：绘制在画板（`static`、`relative`）
		- 第二种方式：漂浮在画板之上（`fixed`、`absolute`）
	- `absolute` //绝对的漂浮定位在`body`的某个位置【`position：absolute` 也能让行内元素不用`display：block`设置宽度和高度】
	- **`z-index`** 层级 `absolute` 与`fixed`才有的属性  谁层级越高就优先显示谁
	-  **`clip:rect(上下左右)`**  裁剪`absolute`绝对定位元素框
	**结论：**
		- `position`组合使用的规律
		- 如果有个元素它的`position:absolute`的话，那么它参照的顶点
		- 就是往父容器寻找`position非static`的元素

 - 只要是盒子漂浮起来（设置了`position:fixed/absolute`或者`float`）那么 `display:block/inline` 就不需要用到 没有效果` position`优先级比`float`的高


####  浮动
---

**浮动:** 浮动的元素框不在普通文档流中，漂浮起来了 原来所占据的空间位置也被删除了


- **float\clear【没事不要乱用float】**
	- **总结：**
		- `float`的元素是漂浮
		- `float`的本质好比向左|右看齐
		- `clear`的本质就是用来换行

- **overflow**
    -  `visible`：默认值，默认显示出来
    -  `scroll:`无论内容溢出与否，都出现滚动条，基本不用
    - ` auto`:自动出现滚动，高级
    -  `hidden`:内容溢出则隐藏


### 第六节 列表标签
---

- **1、无序列表**
```html
<ul>
	<li>
		<ul>
			<li></li>
		</ul>
	</li>
	<li></li>
	<li></li>
	<li></li>
	<li></li>
</ul>
 ```
  - `list-style-type:` `none`没有` disc` 默认值 实心圆` circle`空心圆点 `square`实心方块
  - `list-style-image`:url(路劲)
  - `list-style-position`:设置前面的图标的位置 `outside` 默认值 在内容外面
                          ` inside`  在内容里
  - `list-style`:`none`;

- **2、有序列表 `ol li` 前面的图标有顺序**

  - `list-style-type`:`none` 没有 `decimal`标记是数字（默认值）

  - `list-style-position`:设置前面的图标的位置 `outside `默认值 在内容外面
                           `inside ` 在内容里


- **3、定义列表 `dl dt dd`**
  - `dt` 规定列表的项目名
  - `dd` 描述项目的内容


### 第七节 框架与表格
---

- **1、框架**
	- `iframe` 内框架 只能嵌套在`body`里面使用

	- `frameset` 框架集 不能放在`body`里面
	- `noresize="noresize"` 固定框架的大小
    - `frameborder` 框架边框
    - `name  src`   这些属性的使用和`iframe`一样
```html

	<frameset cols="50%,50%列" rows="行">
		<frame></frame>
		<frame></frame>
		<frameset>
			<frame></frame>
		</frameset>
	</frameset>
```


- **2、表格**

- `table` 逐渐被淘汰了  `ul li` 取代
- `border-collapse` 边框的样式 ：`separate` 默认值  `collapse` 边框合并
- `colspan` 合并列
- `rowspan` 合并行

```html
<table border>
    <caption></caption>//表头
    <tr>//规定行
        <th>姓名</th>//规定标题的列
        <th>年龄</th>
    </tr>
    <tr>
        <td></td>//内容的列
        <td></td>
    </tr>
    <tr>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td></td>
        <td></td>
    </tr>
</table>
 ```


### 第七节 表单
---

- **1、表单 `form`**

- `ajax`、`php/asp`   
- **`get`**方式提交：
  - 1、不安全（所有的参数会暴露在地址栏里）
  - 2、url长度是有限制

- **`post`**方式提交：
  - 1、安全性
  - 2、长度没有限制

```html
<form action="url路劲" method="get/post" target="">
		<input />//单标签 ，行内块级元素
</form>

```

- **2、单行文本框：**

```html
<input type="text" name="username" value="" id=""/>
<input type="password" name="mima" value="请输入密码" id="">
```

- **3、单选按钮：**

```html
	<input type="radio" checked=“checked”name="sex" />男    checked=“checked”选中
	<input type="radio" checked=“checked”name="sex" />女
```

- **4、多选按钮：**

``` html
<input type="checkbox" />
```


- **5、文本域：**

```html
<textarea rows="10" cols="20"></textarea>
```

- **6、文件域：**

``` html
<input type="file" name="file" id="" value="文件的地址"/>
```

- **7、`label`标签** 

```html
 	 <input type="text" name="usernmae" id="man" value=""/><label for="man">男</label>
  	 <input type="text" name="usernmae" id="man" value=""/><label for="man">男</label>
 ```
 

- **8、按钮：**

  - `<input type="button" name="" value="普通按钮"/>`

  - `<button type="">按钮</button>` 在`form`表单里面不常用，因为他的默认属性就是`submit type="submit/button/reset"`

- **9、提交按钮：**

`<input type="submit" value="提交"> 用在form表单里面`


- **10、重置按钮：**

`<input type=reset"" name="" value="重置"/>`

- **11、下拉菜单：**

```html
<select disabled="disabled" name="" id="" size="2">
		<option></option>
		<option></option>
		<option></option>
		<option></option>
	</select>
```

 - **隐藏域：**

   - `<input type="hidden" name="pass" value="123456"/>`  通常用来监控数据



