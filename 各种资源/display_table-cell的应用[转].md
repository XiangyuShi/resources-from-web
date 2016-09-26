---
title: display:table-cell的应用[转]
date: 2016-09-08 00:00:08
tags: CSS
categories: Front-End
---

### display:table-cell属性简述
---

- `display:table-cell`属性指让标签元素以表格单元格的形式呈现，类似于`td`标签。目前`IE8+`以及其他现代浏览器都是支持此属性的，但是`IE6/7`只能对你说sorry了，这一事实也是大大制约了`display:table-cell`属性在实际项目中的应用
- `table-cell`同样会被其他一些`CSS`属性破坏，例如`float`, `position:absolute`，所以，在使用`display:table-cell`与`loat:left`或是`position:absolute`属性尽量不用同用。设置了`display:table-cell`的元素对宽度高度敏感，对`margin`值无反应，响应`padding`属性

<!--more-->
### display:table-cell与大小不固定元素的垂直居中
---

- 使用`display:table-cell`让大小不固定元素垂直居中已经是很老的方法了

```css
div{
  display:table-cell; 
  width:1em;
  height:1em;
  border:1px solid #beceeb; 
  font-size:144px; 
  text-align:center; 
  vertical-align:middle;
} 
div img{
  vertical-align:middle;
}
```


### display:table-cell与两栏自适应布局
---

- `display:table-cell`可以用在两栏的自适应布局上
- 对于不认识`display:table-cell`属性的IE6/7呢，使用display:inline-block属性代替`display:table-cell`就完全ok


### display:table-cell下的等高布局
---

- `table`表格中的单元格最大的特点之一就是同一行列表元素都等高。所以，很多时候，我们需要等高布局的时候，就可以借助`display:table-cell属`性
- `table`表格中的单元格最大的特点之一就是同一行列表元素都等高。所以，很多时候，我们需要等高布局的时候，就可以借助`display:table-cell属`性

---
- [ 原文出处](http://www.zhangxinxu.com/wordpress/2010/10/%E6%88%91%E6%89%80%E7%9F%A5%E9%81%93%E7%9A%84%E5%87%A0%E7%A7%8Ddisplaytable-cell%E7%9A%84%E5%BA%94%E7%94%A8/)
