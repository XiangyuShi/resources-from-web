---
title: javascript工具函数
date: 2016-09-18 23:21:00
tags: 
   - Javascript
   - Snippet
categories: Front-End
---

### 第一部分 JavaScript工具函数
---

#### 转义特殊字符为html实体
---

```javascript
    HtmlEncode: function(str){
        return str.replace(/&/g, '&amp;').replace(/\"/g, '&quot;').replace(/</g, '&lt;').replace(/>/g, '&gt;').replace(/'/g, '&apos;');
    },
```
<!--more-->
#### 验证是否为有效的手机电话号码
---

```javascript
    IsMobile: function(str){
        var rp = /^1[3|4|5|7|8][0-9]\d{4,8}$/;
        return rp.test(str);
    },
```
#### 验证是否为有效的座机电话号码
---

```javascript
    IsTel: function(str){
        var rp = /^([0-9]{3,4}-)?[0-9]{7,8}$/;
        return rp.test(str);
    },
```
#### 清除左空格/右空格
---

```javascript
    Ltrim: function(str){ return str.replace( /^(\s*|　*)/, ""); },
    Rtrim: function(str){ return str.replace( /(\s*|　*)$/, ""); },
```

#### 清除左右空格
---

```javascript
    Trim: function(str){
        return this.Ltrim(this.Rtrim(str));
    },
 ```
#### 判断是那种类型的浏览器
---

```javascript
    WhichBrowser: function(){
        var userAgent = navigator.userAgent;

        var isOpera = userAgent.indexOf("Opera") > -1;
        var isIE = userAgent.indexOf("compatible") > -1 && userAgent.indexOf("MSIE") > -1 && !isOpera;
        var isFF = userAgent.indexOf("Firefox") > -1;
        var isCH = userAgent.indexOf("Chrome") > -1;
        var isSafari = userAgent.indexOf("Safari") > -1;
 
        if (isIE){
            var IE5 = IE55 = IE6 = IE7 = IE8 = false;
            var reIE = new RegExp("MSIE (\\d+\\.\\d+);");
            reIE.test(userAgent);
            var fIEVersion = parseFloat(RegExp["$1"]);
            IE55 = fIEVersion == 5.5;
            IE6 = fIEVersion == 6.0;
            IE7 = fIEVersion == 7.0;
            IE8 = fIEVersion == 8.0;
            if (IE55) {
                return "IE55";
            }
            if (IE6) {
                return "IE6";
            }
            if (IE7) {
                return "IE7";
            }
            if (IE8) {
                return "IE8";
            }
        }
 
        if (isFF) {
            return "Firefox";
        }
        if (isCH) {
            return "Chrome";
        }
        if (isOpera) {
            return "Opera";
        }
        if (isSafari) {
            return "Safari";
        }
    },
 ```
#### 获取客户端浏览器cookie
---

```javascript
    GetCookie: function(c_name){
        if(document.cookie.length>0){
            c_start = document.cookie.indexOf(c_name + '=');
            if(c_start != -1){
                c_start = c_start + c_name.length + 1;
                c_end = document.cookie.indexOf(';',c_start);
                if (c_end==-1) c_end = document.cookie.length;
                return unescape(document.cookie.substring(c_start,c_end));
            }
        }
        return '';
    },
 ```
 
#### 设置客户端浏览器cookie
---

```javascript
    SetCookie: function(c_name, value, expiredays){
        var exdate = new Date();
        exdate.setDate(exdate.getDate() + expiredays);
        document.cookie = c_name + "=" + escape(value) + ((expiredays==null) ? "" : ";expires="+exdate.toGMTString());
    },
};
```

### 第二部分 插件工具
---

#### Dialog对话框

```javascript
;(function($){
    var DialogBox = function(options){
        this.defaults = {
            'height': 350,
            'width': 500,
            'title': '',
            'content': '',
            'action': ''
        };
        this.options = $.extend(this.defaults,options);
    };
 
    DialogBox.prototype = {
 
        mask: '',
        dialogBox: '',
 
        close: function(){
            var self = this;
            self.mask.remove();
            self.dialogBox.remove();
        },
 
        resize: function(){
            var self = this;
            var w_h = $(window).height();
            var w_w = $(window).width();
 
            var pos_l = w_w/2-self.defaults.width/2;
            var pos_t = w_h/2-self.defaults.height/2;
            self.dialogBox.css({
                'top': pos_t,
                'left': pos_l
            });
        },
 
        init: function(){
            var self = this;
 
            // mask
            var d_w = $(document).width();
            var d_h = $(document).height();
            var w_h = $(window).height();
            var w_w = $(window).width();
 
            var mask = $('<div class="dialog-mask"></div>');
            mask.css({
                'height': d_h,
                'width': d_w
            });
 
            // dialog-box
            var dialog_out = $('<div class="dialog-out"></div>');
            var pos_l = w_w/2-self.defaults.width/2;
            var pos_t = w_h/2-self.defaults.height/2;
            dialog_out.css({
                'height': self.defaults.height,
                'width': self.defaults.width,
                'top': pos_t,
                'left': pos_l
            });
 
            // insert html
            var inner = $('<div class="dialog-inner"></div>');
            inner.html(self.defaults.content);
            dialog_out.append(inner);
 
            // close-btn
            var close = $('<div class="close-btn" title="关闭"></div>');
            close.click(function(){
                self.close();
            });
            dialog_out.append(close);
 
            // action-btn
            var action_btn = $('<button class="action-btn ibtn">确认</button>');
            dialog_out.append(action_btn);
            if(typeof self.defaults.action === 'function'){
                action_btn.click(function(){
                    self.defaults.action();
                });
            }else{
                action_btn.click(function(){
                    self.close();
                });
            }
 
            // add to body
            $(document.body).append(dialog_out);
            $(document.body).append(mask);
 
            self.mask = mask;
            self.dialogBox = dialog_out;
 
            window.onresize = function(){
                self.resize();
            };
 
            return self;
        }
    };
 
    $.fn.deYuanDialog = function(options){
        var dialog = new DialogBox(options);
        return dialog.init();
    };
})(jQuery);
```

#### Tips
---

```javascript
;(function($){
    var Tip = function(element,options){
        this.element = element;
        this.defaults = {
            'height': 27,
            'width': 150,
            'content': '温馨提示',
            'background-color': '#000000',
        };
        this.options = $.extend(this.defaults,options);
    };
 
    Tip.prototype = {
 
        hide: function(){
            //$(self.element).remove();
        },
 
        init: function(){
            var self = this;
            var element = self.element;
            var pos_l = element.offset().left;
            var pos_t = element.offset().top;
 
            var tip_out = $('<div class="tip-out"><span class="tip-arrow"></span></div>');
            var tip_body = $('<div class="tip-body"></div>');
            tip_body.html(self.defaults.content);
            tip_out.append(tip_body);
            tip_out.css({
                'left': pos_l,
                'top': pos_t - self.defaults.height - 13,
            }).show();
            $(document.body).append(tip_out);
 
            function hide(){
                tip_out.stop().fadeOut('slow',function(){tip_out.remove();});
            }
 
            setTimeout(hide,3000);
 
            return self;
        }
    };
 
    $.fn.deYuanTip = function(options){
        var tip = new Tip(this,options);
        return tip.init();
    };
})(jQuery);
```

#### Banner
---

```javascript
;(function($){
 
    var Scrolling = function(element,options){
        this.element = element;
        this.defaults = {
            'height': 400,  // 默认高度
            'interval': 3000    // 默认时间间隔ms
        };
        this.options = $.extend(this.defaults,options);
    };
 
    Scrolling.prototype = {
        d_w : 0,    // 浏览器宽度
        sort: 0,    // 图片顺序
        count : 0,  // 图片数量
 
        // 分页按钮
        scrollBtn: function(i){
            var step = parseInt(i) ? parseInt(i) : 0;
            var self = this;
            var element = $(self.element);
            var banner = element.find('.banner-inner');
 
            banner.stop().animate({
                'left': -self.d_w * step
            });
 
            return this;
        },
 
        // 初始化
        init: function(){
            var self = this;
            var element = $(self.element);
            self.d_w = $(document).width();
 
            var inner = element.find('.banner-inner');
            var a = inner.find('a');
            self.count = a.length - 1;
            //设置包裹容器高宽
            var wrap = element.find('.banner-img');
            wrap.css({
                'height': self.defaults.height,
                'width': self.d_w
            });
            // 设置内容器高宽
            inner.css({
                'height': self.defaults.height,
                'width': (self.count+1) * self.d_w
            });
            // 设置内容高宽
            a.css({
                'height': self.defaults.height,
                'width': self.d_w
            });
            // 设置btn点击事件
            var pages = element.find('li');
            pages.each(function(i){
                var page = $(this);
                page.on('mousedown',function(){
                    pages.removeClass('page-active');
                    $(this).addClass('page-active');
                    self.sort = i;
                    self.scrollBtn(self.sort);
                });
            });
            var btns = element.find('.banner-btn');
            btns.remove();
            var len = pages.length;
            btns.each(function(){
                var btn = $(this);
                btn.on('mousedown',function(){
                    var left = $(this).hasClass('left-btn');
                    var right = $(this).hasClass('right-btn');
                    if(left){
                        if(self.sort < len - 1){
                            self.sort += 1;
                        }
                        self.scrollBtn(self.sort);
                        pages.removeClass('page-active');
                        pages.eq(self.sort).addClass('page-active');
                    }
                    if(right){
                        if(self.sort > 0){
                            self.sort -= 1;
                        }
                        self.scrollBtn(self.sort);
                        pages.removeClass('page-active');
                        pages.eq(self.sort).addClass('page-active');
                    }
                });
            });
 
            // 当窗口改变大小时重新初始化banner
            window.onresize = function(){
                self.init();
            };
 
            return this;
        },
 
        // 自动播放
        scrollAuto: function(){
            var self = this;
            var banner = $(self.element).find('.banner-inner');
            var element = $(self.element);
            var btns = element.find('li');
            function scroll(){
                if(self.sort <= self.count){
                    banner.stop().animate({
                        'left': (-self.d_w * self.sort)
                    });
 
                    btns.removeClass('page-active');
                    btns.eq(self.sort).addClass('page-active');
 
                    self.sort++;
                }else{
                    self.sort = 0;
                    banner.stop().animate({
                        'left': 0
                    });
                }
            }
            setInterval(scroll, self.defaults.interval);
        }
    };
 
    $.fn.deYuanBanner = function(options){
        var scrolling = new Scrolling(this, options);
        scrolling.init().scrollAuto();
    }
})(jQuery);
```

#### GotoTop
---

- 当窗口滚动大于300px时出现回底部按钮

```javascript
    var gotop = $('<div class="go-to-top" title="回到顶部"></div>');
    $(document.body).append(gotop);
    $(window).scroll(function(){
        if($(window).scrollTop()>300){
            gotop.fadeIn('fast');
        }else{
            gotop.fadeOut('fast');
        }
    });
    gotop.click(function(){
        $('body,html').animate({scrollTop:0},1000);
    });
```

#### 判断用户是否用低版本的IE浏览器访问网页，如是，则提醒升级
---

```javascript
var oldIE = new Array('IE55','IE6','IE7','IE8');
    var browser = $Dy.WhichBrowser();
    if(oldIE.toString().indexOf(browser)>-1){
        function append(){
            var old_browser = $('<div class="old-browser">您的浏览器版本过低，为您让您获得更好的浏览体验，请您升级至高版本浏览器，如IE10，Firefox，Chrome。</div>');
            var close = $('<span class="old-close" title="关闭">×</span>');
            old_browser.append(close);
            $(document.body).prepend(old_browser);
            old_browser.fadeIn();
 
            close.click(function(){
                $Dy.SetCookie('old_browser_warn',true,1);
                old_browser.remove();
            });
        }
 
        var is_close = $Dy.GetCookie('old_browser_warn');
        if(is_close.length===0){
            setTimeout(append,2000);
        }
    }
 ```



