
[toc]
学习网站[https://learngitbranching.js.org/?locale=zh_CN](https://learngitbranching.js.org/?locale=zh_CN)

### 远程仓库
##### 查看远程仓库
 git remote 可以列出每一个远程服务器的简写。
 >$ git remote
origin

 你也可以指定选项`-v`，会现实需要读写的远程仓库使用Git保存的简写与其对应的URL。

 >$ git remote -v
origin https://github.com/schacon/ticgit (fetch)
origin https://github.com/schacon/ticgit (push)

#### 添加远程仓库
`git remote add <shortname> <url>` 添加一个新的远程Git仓库，同时指定一个方便使用的简写：
>\$ git remote
origin
\$ git remote add pb https://github.com/paulboone/ticgit
\$ git remote -v
origin https://github.com/schacon/ticgit (fetch)
origin https://github.com/schacon/ticgit (push)
pb https://github.com/paulboone/ticgit (fetch)
pb https://github.com/paulboone/ticgit (push)

在普通使用中，你可以使用pd 来代替整个URL。比如`git fetch pb`





