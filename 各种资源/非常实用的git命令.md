---
title: 非常实用的git命令
date: 2016-07-09 20:10:20
tags: GitHub
categories: VCS
---

### 一、前言

![enter description here][1]


---

### 二、git branch 和 git checkout

- `git branch` //查看当前分支
- `git branch -r` //列出远程分支
- `git branch -a` //列出所有分支
 
- `git branch branchName` //创建分支
- `git checkout branchName` //切换分支
- `git checkout -b branchName` //创建并切换到分支
 
- `git checkout`  //后面不跟任何参数，则就是对工作区进行检查
-  `git checkout --filename` //从暂存区中恢复文件(确保filename与branch名称不同)
 
- `git status` //查看状态

<!--more-->
---

### 三、git clone 和 git remote

- `git clone <版本库的网址> <本地目录名>`
- `git clone`支持多种协议，除了HTTP(s)以外，还支持SSH、Git、本地文件协议等，下面是一些例子。
 
- `git clone http[s]://example.com/path/to/repo.git/`
- `git clone ssh://example.com/path/to/repo.git/`
-  `git clone git://example.com/path/to/repo.git/`
-  `git clone /opt/git/project.git`
-  `git clone file:///opt/git/project.git`
-  `git clone ftp[s]://example.com/path/to/repo.git/`
- `git clone rsync://example.com/path/to/repo.git/`
 
SSH协议还有另一种写法
- `git clone [user@]example.com:path/to/repo.git/`
 
---
 
- `git remote`
- `git remote -v`  //查看远程主机的网址
- `git remote show <主机名>` //查看该主机的详细信息
- `git remote add <主机名> <网址>` //添加远程主机
- `git remote rm <主机名>`  //删除远程主机
- `git remote rename <原主机名> <新主机名>` //重命名远程主机

---

### 四、git pull 和 git push

- `git pull <远程主机名> <远程分支名>:<本地分支名>`
- `git push <远程主机名> <本地分支名>:<远程分支名>`
             

- `git pull origin master:master`
取回origin主机的master分支，与本地的master分支合并
 
- `git push origin master:master`
推送本地的master分支，与origin主机的master分支合并
 

- `git pull origin master`
如果远程分支是与当前分支合并，则冒号后面的部分可以省略。
 
- `git push origin master`
本地的master分支推送到origin主机的master分支。如果后者不存在，则会被新建
 
 
- `git pull origin`
本地的当前分支自动与对应的origin主机”追踪分支”(remote-tracking branch)进行合并。
追踪分支 是 远程的同名分支
 
- `git push origin`
当前分支与远程分支之间存在追踪关系，则本地分支和远程分支都可以省略
 
 
 
- `git pull`
当前分支自动与唯一一个追踪分支进行合并
 
- `git push`

当前分支只有一个追踪分支，那么主机名都可以省略

---

### 五、git merge 和 git rebase

- `git merge`
用"pull"命令把"origin"分支上的修改拉下来并且和你的修改合并；
结果看起来就像一个新的"合并的提交"(merge commit):
 
 
**使用 rebase 合并**

- `git checkout mywork`
- `git rebase origin`
这些命令会把你的"mywork"分支里的每个提交(commit)取消掉，
并且把它们临时 保存为补丁(patch)(这些补丁放到".`git/rebase`"目录中),
然后把"mywork"分支更新 到最新的"origin"分支，
最后把保存的这些补丁应用到"mywork"分支上
 
 
在rebase的过程中，也许会出现冲突(conflict). 在这种情况，
Git会停止rebase并会让你去解决 冲突；在解决完冲突后，
用"git-add"命令去更新这些内容的索引(index), 然后，你无需执行 `git-commit,`只要执行`:git rebase --continue`
这样git会继续应用(apply)余下的补丁。
 
在任何时候，你可以用--abort参数来终止rebase的行动，并且"mywork" 分支会回到rebase开始前的状态。
- `git rebase --abort`

![enter description here][3]


---

### 六、git log

- `git log --stat -n 5`   // 简单的列出了修改过的文件
 
- `git log -p  -n 5`  // 详细的列出修改过的文件，及提交文件的对比
 
- `git log --graph` // ASCII 字符串表示的简单图形，形象地展示了每个提交所在的分支及其分化衍合情况
- git log --all --decorate --graph
 
- `git log --pretty=oneline` // 只显示哈希值和提交说明
 
- git log --pretty=oneline/short/full/fuller/format:""(格式等)
 
- `git log --name-only`  // 仅在提交信息后显示已修改的文件清单
 
- `git log --no-merges` // 不显示merge的log
 
 
**常用的命令：**
 
- `git log --name-status -n 5 --no-merges path/filename` // 显示新增、修改、删除的文件清单(不包含merge的log)

- `git log --name-status --skip=5 -n 5 --no-merges path/filename` // 略过5条,从第6条开始取5条log

---

### 七、git stash

**保存工作现场**
 
- `git stash`     // 保存工作现场
 
do some work
 
- `git pop` // 返回工作现场
 
 
 
- `git stash list` //查看 stash 队列
 
- `git stash pop stash@{num}` 
// num就是list中要恢复的工作现场编号
// 使用pop命令恢复的工作现场，其对应的stash 在队列中删除
 
- `git stash apply stash@{num}`
// num就是list中要恢复的工作现场编号
// 使用apply命令恢复的工作现场，其对应的stash 在队列中不删除
 
 
- `git stash clear` // 情况 stash 队列

---

### 八、分支合并

**strong text**分支合并：
 
1.保持工作目录 `clean`
2.`git checkout master`  //切换到主干
3.`git merge subscribeQY`  //在主干上合并分支
4.如果有冲突就解决一下
 
`master push`前，在分支上`merge master`
然后，在master上，merge 分支，在 `push`

---

### 九、其他

- git fetch <远程主机名> <分支名>
 
- git fetch origin master
取回`origin`主机的`master`分支



### 十、参考资料

- [阮一峰Git操作][2]



  [1]: http://images2015.cnblogs.com/blog/385704/201509/385704-20150915155600929-543996061.jpg
  [2]: http://www.ruanyifeng.com/blog/2014/06/git_remote.html
  [3]: http://images2015.cnblogs.com/blog/385704/201509/385704-20150915155746492-957531481.png
  [4]: http://images2015.cnblogs.com/blog/385704/201509/385704-20150915155746492-957531481.png
