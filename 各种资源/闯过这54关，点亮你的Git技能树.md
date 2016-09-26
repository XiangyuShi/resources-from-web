---
title: 闯过这54关，点亮你的Git技能树
date: 2016-03-14 17:11:54
tags: GitHub
categories: VCS
---


**如今，Git 大行其道，颇有一统天下之势**。

如果你的技能树上 Git 和 Github的图标还没有点亮的话，你都不好意思说你是程序员。

别说互联网企业，我接触到的许多传统企业都在从 SVN，ClearCase 等迁移到 Git 上，甚至大厂还会有一个团队去定制适合自己企业的 Git 服务器。

很多人简历上写的「精通 Git 与Github」，但如果你问他熟悉到什么程度的话，回答通常是「就是会用常用的add，commit，push 操作」。

**但工作中我们会遇到一些更加复杂的场景：**
<!--more-->
* 忽略某些文件 
* 创建，删除分支
 * 找到最后修改某行代码的人
 * commit 后发现里边包含一个不应该提交的文件 
* commit 后发现少提交了一些文件 
* 一个文件中的多次有改动，怎么做到只提交其中的一部分？
 * 怎样整理提交记录使其更加整洁？ 
* 快速定位是哪一次提交引入了 bug 
* ...

作为一线程序员，我们要如何快速学习 Git 以发挥其最大威力呢？

今天我就要向大家介绍一个工具，准确说应该是「游戏」，名字叫「githug」，它把平常可能遇到的一些场景都实例化，变成一个一个的关卡，一共有 55 个关卡（以下这些你熟悉吗？）：

-  1: init
-  2: config
-  3: add
-  4: commit
-  5: clone
-  6: clone_to_folder
-  7: ignore
-  8: include
-  9: status
-  10: number_of_files_committed
-  11: rm
-  12: rm_cached
-  13: stash
-  14: rename
-  15: restructure
-  16: log
-  17: tag
-  18: push_tags
-  19: commit_amend
-  20: commit_in_future
-  21: reset
-  22: reset_soft
-  23: checkout_file
-  24: remote
-  25: remote_url
-  26: pull
-  27: remote_add
-  28: push
-  29: diff
-  30: blame
-  31: branch
-  32: checkout
-  33: checkout_tag
-  34: checkout_tag_over_branch
-  35: branch_at
-  36: delete_branch
-  37: push_branch
-  38: merge
-  39: fetch
-  40: rebase
-  41: repack
-  42: cherry-pick
-  43: grep
-  44: rename_commit
-  45: squash
-  46: merge_squash
-  47: reorder
-  48: bisect
-  49: stage_lines
-  50: find_old_branch
-  51: revert
-  52: restore
-  53: conflict
-  54: submodule
-  55: contribute


**安装**

首先我们需要来安装这个游戏，githug 是用 Ruby 编写的，可通过如下命令安装：

    gem install githug

 如果遇到权限问题，请加上sudo：
 

> sudo gem install githug

安装成功后，在 Terminal 里进入你常用的目录，输入githug，会提示游戏目录不存在，是否要创建一个，输入y然后回车：

[此处输入链接的描述][1]


  根据提示cd git_hug 进入游戏目录，准备开始游戏。
  
  **基本命令**
  
在开始前我们还需要了解游戏的一些基本操作：

 - play - 默认命令，检查是否过关
 - hint - 显示过关提示
 - reset - 重启本关，或者重启到指定的某关
 - levels - 显示关卡列表
 
 **来试一下，githug reset：**

![此处输入图片的描述][2]

**示例**
我以第一关为例子给大家演示一下玩法。

第一关的名称是：init，提示是：「一个新目录 git_hug 被创建了，请把它初始化为一个空仓库」。

假设现在我不知道该怎么过关，我可以查看过关提示：

![此处输入图片的描述][3]

指示是：「你可以输入 git 命令来查看 git 命令列表」。

![此处输入图片的描述][4]

看最后一行，原来用 git init 就可以初始化一个空仓库，接着输入 githug 进行过关检测：

![此处输入图片的描述][5]

太棒了！顺利进入第二关！
怎么样？明白了吗？后面的 54 关就靠你自己了哦！

**后语**
有了这githug游戏，再也不担心不会操作git了。

**[文章来源转载][6]**


  [1]: http://mmbiz.qpic.cn/mmbiz/meG6Vo0Mevj2pbrPwhHZl5r4fsUIQJnFzsG18hJtKX2l1WjItoRO1vicObuZCqzKQ0bIE1yLIgHV9IiaEqLXR1uQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1
  [2]: http://mmbiz.qpic.cn/mmbiz/meG6Vo0Mevj2pbrPwhHZl5r4fsUIQJnFFN5UxtBGRfSOBicSrLJ7BQs1VxCgW4kAgkibRG6iaaIPgxNYgXaXSdv9Q/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1
  [3]: http://mmbiz.qpic.cn/mmbiz/meG6Vo0Mevj2pbrPwhHZl5r4fsUIQJnFzLrprXs6SXXSopibZcAUYSDvWKAbu5U2gnkwb0ic2rpoDY2LvDqHM2Fw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1
  [4]: http://mmbiz.qpic.cn/mmbiz/meG6Vo0Mevj2pbrPwhHZl5r4fsUIQJnFop08AtGYCUzfTGwibWXSQVRTGH5yM9BicPyc1yhP8LjIiaqh0bCrFyU6A/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1
  [5]: http://mmbiz.qpic.cn/mmbiz/meG6Vo0Mevj2pbrPwhHZl5r4fsUIQJnFKYVUMfz9FvsN7txRvfokYsgrroxjs029KrWOzKicK0iaKGz1sO5x2boA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1
  [6]: http://mp.weixin.qq.com/s?__biz=MjM5MTA1MjAxMQ==&mid=401590191&idx=1&sn=099554635426602311a82429519fdc41&scene=1&srcid=01178OETHw3jwBnIUXbcSQJi#rd