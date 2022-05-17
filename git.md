
- [起步](#起步)
  - [关于版本控制](#关于版本控制)
    - [本地版本控制系统](#本地版本控制系统)
    - [集中式的版本控制系统](#集中式的版本控制系统)
    - [分布式版本控制系统](#分布式版本控制系统)
  - [Git 简史](#git-简史)
  - [Git 是什么](#git-是什么)
    - [直接记录快照，而非差异比较](#直接记录快照而非差异比较)
    - [几乎所有的操作都是本地执行](#几乎所有的操作都是本地执行)
    - [Git 保证完整性](#git-保证完整性)
    - [Git 一般只添加数据](#git-一般只添加数据)
    - [三种状态](#三种状态)
  - [初次运行Git 前的配置](#初次运行git-前的配置)
    - [用户信息](#用户信息)
    - [文本编辑器](#文本编辑器)
    - [检查配置信息](#检查配置信息)
  - [获取帮助](#获取帮助)
- [Git 基础](#git-基础)
  - [获取 Git 仓库](#获取-git-仓库)
    - [初始化已存在的目录](#初始化已存在的目录)
    - [克隆现有仓库](#克隆现有仓库)
  - [记录每次更新到仓库](#记录每次更新到仓库)
    - [检查当前文件的状态](#检查当前文件的状态)
    - [跟踪新文件](#跟踪新文件)
    - [暂存已修改的文件](#暂存已修改的文件)
    - [状态简览](#状态简览)
    - [忽略文件](#忽略文件)
    - [查看已暂存和未暂存的修改](#查看已暂存和未暂存的修改)
    - [提交更新](#提交更新)
    - [跳过使用暂存曲序](#跳过使用暂存曲序)
    - [移除文件](#移除文件)
    - [移动文件](#移动文件)
  - [查看历史提交](#查看历史提交)
    - [限制输出长度](#限制输出长度)
  - [撤销操作](#撤销操作)
    - [取消暂存的文件](#取消暂存的文件)
    - [撤销对文件的修改](#撤销对文件的修改)
  - [远程仓库的使用](#远程仓库的使用)
    - [查看远程仓库](#查看远程仓库)
    - [添加远程仓库](#添加远程仓库)
    - [从远程仓库中抓取与拉取](#从远程仓库中抓取与拉取)
    - [推送到远程仓库](#推送到远程仓库)
    - [查看某个远程仓库](#查看某个远程仓库)
    - [远程仓库的重命名与移除](#远程仓库的重命名与移除)
  - [打标签](#打标签)
    - [列出标签](#列出标签)
    - [创建标签](#创建标签)
    - [附注标签](#附注标签)
    - [轻量标签](#轻量标签)
    - [后期打标签](#后期打标签)
    - [共享标签](#共享标签)
    - [删除标签](#删除标签)
    - [检出标签](#检出标签)
  - [Git 别名](#git-别名)
- [Git 分支](#git-分支)
  - [分支简介](#分支简介)
    - [分支创建](#分支创建)
    - [分支切换](#分支切换)
  - [分支的新建与合并](#分支的新建与合并)
    - [新建分支](#新建分支)
    - [分支的合并](#分支的合并)
    - [遇到冲突时的分支合并](#遇到冲突时的分支合并)
  - [分支管理](#分支管理)
  - [分支工作流](#分支工作流)
    - [长期分支](#长期分支)
    - [主题分支](#主题分支)
  - [远程分支](#远程分支)
    - [推送](#推送)
    - [跟踪分支](#跟踪分支)
    - [拉取](#拉取)
    - [删除远程分支](#删除远程分支)
  - [变基](#变基)
    - [变基的基本操作](#变基的基本操作)
    - [更有趣的变基例子](#更有趣的变基例子)
    - [变基的风险](#变基的风险)
    - [用变基解决编辑](#用变基解决编辑)
- [服务器上的 Git](#服务器上的-git)
  - [协议](#协议)
    - [本地协议](#本地协议)
    - [HTTP 协议](#http-协议)
      - [智能 HTTP 协议](#智能-http-协议)
    - [SSH 协议](#ssh-协议)
    - [Git 协议](#git-协议)
- [分布式 Git](#分布式-git)
  - [分布式工作流程](#分布式工作流程)
    - [集中式工作流](#集中式工作流)
    - [集成管理者工作流](#集成管理者工作流)
    - [主管与副主管工作流](#主管与副主管工作流)
  - [向一个项目共享](#向一个项目共享)
    - [提交准则](#提交准则)
- [Git 工具](#git-工具)
  - [选择修订版本](#选择修订版本)
    - [简短的 SHA-1](#简短的-sha-1)
    - [分支引用](#分支引用)
    - [引用日志](#引用日志)
    - [祖先引用](#祖先引用)
    - [提交区间](#提交区间)
      - [双点](#双点)
      - [多点](#多点)
      - [三点](#三点)
  - [交互式暂存](#交互式暂存)
    - [暂存与取消暂存文件](#暂存与取消暂存文件)
    - [暂存补丁](#暂存补丁)
    - [贮藏与清理](#贮藏与清理)
    - [贮藏工作](#贮藏工作)
    - [从贮藏中创建一个分支](#从贮藏中创建一个分支)
    - [清理工作目录](#清理工作目录)
  - [搜索](#搜索)
    - [Git Grep](#git-grep)
    - [Git 日志搜索](#git-日志搜索)
      - [行日志搜索](#行日志搜索)
  - [重写历史](#重写历史)
    - [修改最后一次提交](#修改最后一次提交)
    - [修改多个提交信息](#修改多个提交信息)
    - [重新排序提交](#重新排序提交)
    - [压缩提交](#压缩提交)
    - [拆分提交](#拆分提交)
    - [核武级选项：filter-branch](#核武级选项filter-branch)
      - [从每一个提交中移除一个文件](#从每一个提交中移除一个文件)
      - [使一个子目录作为新的根目录](#使一个子目录作为新的根目录)
      - [全局修改邮箱地址](#全局修改邮箱地址)
  - [重置揭秘](#重置揭秘)
      - [三棵树](#三棵树)
      - [HEAD](#head)
      - [索引](#索引)
      - [工作目录](#工作目录)
    - [工作流程](#工作流程)
    - [重置的作用](#重置的作用)
      - [第一步：移动 HEAD](#第一步移动-head)
      - [第二步：更新索引（--mixed）](#第二步更新索引--mixed)
      - [第三步：更新工作目录（--hard）](#第三步更新工作目录--hard)
      - [回顾](#回顾)
    - [通过路径来重置](#通过路径来重置)
    - [压缩](#压缩)
    - [检出](#检出)
      - [不带路径](#不带路径)
      - [带路径](#带路径)
    - [总结](#总结)
  - [高级合并](#高级合并)
    - [合并冲突](#合并冲突)
    - [中断合并](#中断合并)
    - [忽略空白](#忽略空白)
    - [手动文件在合并](#手动文件在合并)
    - [检出冲突](#检出冲突)
    - [合并日志](#合并日志)
    - [组合式差异格式](#组合式差异格式)
    - [撤销合并](#撤销合并)
      - [修复引用](#修复引用)
      - [还原提交](#还原提交)
    - [其他类型的合并](#其他类型的合并)
      - [我们或他们的偏好](#我们或他们的偏好)
      - [子树合并](#子树合并)
  - [Rerere](#rerere)
[toc]
简单的学习网站
[https://learngitbranching.js.org/?locale=zh_CN](https://learngitbranching.js.org/?locale=zh_CN)
## 起步
本章为 Git 入门。 我们从介绍版本控制工具的背景知识开始，然后讲解如何在你的系统上运行 Git，最后是关于如何设置 Git 以便开始工作。 通过本章的学习，你应该能了解为什么 Git 这么流行，为什么你应该使用 Git 以及你应该如何设置以便使用 Git。
### 关于版本控制
版本控制是一种记录一个或若干文件内容变化，以便将来查阅特定版本修订情况的系统。你可以对任何类型的文件进行版本控制。

有了它你就可以将选定的文件回溯到之前的状态，甚至将整个项目都回退到过去某个时间点的状态，你可以比较文件的变化细节，查出最后是谁修改了哪个地方，从而找出导致怪异问题出现的原因，又是谁在何时报告了某个功能缺陷等等。 使用版本控制系统通常还意味着，就算你乱来一气把整个项目中的文件改的改删的删，你也照样可以轻松恢复到原先的样子。 但额外增加的工作量却微乎其微。
![local](https://git-scm.com/book/en/v2/images/local.png)

#### 本地版本控制系统
可以记录变更，但是无法协作。

#### 集中式的版本控制系统
集中化的版本控制系统（Centralized Version Control Systems，简称 CVCS）。这类系统，诸如 CVS、Subversion 以及Perforce 等，都有一个单一的集中管理的服务器，保存所有文件的修订版本，而协同工作的人们都通过客户端连到这台服务器，取出最新的文件或者提交更新。 
![centralized](https://git-scm.com/book/en/v2/images/centralized.png)

好处是可以共享项目和变更记录，权限管理轻松。坏处是一旦中心系统故障，导致所有电脑无法仅能读取本地镜像，无法提交，无法协同。而且所有提交存于一处，始终有丢失记录的风险。

#### 分布式版本控制系统
（Distributed Version Control System，简称 DVCS）
 在这类系统中，像Git、Mercurial、Bazaar 以及 Darcs 等，客户端并不只提取最新版本的文件快照， 而是把代码仓库完整地镜像下来，包括完整的历史记录。 这么一来，任何一处协同工作用的服务器发生故障，事后都可以用任何一个镜像出来的本地仓库恢复。 因为每一次的克隆操作，实际上都是一次对代码仓库的完整备份。



![distributed](https://git-scm.com/book/en/v2/images/distributed.png)

让本地仓库和远程仓库接触耦合。更进一步，许多这类系统都可以指定和若干不同的远端代码仓库进行交互。

### Git 简史
起于一场linux 被卡脖子的经历，linux 技术人表示不服，于是有了git。
git 的目标：
- 速度
- 简单的设计
- 对非线性开发模式的强力支持（允许成千上万个并行开发的分支）
- 完全分布式
- 有能力高效管理类似 Linux 内核一样的超大规模项目（速度和数据量）
  
### Git 是什么
尽管 Git 用起来与其它的版本控制系统非常相似， 但它在对信息的存储和认知方式上却有很大差异，理解这些差异将有助于避免使用中的困惑。

#### 直接记录快照，而非差异比较

git 和其他版本控制对待数据的方式不同，其他版本控制基于差异（delta-based)
![deltas](https://git-scm.com/book/en/v2/images/deltas.png)

而git基于快照，对于每一次提交，会创建快照并保存索引。没有变化，则不在存储，保留一个引用指向之前的文件。
![snapshots](https://git-scm.com/book/en/v2/images/snapshots.png)

git 更像是一个小型的文件系统。

#### 几乎所有的操作都是本地执行
这样首先速度很快，而且由于缓存在本地，工作不依赖于网络，随时可以提交。只要最终能和网络同步就能和其他人协作。

#### Git 保证完整性
所有数据在存储之前都参加校验和，然后以校验和来引用。难以修改且高度安全。保存的信息都是以sha-1哈希校验和来作为索引。
#### Git 一般只添加数据
git 几乎不会执行任何可能导致文件不可恢复的操作。可以随意尝试，而没有任何风险。
#### 三种状态
Git 有三种状态，你的文件可能处于其中之一： **已提(committed)、已修改(modified) 和 已暂存(staged)**。
- 已修改表示修改了文件，但还没保存到数据库中。
- 已暂存表示对一个已修改文件的当前版本做了标记，使之包含在下次提交的快照中。
- 已提交表示数据已经安全地保存在本地数据库中。

这让Git项目有三个阶段：**工作区、暂存区以及Git目录**
![areas](https://git-scm.com/book/en/v2/images/areas.png)

工作区是对项目的某个版本独立提取出来的内容。 这些从 Git 仓库的压缩数据库中提取出来的文件，放在磁盘上供你使用或修改。

暂存区是一个文件，保存了下次将要提交的文件列表信息，一般在 Git 仓库目录中。 按照 Git 的术语叫做“索引”，不过一般说法还是叫“暂存区”。

Git 仓库目录是 Git 用来保存项目的元数据和对象数据库的地方。 这是 Git 中最重要的部分，从其它计算机克隆仓库时，复制的就是这里的数据。

基本流程：
1. 在工作区中修改文件。
2. 将你想要下次提交的更改选择性地暂存，这样只会将更改的部分添加到暂存区。
3. 提交更新，找到暂存区的文件，将快照永久性存储到 Git 目录。
   
如果 Git 目录中保存着特定版本的文件，就属于 **已提交** 状态。 如果文件已修改并放入暂存区，就属于 **已暂存** 状态。 如果自上次检出后，作了修改但还没有放到暂存区域，就是 **已修改** 状态。

### 初次运行Git 前的配置
Git 自带一个 `git config` 的工具来帮助设置控制 Git 外观和行为的配置变量。 这些变量存储在三个不同的位置：
1. `/etc/gitconfig` 文件: 包含系统上每一个用户及他们仓库的通用配置。 如果在执行 `git config` 时带上`--system` 选项，那么它就会读写该文件中的配置变量。 （由于它是系统配置文件，因此你需要管理员或超级用户权限来修改它。）
2. `~/.gitconfig 或` `~/.config/git/config` 文件：只针对当前用户。 你可以传递 `--global` 选项让 Git读写此文件，这会对你系统上 所有 的仓库生效。
3. 当前使用仓库的 Git 目录中的 config 文件（即 `.git/config`）：针对该仓库。 你可以传递 `--local` 选项让 Git 强制读写此文件，虽然默认情况下用的就是它。。 （当然，你需要进入某个 Git 仓库中才能让该选
项生效。）

每一个级别会覆盖上一级别的配置，所以 `.git/config` 的配置变量会覆盖 `/etc/gitconfig` 中的配置变量。

在 Windows 系统中，Git 会查找 $HOME 目录下（一般情况下是 C:\Users\$USER ）的 .gitconfig 文件。Git 同样也会寻找 /etc/gitconfig 文件，但只限于 MSys 的根目录下，即安装 Git 时所选的目标位置。

你可以通过以下命令查看所有的配置以及它们所在的文件：
>\$ git config --list --show-origin

#### 用户信息

安装完 Git 之后，要做的第一件事就是设置你的用户名和邮件地址。 这一点很重要，因为每一个 Git 提交都会使用这些信息，它们会写入到你的每一次提交中，不可更改：

>\$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com

再次强调，如果使用了 `--global` 选项，那么该命令只需要运行一次，因为之后无论你在该系统上做任何事情， Git 都会使用那些信息。 当你想针对特定项目使用不同的用户名称与邮件地址时，可以在那个项目目录下运行没有 `--global` 选项的命令来配置。

#### 文本编辑器

如果没有配置，则使用系统默认文本编辑器。
如果你向使用不同的文本编辑器，可以这样：
>$ git config --global core.editor emacs

#### 检查配置信息
使用`git config --list` 列出Git 当时能找到的配置。
>$ git config --list
user.name=John Doe
user.email=johndoe@example.com
color.status=auto
color.branch=auto
color.interactive=auto
color.diff=auto
...

你可能会看到重复的变量名， 因为Git 会从不同的文件中读取同一个配置(`/etc/gitconfig`,`~/.gitconfig`)。git 会使用最后一个配置。

你可以使用 `git config <key>` 查找具体项配置
>$ git config user.name
John Doe

由于 Git 会从多个文件中读取同一配置变量的不同值，因此你可能会在其中看到意料之外的值而不知道为什么。 此时，你可以查询 Git 中该变量的 原始 值，它会告诉你哪一个配置文件最后设置了该值：
>$ git config --show-origin rerere.autoUpdate
file:/home/johndoe/.gitconfig false

### 获取帮助

三种方式等价：
>\$ git help \<verb\>
\$ git \<verb\> --help
\$ man git-\<verb\>

比如想要获得`git config` 命令手册，执行
>$ git help config

这些命令无需联网。也可以使用`-h`获得更加简明的"help"
>\$ git add -h 

## Git 基础
核心章节，git 的基本使用。

### 获取 Git 仓库

通常使用两种方式获取 Git 项目:
1. 将尚未进行版本控制的本地目录转换为 Git 仓库。
2. 从其它服务器 **克隆** 一个已存在的 Git 仓库。

#### 初始化已存在的目录

> cd 文件目录
> git init

该命令会创建一个名为 `.git` 的子目录，这是 Git 仓库的骨干。但此时，项目里的文件并没有被跟踪。

你可以使用`git add` 命令来指定所需文件的追踪，然后执行 `git commit`:
> git add *.c
> git add LICENSE
> git cimmit -m 'init'

#### 克隆现有仓库
`git clone <url>` 不同于 checkout， 默认配置下远程 Git 仓库中的每一个文件的每一个版本都被拉了下来。

会在当前目录创建一个 "project_name" 的目录，并初始化`.git`文件夹，并取出所有版本放入`.git`。

可以重新命名：
> git clone \<url\> project_name

同时支持 https,git,ssh

### 记录每次更新到仓库
项目文件分为**已跟踪** 和 **未跟踪**。

对于跟踪文件，你可以选择性的将这些修改过的文件放入暂存区，然后提交所有已暂存的修改，如此反复。
![lifcycle](https://git-scm.com/book/en/v2/images/lifecycle.png)

#### 检查当前文件的状态

可以使用`git status` 查看哪些文件处于什么状态。
>git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working directory clean

这说明工作目录相当干净。上次提交后都未被修改过。同时也说明了没有出现未被跟踪的新文件，否则会被罗列出来。最后，还显示了当前所在分支，并且对应远程服务器分支没有偏离。分支名默认未 "master"。

现在创建一个 `README`文件，使用`git status`查看状态：
>echo 'tool-note' > README
>git status
On branch master
Your branch is up to date with 'origin/master'.
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README
 >       
>no changes added to commit (use "git add" and/or "git commit -a")

可以看见 `README` 出现在了 `untracked files` 下面。未跟踪的文件意味着 Git 在之前的快照（提交）中没有这些文件；Git 不会自动将之纳入跟踪范围，除非你明明白白地告诉它“我需要跟踪该文
件”。 这样的处理让你不必担心将生成的二进制文件或其它不想被跟踪的文件包含进来。 不过现在的例子中，我们确实想要跟踪管理 README 这个文件。

#### 跟踪新文件

使用`git add` 开始跟踪一个文件。
> git add README

此时在运行 `git status` 会看到 `README` 文件已经被跟踪，并处于暂存状态：
>On branch master
Your branch is up to date with 'origin/master'.
>
>Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   README

只要在 `Changes to be committed` 这下面，就说明已经是暂存状态。 `git add` 命令使用文件或目录的路径作为参数；如果参数是目录的路径，该命令将递归地跟踪该目录下的所有文件。

#### 暂存已修改的文件

我们修改一个被跟踪的文件，然后`git status`：
>git status
On branch master
Your branch is up to date with 'origin/master'.
>
>Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   README
>
>Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   git.md

文件出现在 `Change not staged for commit` 下面，这说明跟踪文件发生了变化，但还没有放入暂存区。此时使用`git add` 可以将修改结果放入暂存区。将这个明林理解为”精确的将内容添加到下一次提交中“ 而不是”将一个文件添加到项目中" 比较合适。使用 `git add git.md` 之后在 使用`git status`:
>git status
On branch master
Your branch is up to date with 'origin/master'.
>
>Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   README
        modified:   git.md

文件都已经被缓存。此时在修改`git.md` 然后在 `git status`:
>On branch master
Your branch is up to date with 'origin/master'.
>
>Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   README
        modified:   git.md
>
>Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   git.md

`git.md` 出现在两个地方。实际上 Git 只不过暂存了你运行 `git add` 命令时的版本。如果你提交，提交的也是最后一次 `git add`的版本，所以，`git add` 之后的所有修改，只有再次运行`git add` 才能够放入暂存区。

#### 状态简览

`git status` 的状态有些繁琐。可以使用 `git status -s` 或者 `git status --short` 得到一种更为紧凑的输出。
>  git status -s
><pre>A  README
>MM git.md
>?? LICENSE.txt</pre>

`??` 表示未跟踪，`A` 表示 新添加到暂存区，修改的标记未`M`。输出中有两栏，左侧指明了暂存区状态，右栏指明了工作区的状态。

#### 忽略文件

很多文件无需纳入 Git 管理，也不希望他们总出现在跟踪文件列表。通常都是一些自动生成的文件，或者临时创建的文件。这时，我们需要创建一个 `.gitingnore` 文件，列出需要忽略的文件。
>cat .gitignore
>*.[oa]

要养成一开始就为你的新仓库设置好`.gitignore` 文件的习惯，以免将来误提交这类无用的文件。

`.gtiignore` 格式规范如下：
- 所有空行或者以 # 开头的行都会被 Git 忽略。
- 可以使用标准的 glob 模式匹配，它会递归地应用在整个工作区中。
- 匹配模式可以以（/）开头防止递归。
- 匹配模式可以以（/）结尾指定目录。
- 要忽略指定模式以外的文件或目录，可以在模式前加上叹号（!）取反。
  
所谓的 glob 模式是指 shell 所使用的简化了的正则表达式。

>GitHub 有一个十分详细的针对数十种项目及语言的 .gitignore 文件列表， 你可以在https://github.com/github/gitignore 找到它。

>在最简单的情况下，一个仓库可能只根目录下有一个 .gitignore 文件，它递归地应用到整个仓库中。 然而，子目录下也可以有额外的 .gitignore 文件。子目录中的 .gitignore文件中的规则只作用于它所在的目录中。 （Linux 内核的源码库拥有 206 个 .gitignore 文件。）多个 .gitignore 文件的具体细节超出了本书的范围，更多详情见 man gitignore 。

#### 查看已暂存和未暂存的修改

`git status` 的信息有些时候相对简略，如果想看到更加详细的信息，可以使用`git diff`，此命令比较的是工作目录中当前文件和暂存区域的快照之间的差异。也就是修改之后还没暂存起来的变化内容。

如果要查看已暂存的和最后一次提交的文件差异，可以使用`git diff --staged`。`git diff --staged` 和 `git diff --cached` 是同义词。




  






#### 提交更新

提交命令 `git commit` ，更加详细的内容修改提示可以使用`-v` 查看，这回将你所作的更改的 diff 输出呈现在编辑器中。

你也可以在`commit` 后面添加`-m` 选项，将提交信息命令放在同一行。

#### 跳过使用暂存曲序

可以使用`git commit` 加上`-a` 参数, Git 将自动跟踪的文件暂存并一起提交，从而跳过`git add` 步骤。



#### 移除文件

要从 Git 中移除某个文件，就必须要从已跟踪文件清单中移除（确切的说，是从暂存区移除），然后提交。可以使用`git rm` 命令完成，并且从工作区删除。

如果只是简单的手工删除文件，运行`git status` 时就会在 "Changes not staged for commit" 看见 deleted。然后在运行 `git rm` 记录此次移除文件的操作。

下一次提交时，该文件不在纳入版本管理。如果删除之前修改过或者已经放入了暂存区，必须使用`-f` 。删除的文件无法恢复。

另一种情况，我们只想删除 Git 仓库中，并且不再继续追踪，比如忘记添加`.gitignore`，可以使用`--cached` 选项。

`git rm ` 可以使用 `glob` 通配符模式。
>git rm log/\*.log


**这里我不太明白，使用`git add` 不是也能够把删除操作保存进暂存区吗？此操作的优势在哪里？**


#### 移动文件

`git mv file_from file_to` 可以对文件进行重命名。
>git mv README READE.md

其实他相当于三条命令
>mv READEME README.md
>git rm README
>git add README.md



### 查看历史提交

`git log` 可以查看历史提交。 
`-p` 或者`--patch` 会现实每次提交所引入的差异（按补丁的格式输出。
可以使用 `-2` 来现实最近的两次提交。
可以使用`--stat` 来查看每次提交的简略统计。
可以使用`--pretty`。可以使用各种格式展示历史。`oneline` 展示一行提交信息。`short`,`full`,`fuller` 格式基本一致，但详尽程度不一。`format` 可以定制格式。
>git log --pretty=format:"%h - %an, %ar : %s"

常用选项
| 选项 | 说明|
|------|----|
|%H| 提交完整的哈希值|
|%h| 提交简写的哈希值|
|%T | 树的完整哈希值|
|%t | 树的简写哈希值|
|%P | 父提交的完整哈希值|
|%p  | 父提交的简写哈希值|
|%an  | 作者名字|
|%ae  | 作者的电子邮件地址|
|%ad | 作者修订日期（可以用 --date=选项 来定制格式）|
|%ar  | 作者修订日期，按多久以前的方式显示|
|%cn | 提交者的名字|
|%ce | 提交者的电子邮件地址|
|%cd | 提交日期|
|%cr | 提交日期（距今多长时间）|
|%s | 提交说明|

当 `oneline` 或 `format` 与另一个`log` 选项 `--graph` 结合时尤其有用。会通过ASCII字符形象展示你的分支、合并历史。

git log 常用选项

| 选项|说明|
|-|-|
|-p|按补丁格式显示每个提交引入的差异。|
|--stat|显示每次提交的文件修改统计信息。|
|--shortstat|只显示 --stat 中最后的行数修改添加移除统计。|
|--name-only|仅在提交信息后显示已修改的文件清单。|
|--name-status|显示新增、修改、删除的文件清单。|
|--relative-date|使用较短的相对时间而不是完整格式显示日期（比如“2 weeks ago”）。|
|--graph|在日志旁以 ASCII 图形显示分支与合并历史。|
|--pretty|使用其他格式显示历史提交信息。可用的选项包括 oneline、short、full、fuller 和format（用来定义自己的格式）。|
|--oneline|--pretty=oneline --abbrev-commit 合用的简写。|

#### 限制输出长度

除了使用 `-n` 外，还可以使用按照时间限制的选项`--since` 和 `--until`。
> git log --since=2.weeks

此命令十分丰富。可以是类似 "2008-01-15" 的具体的某一天，也可以是类似 "2 years 1 day3 minutes ago" 的相对日期。

可以是用`--author` 选项显示指定作者的提交，用`--grep` 选项搜索提交说明中的关键字。可以指定多个，但只输出**任意**一个。如果你添加了`--all-match` 则输出所有`--grep` 模式提交。

另一个非常有用的过滤器是 `-S`(俗称“pickaxe”选项，取“用鹤嘴锄在土里捡石头”之意)，他接受一个字符串参数，并且只会显示那些添加或删除了该文字字符串的提交。
> git log -S function_name

`git log` 可以使用路径，表示只关心某些文件或者目录的提交可以在 git log选项的最后指定它们的路径。 因为是放在最后位置上的选项，所以用两个短划线（--）隔开之前的选项和后面限定的路径名。
>git log --pretty=oneline -- git.md

常用的输出选项
| 选项|说明|
|-|-|
|--\<n>|仅显示最近的 n 条提交。|
|--since, --after|仅显示指定时间之后的提交。|
|--until, --before|仅显示指定时间之前的提交。|
|--author|仅显示作者匹配指定字符串的提交。|
|--committer|仅显示提交者匹配指定字符串的提交。|
|--grep|仅显示提交说明中包含指定字符串的提交。|

>git log --pretty="%h - %s" --author='Junio C Hamano' --since="2008-10-01" --before="2008-11-01" --no-merges -- t

>隐藏合并提交
>按照你代码仓库的工作流程，记录中可能有为数不少的合并提交，它们所包含的信息通常并不
多。 为了避免显示的合并提交弄乱历史记录，可以为 log 加上 --no-merges 选项。

### 撤销操作

有时候我们提交完了才发现漏掉了几个文件没有添加，或者提交信息写错了。此时，可以运行带有`--amend` 选项的提交命令来重新提交。这个命令会将暂存区中的文件提交。如果自上次提交以来你还未做任何修改（例如，在上次提交后马上执行了此命令），那么快照会保持不变，而你所修改的只是提交信息。
使用此命令会覆盖原提交。
><pre>
>git commit -m 'init'
>git add forgotten_file
>git commit --amend
></pre>

最终你只会得到一个提交。

#### 取消暂存的文件

使用`git reset HEAD <file>` 来取消文件暂存。

#### 撤销对文件的修改

如何撤销工作区对文件的修改？使用`git status` 可以很清楚的看到。书上说的是 `get checkout -- <file>` , 而我本地则是 `get restore <file>`。 我尝试了下，两个都可以。

请记住，在 Git 中任何 **已提交** 的东西几乎总是可以恢复的。甚至那些被删除的分支中的提交或使用`--amend` 选项覆盖的提交也可以恢复。然而，任何你未提交的东西一旦丢失很可能再也找不到了。


### 远程仓库的使用

为了协作，你需要知道如何管理远程仓库。"远程" 只是一个概念，并不一定在其他计算机，也可能在你的本机上。

#### 查看远程仓库

`git remote` 可以查看已经配置的远程服务器。也可以指定 `-v`,会显示需要读写的远程仓库和其连接。

#### 添加远程仓库

`git remote add <shortname> <url>` 添加一个新的远程仓库，同时指定一个方便的简写。 在命令行中，你可以使用简写来代替url。

#### 从远程仓库中抓取与拉取

>git fetch \<remote>

这个命令会访问远程仓库，从中拉取所有你还没有的数据。执行完成后，你将拥有那个远程仓库中的所有分支。注意此命令只会将远程仓库下载到本地仓库，并不会干扰工作区。如果你的当前分支设置了跟踪远程分支，那么可以用`git pull` 命令来自动抓取后合并到该远程分支到当前分支。

#### 推送到远程仓库

推送命令很简单`git push <remote> <branch>`。只有当你有写入权限时，此命令才能生效。当你和其他人同时克隆，他们先推送到上游，而你在推送的时候，你的推送会被拒绝，你需要先抓取他们的工作，然后在推送。

#### 查看某个远程仓库

`git remote show <remote>` 是一个很有用的命令，特别当你时一个重度 Git 使用者时尤其如此。他还会告诉你 使用`git pull` 和 `git push` 时的结果。


#### 远程仓库的重命名与移除

你可以运行`git remote rename` 来修改一个远程仓库的名字。
> git remote rename pb paul

这个命令同样会修改你所有远程跟踪的名字。
使用 `git remote remove` 或 `git remote rm` 来移除远程仓库，当仓库被删除，远程仓库和所有分支也将一起被删除。



### 打标签

Git 可以个重要的提交打标签，具有代表性的是使用这个功能来标记发布结点（v1.0,v2.0...）。

#### 列出标签

`git tag` 可以列出标签(可带上 `-l` 意味着`--list`)。
也可以按照特定的模式查找标签：
>git tag -l "v1.8.5*"

如果你提供了一个匹配标签名的统配模式，那么`-i` 或 `--list` 是强制使用的。

#### 创建标签

Git 支持两种标签：轻量标签（lightweight）与 附注标签（annotated）。

轻量标签很像一个不会改变的分支--它只是某个特定提交的引用。

附注标签是存储在 Git 中的一个完整对象，它们是可以被校验的，其中包含打标签者的名字、电子邮件地址、日期时间，此外还有一个标签信息，并且可以使用GUN Privacy Guard (GPG) 签名并验证。通常会建议创建附注标签，这样你可以拥有以上的所有信息，但如果你只是想用一个临时标签，或者因为某些原因不想保存这些信息，那么也可以使用轻量标签。

#### 附注标签

在 Git 中创建附注标签十分简单。最简单的方式是当你在运行`tag` 命令时指定 `-a` 选项：
>git tag -a v1.4 -m "my version 1.4"

`-m` 选项指定了一条将会存储在标签中的信息，如果没有指定，会启动编辑器要求你输入信息。

通过 `git show` 可以看到标签信息和与之对应的提交信息。

#### 轻量标签

另一种给提交打标签的方式是使用轻量标签。轻量标签本质是将提交校验和存储到一个文件中--没有保存其他任何信息。

#### 后期打标签

可以将标签直接打到某个提交
>git tag -a v1.2 439776f62b06dff3729183c660ee601f87a4b126

#### 共享标签

默认情况下，`git push` 不会传送标签到远程仓库。必须显示设置`git push origin <tagname>`。

如果一次推送很多标签，也可以使用`--tags` 选线的`git push` 命令。这将会把所有不在远程仓库的标签全部推送过去。`git push <remote> --tags` 会推送两种标签。

#### 删除标签

`git tag -d <tagname>` 可以删除标签。但这个操作不能移除远程仓库的标签。你必须使用`git push <remote> :refs/tags/<tagname>` 来更新你的远程仓库。

第一种变体是`git push <remote> :refs/tags/<tagname>`：
> git push origin :refs/tags/v1.4-lw

上面操作的含义是将冒号前面的空值推送到远程标签名，从而高效的删除它。

第二种更加直观的删除远程标签的方式是：
> git push origin --delete <tagname>

#### 检出标签

如果你想看某个标签指向的文件版本，可以使用`git checkout`，虽然这会使你的仓库处于“分离头指针” 的状态--这个状态有些不好的副作用：

在”分离头指针“状态下，如果你做了某些改变然后提交它们，标签不会发生变化，但你的新提交不会属于任何分支，并且将无法访问，除非通过确切的提交哈希才能访问。如果你需要提交，你需要创建一个新分支：
>git checkout -b \<branch> \<tagname>

如果在这之后进行了提交，branch 分支就会向前移动，此时它就会和 tagname 稍微有些不同，需要注意。

### Git 别名

Git 可以设置别名，通过`git conifg`:
>git config --global alias.co checkout
>git config --global alias.br branch
>git config --global alias.ci commit
>git config --global alias.st status

这意味这，当需要输入`git commit` 是，只需要输入`git ci`。随着你继续不断使用Git，可能经常用到其他命令，所以创建别名是不要犹豫。

>git config --global alias.unstage 'reset HEAD --'

会使下面两个命令等价:
><pre>git unstaged fileA
>git reset HEAD -- fileA
></pre>

这样看起来更清楚一些。通常会添加一个`last` 命令：
>git config --global alias.last 'log -1 HEAD'

这样，可以轻松看到最后一次提交。

如果你想执行外部命令。那样的话，可以在命令前面加入`!` 号。


## Git 分支
Git 分支异常轻量，创建分支几乎能在一瞬间完成，而切换分支也同样快捷。Git 鼓励在开发中频繁的使用分支和合并。理解这一特性，将改变开发方式。

### 分支简介

暂存操作会为每一个文件计算校验和，然后会把当前版本的文件快照保存到 Git 仓库中（Git 使用 blob 对象来保存他们），最终将校验和放入暂存区：
><pre>
>git add README test.rb LICENSE
>git commit -m 'init'
></pre>

当使用`git commit` 进行提交操作时，Git 会先计算每一个子目录的校验和，然后在 Git 仓库中这些校验和保存为树对象。随后，Git 便会创建一个提交对象，它除了包含上面的信息，还包含指向这个树对象的指针。

现在，Git 仓库有5个对象：3个blob 对象，1个树对象（记录目录结构时blob对象的索引） 以及一个提交对象（包含着树对象和提交信息）。

![commit-and-tree](https://git-scm.com/book/en/v2/images/commit-and-tree.png)

做了些修改后在提交，那么这次提交会包含着一个父对象指向上次提交的指针。

![commits-and-parents](https://git-scm.com/book/en/v2/images/commits-and-parents.png)

Git 的分支，其实本质仅仅是指向提交对象的可变指针。Git 的默认分支名字是`master`。`master` 分支会在每次提交后自动向前移动。

> Git 的 `master` 并不是一个特殊分支，和其他分支没有分别。只是它是初始默认分支。并且大多数人都懒得去修改它。

![branch-and-history](https://git-scm.com/book/en/v2/images/branch-and-history.png)

#### 分支创建

`git branch` 可以创建分支。

> git branch testing

![two-branches](https://git-scm.com/book/en/v2/images/two-branches.png)

在 Git 中，有一个名为 `HEAD` 的指针，指向当前所在的本地分支。`git branch` 只会创建分支，并不会将`HEAD`指针移动到新的分支。

![head-to-master](https://git-scm.com/book/en/v2/images/head-to-master.png)

你可以使用 `git log` 查看各个分支当前所指的对象。参数是`--decorate`

#### 分支切换

`git checkout` 可以切换分支。
>git checkout testing

这样`HEAD` 就指向 `testing` 了。

![head-to-testing](https://git-scm.com/book/en/v2/images/advance-testing.png)

当我们在提交一次后。
><pre>
>vim test.rb
>git commit -a -m 'made a change'
></pre>

![advance-testing](https://git-scm.com/book/en/v2/images/advance-testing.png
)

可以看到 `testing` 分支向前移动了，而`master` 分支并没有。它仍然指向运行着`git checkout` 时所指向的对象。

我们在切回 `master` 分支。

>git checkout master

![checkout-master](https://git-scm.com/book/en/v2/images/checkout-master.png)

这条命令做了两件事。一是使`HEAD`指针指向了`master` 分支，而是将工作目录恢复成`master` 分支所指向的快照内容。也就是说，你现在做修改的话，将始于一个较旧的版本，也就是忽略`testing`分支的修改。

>分支切换会改变你工作目录的文件。
>在切换分支时，一定要注意你工作目录的文件会被改变。如果不能干净
>的完成这个任务，将会禁止分支切换，防止工作内容丢失。

![advance-master](https://git-scm.com/book/en/v2/images/advance-master.png)

你可以简单的使用 `git log` 命令查看分支历史。运行`git log --oneline --decorate --graph --all`，他会输出你的提交历史、各个分支的指向以及项目的分支分叉情况。

通常我们会创建一个分支并且切换过去，这可以使用`git checkout -b <newbranchname>` 一条命令完成。

### 分支的新建与合并

使用分支能多条线路前进。

#### 新建分支

![basic-branching-1](https://git-scm.com/book/en/v2/images/basic-branching-1.png)

原本的分支是这样的。

当使用`git checkout -b iss53` 之后时。

![basic-branching-2](https://git-scm.com/book/en/v2/images/basic-branching-2.png)

然后在新的分支上做一些提交

>vim index.html
>git commit -a -m 'added a new footer [issue 53]

![basic-branching-3](https://git-scm.com/book/en/v2/images/basic-branching-3.png)

此时有个需求突然需要你修改，但此时`iss53`还没有完成。此时需要你切回`master` 分支，不过在切换之前，需要留意你工作目录和暂存区里那些还没有被提交的修改，它可能和你即将检出的分支有冲突从而阻止 Git 切换到该分支。最好的方法，在你切换分支之前，保持好一个干净状态。有一些方法可以绕过这些问题（暂存（stashing）和 修补提交（commit amending），后面会提到。现在，可以把分支切回`master`了。请注意，切换分支会充值工作区目录。

>git checkout master

在 `master`上进行修改。

![basic-branching-4](https://git-scm.com/book/en/v2/images/basic-branching-4.png)

确保正确后，将 `hotfix` 合并回你的`master`上面。

><pre>git checkout master
>git merge hotfix
>Updating f42c576..3a0874c
>Fast-forward
>  index.html | 2 ++
>  1 file changed, 2 insertions(+)
> </pre>

在合并的时候有个词需要特别关注`快进（fast-forwar）`。这个词的意思就是简单的将指针向前推进，因为两个分支没有冲突的地方。

![basic-branching-5](https://git-scm.com/book/en/v2/images/basic-branching-5.png)

当合并完成和，你应该先删除`hotfix`分支，因为已经不需要它了--`master` 已经指向同一个位置，留着反而有可能造成混乱。
>git branch -d hotfix

现在你可以切回`iss53` 分支继续工作。
>git checkout iss53

![basic-branching-6](https://git-scm.com/book/en/v2/images/basic-branching-6.png)

你在`hotfix`上的工作并没有包含到`iss53`中。

#### 分支的合并

当你完成`iss53` 后，将其并入`master`中，这和之前的工作差不多。
><pre>git checkout master
>Switched to branch 'master'
>git merge iss53
>Merge made by the 'recursive' strategy.
>index.html | 1 +
>1 file changed, 1 insertion(+)
></pre>

这和之前的状况似乎不一样。你的开发历史从一个更早的地方开始分叉（diverged）。Git 不得不做一些额外的工作，这称为三方合并。

![basic-merging-1](https://git-scm.com/book/en/v2/images/basic-merging-1.png)

和之前直接推进不同，Git 将此次三方合并的结果做了一个新的快照并且自动创建一个新的提交指向它。这个被称作一次合并提交，它的特别之处在于它有不止一个父提交。

![basic-merging-2](https://git-scm.com/book/en/v2/images/basic-merging-2.png)

#### 遇到冲突时的分支合并

很多情况不会如此顺利。经常在两个分支中对同一个文件做了不同的修改，此时 Git 没办法干净的合并他们。

><pre>
>git merge iss53
>Auto-merging index.html
>CONFLICT (content): Merge conflict in index.html
>Automatic merge failed; fix conflicts and then commit the result.
></pre>

此时 Git 做了合并，但是并没有自动创建一个提交。 Git 会暂停下来，等待你去解决合并产生的冲突。你可以使用`git status` 查看。
><pre>
>git status
>On branch master
>You have unmerged paths.
>  (fix conflicts and run "git commit")
>Unmerged paths:
>  (use "git add <file>..." to mark resolution)
>  both modified: index.html
>no changes added to commit (use "git add" and/or "git commit -a")
><pre>

Git 会在冲突文件中加入标识。
><pre>
><<<<<<< HEAD:index.html
><div id="footer">contact : email.support@github.com</div>
>=======
><div id="footer">
> please contact us at support@github.com
></div>
>>>>>>>> iss53:index.html
><pre>
上半部分为当前分支的部分。下班部分为合并部分的内容。以`======` 为分界。

当冲突被解决时，对每个文件使用`git add` 命令将其标记为冲突已解决。一旦暂存这些原本的冲突文件，Git 就会将他们标记为冲突已解决。

当完成在使用`git status` 查看状态，可以看到冲突已经解决。

### 分支管理

`git branch` 不仅可以创建和删除分支。不加参数的时候，会获得分支列表。
><pre>
>git branch
>  iss53
>* master
>  testing

前面有`*` 号表示当前分支。如果需要查看每个分支的最后一次提交，可以运行`git branch -v` 命令。

`--merged` 和 `--no-merged` 这两个选项可以过滤这个列表中已经合并和未合并到当前分支的分支。

如果包含未被合并的工作，则不允许删除，如果要强制删除`git branch -D` 命令来删除。

你可以总是查看合并分支而不检出他们
><pre>
>git checkout testing
>git branch --no-merged master
> topicA
> featureB
> </pre>

### 分支工作流

介绍一些工作模式。

#### 长期分支

你可以在`master` 分支保留稳定的代码。然后分出一些名为`develop` 或者 `next` 的平行分支。等他们稳定之后在合并到`master` 分支中。这能维持一定的稳定性。

![lr-branches-1](https://git-scm.com/book/en/v2/images/lr-branches-1.png)

通常我们会把他们想象成流水线（work silos）可能更好理解一点，那些经过测试和考验的提交被宣导更加稳定的流水线上去。

![lr-branched-2](https://git-scm.com/book/en/v2/images/lr-branches-2.png)

#### 主题分支

这种分支使用最多，作为一个短期分支。只为实现某一个功能或者修复某一个bug。在完成任务之后即被删去。虽然时短期分支，依然可以长时间保存，等待方案确定了之后在删除，时间是不定的。

### 远程分支

当我们使用 `git clone` 的时候，大概流程如下。

![remote-branches-1](https://git-scm.com/book/en/v2/images/remote-branches-1.png)

如果你在本地`master` 分支做了一些工作，在同一段时间内有其他人推送提交到`origin` 并且更新的了它的`master` 分支，这个就是说你们的提交历史已走向不同的方向。即便这样，只要你保持不与`origin` 服务器连接（并拉取数据），你的`origin/master` 指针就不会移动。

![remote-branches-2](https://git-scm.com/book/en/v2/images/remote-branches-2.png)

如果要给给定的仓库同步数据，运行`git fetch <remote>` 命令。
这个命令查找"origin" 是哪一个服务器，从中抓取本地没有的数据，并且更新本地数据库，移动`origin/master` 指针到更新之后的位置。

![remote-branches-3](https://git-scm.com/book/en/v2/images/remote-branches-3.png)

#### 推送

当你想要公开分享一个分支时，需要将其推送到有写入权限的远程仓库上。本地的分支并不会自动与远程仓库同步--你必须显示设置你想要推送的分支`git push <remote> <branch>`。

`git push origin serverfix:serverfix`，它会用本地的`serverfix` 来覆盖远程的`serverfix` 分支。如果你想改名，你可以使用`git push origin serverfix:awesomebranch` 来将本地的`serverfix` 分支推送到`awesomebranch` 分支。

如果你使用https 来推送，每次都会询问用户名和密码。

如果你不想在每一次推送时都输入用户名和密码，你可以设置一个"credential cache"。最简单的方式就是将其保存在内存中几分钟。可以运行`git config --global credential.helper cache` 来设置它。

注意当抓取新的远程跟踪分支时，本地不会自动生成一份可编辑的副本。换一句话说，这种情况下，不会有一个新的`serverfix` 分支--- 只有一个不可以修改的`origin/serverfix` 指针。

可以运行`git merge origin/serverfix` 将这些工作合并到当前所在的分支。如果想要在自己的`serverfix` 分支上工作，可以将其建立在远程跟踪分支之上。

><pre>
>git checkout -b serverfix origin/serverfix
>Branch serverfix set up to track remote branch serverfix from origin.
>Switched to a new branch 'serverfix'

这会给你的一个用于工作的本地分支，并且起点位于`origin/serverfix`。

#### 跟踪分支

当克隆一个仓库时，它通常会自动创建一个跟踪`orgin/master` 的 `master` 分支。也可以不跟踪`master` 分支，最简单的方式时`git checkout -b <branch> <remote>/<branch>`。这个操作常用，所以提供的 `--track` 快捷方式。

>git checkout --track origin/serverfix

通过这个命令，当前分支会追踪远程分支 `origin/serverfix` 。由于这个命令常用，如果你尝试检出的分支(a) 不存在（b）且刚好存在一个名字与之匹配的远程分支，那么Git 就会为你创建一个跟踪分支；
><pre>
> git checkout serverfi
> Branch serverfix set up to track remote branch serverfix from origin.
></pre>

想要修改跟踪的远程分支，可以使用`-u` 或 `--set-upstream-to` 运行`git branch` 来显示的设置。
>git branch -u origin/serverfix
>Branch serverfix set up to track remote branch serverfix from origin.

当设置好跟踪分支后，可以使用简写`@{upstream}` 或 `@{u}` 来引用它的上游分支。所以在`master` 分支时并且它正在跟踪`origin/master` 时，如果愿意的话可以使用`git merge @{u}` 来取代`git merge origin/master`。

想要查看更多信息，可以使用 `git branch -vv` 来查看，它会将所有本地分支列出来并且包含更多的信息，如正在跟踪哪个远程分支，是否领先，落后等。

#### 拉取

`git pull` 在大多数情况下的含义大概时`git fetch` 紧接着一个`git merge`。由于经常让人困惑，所以通常单独使用`fetch` 与 `merge` 好些。

#### 删除远程分支

`git push origin --delete serverfix` 会删除远程 `serverfix` 分支。基本这个命令只是从服务器上移除这个指针。Git 服务器通常会保留数据一段时间，知道垃圾回收运行，所以很容易恢复。

### 变基

在Git 中整合来自不同分支的修改方法主要有两种：`merge` 和 `rebase`。

#### 变基的基本操作

![basic-rebase](https://git-scm.com/book/en/v2/images/basic-rebase-1.png)

之前的`merge` 方法会把两个最新的快照(C3 和 C4) 以及二者最近的共同祖先(C2) 进行三方合并，合并的结果是生成一个新的快照（并提交）。

![basic-rebase-2](https://git-scm.com/book/en/v2/images/basic-rebase-2.png)

其实还有一种方法：你可以提取在`C4` 中引入的补丁和修改，然后在`C3` 的基础上应用一次。在Git 中，这种操作就叫做**变基（rebase）**。你可以使用`rebase` 将提交到所有修改都移至另一分支。

><pre>
>git checkout experiment
>git rebase master
> First, rewinding head to replay your work on top of it...
> Applying: added staged command

![basic-rebase-3](https://git-scm.com/book/en/v2/images/basic-rebase-3.png)

切回 `master` 进行一次快照合并。
>git checkout master
>git merge experiment

![basic-rebase-4](https://git-scm.com/book/en/v2/images/basic-rebase-4.png)

此时，C4' 指向的快照就和 the merge example 中 C5 指向的快照一模一样了。这两种整合方法的最终结果没有任何区别，但是变基使得提交历史更加整洁。 你在查看一个经过变基的分支的历史记录时会发现，尽管实际的开发工作是并行的， 但它们看上去就像是串行的一样，提交历史是一条直线没有分叉。

一般我们这样做的目的是为了确保在向远程分支推送时能保持提交历史的整洁——例如向某个其他人维护的项目贡献代码时。 在这种情况下，你首先在自己的分支里进行开发，当开发完成时你需要先将你的代码变基到`origin/master` 上，然后再向主项目提交修改。 这样的话，该项目的维护者就不再需要进行整合工作，只需要快进合并便可。

请注意，无论是通过变基，还是通过三方合并，整合的最终结果所指向的快照始终是一样的，只不过提交历史不同罢了。 变基是将一系列提交按照原有次序依次应用到另一分支上，而合并是把最终结果合在一起。

#### 更有趣的变基例子

![intersting-rebase-1](https://git-scm.com/book/en/v2/images/interesting-rebase-1.png)

假设你希望将 `client` 中的修改合并到主分支并发布，但暂时并不想合并`server` 中修改。这时，你可以使用`git rebase` 命令的`--onto` 选项，选中在`client` 中但不在 `server` 分支中的修改，将他们在`master` 上重放：
>git reabse --onto master server client

以上命令的意识是：“取出`client` 分支，找出它从`server` 分支分歧之后的补丁，然后把这些补丁在`master` 分支上重放一遍，让`client` 看起来像直接基于`master` 修改一样”。这理解起来有一点复杂，不过效果很好。

![interesting-rebase-2](https://git-scm.com/book/en/v2/images/interesting-rebase-2.png)

现在可以合并分支`master` 分支了。

>git checkout master
>git merge client

![interresting-rebase-3](https://git-scm.com/book/en/v2/images/interesting-rebase-3.png)

接下来将`server` 中的修改也整理进来。使用`git rebase <basebranch> <topicbranch>`。这个命令可以避免切换分支。

>git rebase master server

![interesting-rebase-4](https://git-scm.com/book/en/v2/images/interesting-rebase-4.png)

然后就可以快进合并主分支`master`：

>git checkout master
>git merge server

至此，`client` 和 `server` 分支中的修改都已经整合到主分支里了， 你可以删除这两个分支，最终提交历史会变成图**最终的提交历**中的样子：

>git branch -d client
>git branch -d server

![interesting-rebase-5](https://git-scm.com/book/en/v2/images/interesting-rebase-5.png)

#### 变基的风险

变基会带来风险。需要遵循一条定律：

**如果是非本地提交，而别人也可能基于这个提交开发，那么就不要变基，因为一般情况下，`git pull` 是不会拉取变基命令的。**

由于变基会直接移动引用指针，实际是丢弃一些修改，而把修改迁移了一些位置。而这些位置如果被本地所引用，而 `git merge` 会自动新建提交。所以会造成一定的引用混乱。

![perils-of-rebasing-4](https://git-scm.com/book/en/v2/images/perils-of-rebasing-4.png)

`C6` 为  `merge` 提交，之后回到`C4` 使用变基来完成。而本地确不知道这一步骤。执行合并后的提交`C8` 指向 `C4'` 但合并之前的最后一次提交依然指向`C6` 但此时`C6` 已经被取消了，本次并不知情。当下一次提交的时候，所以提交将会被提交上去，`C4`,`C6` 被恢复，这显然是混乱的结果。


#### 用变基解决编辑

上诉问题是有解决办法的。比如 **基于远程分支变基**，`git rebase teamone/master`，Git 将会：
- 检查哪些提交是我们的分支上独有的（C2，C3，C4，C6，C7）
- 检查其中哪些提交不是合并操作的结果（C2，C3，C4）
- 检查哪些提交在对方覆盖更新时并没有被纳入目标分支（只有 C2 和 C3，因为 C4 其实就是 C4'）
- 把查到的这些提交应用在 teamone/master 上面

从而我们将得到与**你将相同的内容又合并了一次，生成了一个新的提交**中不同的结果，如图 **在一个被变基然后强制推送的分支上再次执行变基** 所示。其实就是本地提交基于远程提交主题变基，道理是本地变基是类似的。整理本地分支提交树。


![perils-of-rebasing-5](https://git-scm.com/book/en/v2/images/perils-of-rebasing-5.png)

要想上述方案有效，还需要对方在变基时确保 `C4'` 和 `C4` 是几乎一样的。否则变基操作将无法识别，并新建另一个类似 `C4` 的补丁（而这个补丁很可能无法整洁的整合入历史，因为补丁中的修改已经存在于某个地方了）。

另一种简单的方式是`git pull --rebase`。也可以手动完成这个过程先`git fetch`，再`git rebase teamone/master`。

如果你习惯使用`git pull`，同时又希望默认使用选项`--rebase`，你可以执行这条语句`git config --global pull.rebase true` 来更改`pull.rebase` 的默认配置。

如果你只对不会离开你电脑的提交执行变基，那就不会有事。 如果你对已经推送过的提交执行变基，但别人没有基于它的提交，那么也不会有事。 如果你对已经推送至共用仓库的提交上执行变基命令，并因此丢失了一些别人的开发所基于的提交， 那你就有大麻烦了。

如果你或你的同事在某些情形下决意要这么做，请一定要通知每个人执行 git pull --rebase 命令，这样尽管不能避免伤痛，但能有所缓解。

思考：变基 和 合并哪种方式更好？仓库提交历史的意义又是什么呢？是**记录实际发生过什么**，是历史，被修改即使谎言。还是**项目过程中发生的事**，不一定彰显完整过程，但结果看起来应该尽可能精彩。



## 服务器上的 Git

### 协议

Git 可以使用四种不同的协议来传输资料：本地协议（Local），HTTP协议，SSH（secure Shell）协议及Git 协议。

#### 本地协议

最基本的就是本地协议，其中远程版本就是同一主机的另一个目录。这种协议很少用，不展开说明。

#### HTTP 协议

##### 智能 HTTP 协议

最全面的协议，支持授权，免公钥。SSL加密，端口通用。不过架设最棘手。

#### SSH 协议

使用广泛，假设相对简单，安全，加密。缺点是不支持匿名。

#### Git 协议

速度最快。但没有授权机制，假设也是最难的。


## 分布式 Git

工作流程和如何贡献

### 分布式工作流程

几种工作流

#### 集中式工作流

集中式系统中通常使用的是单点协作模型——集中式工作流。 一个中心集线器，或者说 仓库，可以接受代码，所有人将自己的工作与之同步。 若干个开发者则作为节点，即中心仓库的消费者与中心仓库同步。

![centralized_workflow](https://git-scm.com/book/en/v2/images/centralized_workflow.png)

这意味着如果两个开发者从中心仓库克隆代码下来，同时作了一些修改，那么只有第一个开发者可以顺利地把数据推送回共享服务器。 第二个开发者在推送修改之前，必须先将第一个人的工作合并进来，这样才不会覆盖第一个人的修改。 这和 Subversion （或任何 CVCS）中的概念一样，而且这个模式也可以很好地运用到 Git 中。

#### 集成管理者工作流

 Git 允许多个远程仓库存在，使得这样一种工作流成为可能：每个开发者拥有自己仓库的写权限和其他所有人仓库的读权限。 这种情形下通常会有个代表“官方”项目的权威的仓库。 要为这个项目做贡献，你需要从该项目克隆出一个自己的公开仓库，然后将自己的修改推送上去。 接着你可以请求官方仓库的维护者拉取更新合并到主项目。 维护者可以将你的仓库作为远程仓库添加进来，在本地测试你的变更，将其合并入他们的分支并推送回官方仓库。 这一流程的工作方式如下所示

1. 项目维护者推送到主仓库。
2. 贡献者克隆此仓库，做出修改。
3. 贡献者将数据推送到自己的公开仓库。
4. 贡献者给维护者发送邮件，请求拉取自己的更新。
5. 维护者在自己本地的仓库中，将贡献者的仓库加为远程仓库并合并修改。
6. 维护者将合并后的修改推送到主仓库。

![integration-manager](https://git-scm.com/book/en/v2/images/integration-manager.png)

#### 主管与副主管工作流

这其实是多仓库工作流程的变种。 一般拥有数百位协作开发者的超大型项目才会用到这样的工作方式，例如著名的 Linux 内核项目。好了，我弃了。

### 向一个项目共享

如何贡献？

#### 提交准则

首先，你的提交不应该包含任何空白错误。 Git 提供了一个简单的方式来检查这点——在提交前，运行 `git diff --check`，它将会找到可能的空白错误并将它们为你列出来。

接下来，尝试让每一个提交成为一个逻辑上的独立变更集。 如果可以，尝试让改动可以理解——不要在整个周末编码解决五个问题，然后在周一时将它们提交为一个巨大的提交。

如果其中一些改动修改了同一个文件，尝试使用 git add --patch 来部分暂存文件（在 交互式暂存 中有详细介绍）。 不管你做一个或五个提交，只要所有的改动都曾添加过，项目分支末端的快照就是一样的，所以尽量让你的开发者同事们在审查你的改动的时候更容易些吧。

最后一件要牢记的事是提交信息。 有一个创建优质提交信息的习惯会使 Git 的使用与协作容易的多。

## Git 工具

一些不常用，但可能使用的操作。

### 选择修订版本

#### 简短的 SHA-1

`git log --abbrev-commit` 可以生成简短的SHA-1

#### 分支引用

`git rev-parse master` 可以分支指向特定的SHA-1。

#### 引用日志

当你在工作时，Git 会在后台保存一个应用日志（reflog），引用日志记录了最近几个月你的HEAD和分支引用所指向的历史。

你可以使用`git reflog` 来查看引用日志。

#### 祖先引用

`git show HEAD^` 可以指向`HEAD`的父提交。这和`git show HEAD~` 是等价的。`HEAD~2`代表`HEAD`的父提交的父提交。也可以写成`HEAD~~`。

#### 提交区间

##### 双点

这时最常用的语法。这种语法可以选出在一个分支中而不再另一个分支中的提交。`git log master..experiment` 的意思表示，在`experiment` 分支中，而不再`master`分支中的日志。如果默认留空，Git 会默认为`HEAD`。例如，`git log origin/master..` 将会输出会被传输到远端服务器的提交。

##### 多点

一下三个命令是等价的。

>git log refA..refB
>git log ^refA refB
>git log refB --not refA

这个语法很好用，因为你可以在查询中指定超过两个的引用，这是双点语法无法实现的。比如，你想查看所有 被 refA 或 refB 包含的但是不被 refC 包含的提交，你可以使用以下任意一个命令：
>git log refA refB ^refC
>git log refA refB --not refC

##### 三点

如果你想看 master 或者 experiment 中包含的但不是两者共有的提 交，你可以执行`git log master...experiment`。常用命令`git log --left-right master...experiment` 可以指出提交所在分支。

### 交互式暂存

#### 暂存与取消暂存文件

使用`git add -i` 或者`--interactive` 选项，Git 建辉进入一个交互终端模式。这个命令可以有选择性的暂存文件，生成不同的提交。

#### 暂存补丁

Git 也可以暂存文件的特定部分。例如，如果在 simplegit.rb 文件中做了两处修改，但指向要暂存其中一个。可以输入`p` 或 `5`。Git 会询问你想要部分暂存哪些文件

可以在命令行中使用`git add -p` 或 `git add --patch` 来启动同样的脚本。更进一步的，可以使用`git reset --patch` 命令的补丁模式来部分重置文件，通过`git checkout --patch` 命令来部分检出文件与`git stash save --patch` 命令来部分暂存文件。

#### 贮藏与清理

有时，当你在项目的一部分上已经工作一段时间后，所有东西都进入了混乱的状态， 而这时你想要切换到另一 个分支做一点别的事情。 问题是，你不想仅仅因为过会儿回到这一点而为做了一半的工作创建一次提交。 针对这个问题的答案是 `git stash` 命令。

贮藏（stash）会处理工作目录的脏的状态——即跟踪文件的修改与暂存的改动——然后将未完成的修改保存到一 个栈上， 而你可以在任何时候重新应用这些改动（甚至在不同的分支上）。

#### 贮藏工作

对文件做一些修改。突然向切换分支，但是还不想提交之前的工作；所以贮藏修改。将新的贮藏推送到栈上，运行`git stash` 或者`git stash push`。之后在运行`git status`可以看见工作目录是干净的。

此时，你可以切换到其他分支。想要查看贮藏的东西，可以使用`git stash list`。如果想要应用一个贮藏，可以使用`git stash apply`。这个命令可以将刚才保存的贮藏重新运用于当前分支。如果想要使用一个更久的贮藏，可以使用`git stash apply stash@{2}`。如果不指定，Git 认为指定的是最近的贮藏。可以使用`git stash drop` 加上将要移除的贮藏名字来移除它。也可以使用`git stash pop` 来引用然后从栈上扔掉它。

#### 从贮藏中创建一个分支

`git stash branch <new branchname>` 可以以你指定的分支名创建一个新分支，检出贮藏工作时所在的提交，重新在哪应用工作，人后在应用成功后丢弃贮藏。

#### 清理工作目录

对于工作目录中一些工作或文件，你想做的也许不是贮藏而是移除。 `git clean` 命令就是用来干这个的。你需要谨慎地使用这个命令，因为它被设计为从工作目录中移除未被追踪的文件。 如果你改变主意了，你也不 一定能找回来那些文件的内容。 一个更安全的选项是运行 `git stash --all` 来移除每一样东西并存放在栈中。

你可以使用 `git clean` 命令去除冗余文件或者清理工作目录。 使用 `git clean -f -d` 命令来移除工作目录 中所有未追踪的文件以及空的子目录。 `-f` 意味着“强制（force）”或“确定要移除”，使用它需要 Git 配置变量 `clean.requireForce` 没有显式设置为 `false`。

如果只是想要看看它会做什么，可以使用 `--dry-run` 或 `-n` 选项来运行命令， 这意味着“做一次演习然后告诉 你 将要 移除什么”。默认情况下，`git clean` 命令只会移除没有忽略的未跟踪文件。 任何与 `.gitignore` 或其他忽略文件中的模 式匹配的文件都不会被移除。 如果你也想要移除那些文件，例如为了做一次完全干净的构建而移除所有由构建生成的 `.o` 文件， 可以给 `clean` 命令增加一个 `-x` 选项。

如果不知道 `git clean` 命令将会做什么，在将 `-n` 改为 `-f` 来真正做之前总是先用 `-n` 来运行它做双重检查。 另 一个小心处理过程的方式是使用 `-i` 或 “interactive” 标记来运行它。

如果你恰好在工作目录重复制或克隆了其他Git 仓库（可能时子模块），那么即便时`git clean -fd` 都会拒绝删除这些目录。这种情况，你需要加上第二个`-f` 选项来强调。
















### 搜索

Git 提供了两个有用的工具来快速地从它的数据库中浏览代码和提交。

#### Git Grep

Git 提供一个 `grep` 命令，你可以很方便的从提交历史、工作目录、甚至索引中查找一个字符串或者正则表达式。

可以是使用`-n` 或者`--line-numer` 选项来输出Git 找到的匹配行的行号。

除了上面的基本搜索命令外，`git grep` 还支持大量其他有趣的选项。

`-c` 或 `--count` 可以输出概述信息，只包含匹配字符串的文件，以及每个文件中包好了多少个匹配。如果你还关心上下文，你可以传入`-p` 或 `--show function` 来显示每一个匹配的字符所在的方法或者函数。

你还可以使用`--and` 来查看复杂的字符串组合，它确保了多个匹配出现在同一文本行中。

><pre>git grep --break --heading -n -e '#defind' --and \( -e LINK -e BUF_MAX \) v1.8.0</pre>




#### Git 日志搜索

或者你不想知道某一项在**哪里**,而是iang知道是什么**时候**存在或引入的。`git log -S` 可以帮助你。如果你希望得到更加精确的结果，你可以使用`-G` 选项来使用正则表达式搜索。

##### 行日志搜索

`git log -L` 可以展示变更。
><pre>git log -L :git_deflate_bound:zlib.c</pre>

### 重写历史

在满意之前不要推送你的工作

Git 的基本原则之一是，由于克隆中有很多工作是本地的，因此你可以 在本地 随便重写历史记 录。 然而一旦推送了你的工作，那就完全是另一回事了，除非你有充分的理由进行更改，否 则应该将推送的工作视为最终结果。 简而言之，在对它感到满意并准备与他人分享之前，应当避免推送你的工作。

#### 修改最后一次提交

`git commit --amend` 可以修改最后一次提交。如果不需要重写提交消息`git commit --amend --no-edit` 就可以了。如果提交已经推送，想要再次推送得加上`-f`。

#### 修改多个提交信息

`git rebase -i` 可以变基一系列的提交。
>git rebase -i HEAD~3

再次记住这是一个变基命令——在 `HEAD~3..HEAD` 范围内的每一个修改了提交信息的提交及其**所有后裔**都会被 重写。 不要涉及任何已经推送到中央服务器的提交——这样做会产生一次变更的两个版本，因而使他人困惑。

注意其中的反序显示。 交互式变基给你一个它将会运行的脚本。 它将会从你在命令行中指定的提交`（HEAD~3）` 开始，从上到下的依次重演每一个提交引入的修改。 它将最旧的而不是最新的列在上面，因为那会是第一个将要重演的。

你需要修改脚本来让它停留在你想修改的变更上。 要达到这个目的，你只要将你想修改的每一次提交前面的 ‘pick’ 改为 ‘edit’。

>edit f7f3f6d changed my name a bit 
>pick 310154e updated README formatting and added blame
>pick a5f4a0d added cat-file

当保存并退出编辑器时，Git 将你带回到列表中的最后一次提交，把你送回命令行并提示以下信息：

><pre>git rebase -i HEAD~3 
>Stopped at f7f3f6d... changed my name a bit 
>You can amend the commit now, with
>
>    git commit --amend
>
>Once you're satisfied with your changes, run
>
>    git rebase --continue</pre>

按照信息提示持续输入即可。

#### 重新排序提交

在交互页面重新排序或者删除。

#### 压缩提交

通过交互式变基工具，也可以将一连串提交压缩成一个单独的提交。

如果，指定 “squash” 而不是 “pick” 或 “edit”，Git 将应用两者的修改并合并提交信息在一起。

如果想把3个合并为一次提交，可以这样修改脚本：

>pick f7f3f6d changed my name a bit squash 310154e 
>updated README formatting and added blame
>squash a5f4a0d added cat-file

#### 拆分提交

拆分一个提交会撤消这个提交，然后多次地部分地暂存与提交直到完成你所需次数的提交。 例如，假设想要拆 分三次提交的中间那次提交。 想要将它拆分为两次提交：第一个 “updated README formatting”，第二个 “added blame” 来代替原来的 “updated README formatting and added blame”。 可以通过修改`rebase -i` 的脚本来做到这点，将要拆分的提交的指令修改为 “edit”:

>pick f7f3f6d changed my name a bit
>edit 310154e updated README formatting and added blame
>pick a5f4a0d added cat-file

可以通过 `git reset HEAD^` 做一次针对那个提交的混合重置，实 际上将会撤消那次提交并将修改的文件取消暂存。 现在可以暂存并提交文件直到有几个提交，然后当完成时运行 `git rebase --continue`：

>git reset HEAD^ 
>git add README
>git commit -m 'updated README formatting' $ git add lib/simplegit.rb 
>git commit -m 'added blame'
>git rebase --continue

#### 核武级选项：filter-branch

有另一个历史改写的选项，如果想要通过脚本的方式改写大量提交的话可以使用它——例如，全局修改你的邮箱 地址或从每一个提交中移除一个文件。 这个命令是 `filter-branch`，它可以改写历史中大量的提交，除非你 的项目还没有公开并且其他人没有基于要改写的工作的提交做的工作，否则你不应当使用它。 然而，它可以很有用。 你将会学习到几个常用的用途，这样就得到了它适合使用地方的想法。

`git filter-branch` 有很多陷阱，不再推荐使用它来重写历史。 请考虑使用 `gitfilter-repo`，它是一个 Python 脚本，相比大多数使用 `filter-branch` 的应用来说，它做得要更好。它的文档和源码可访问 https://github.com/newren/git-filter-repo 获取。

##### 从每一个提交中移除一个文件

为了从整个提交历史中移除一个叫做 passwords.txt 的文件，可以使用 --tree-filter 选项 给 filter-branch，`git filter-branch --tree-filter 'rm -f password.txt' HEAD`。

`--tree-filter` 选项在检出项目的每一个提交后运行指定的命令然后重新提交结果。 在本例中，你从每一个 快照中移除了一个叫作 `passwords.txt` 的文件，无论它是否存在。 如果想要移除所有偶然提交的编辑器备份文件，可以运行类似 `git filter-branch --tree-filter 'rm -f *~' HEAD `的命令。为了让 `filter-branch` 在所有分支上运行，可以给命令传递 `--all` 选项。

##### 使一个子目录作为新的根目录

如果想要让 `trunk` 子目录作为每一个提交的新的项目根目录，`filter-branch` 也可以帮助你那么做：

>git filter-branch --subdirectory-filter trunk HEAD

现在`trunk` 子目录了。Git 会自动移除所有不影响子目录的提交。

##### 全局修改邮箱地址

另一个常见的情形是在你开始工作时忘记运行 `git config` 来设置你的名字与邮箱地址， 或者你想要开源一个 项目并且修改所有你的工作邮箱地址为你的个人邮箱地址。 任何情形下，你也可以通过 `filter-branch` 来一次性修改多个提交中的邮箱地址。 需要小心的是只修改你自己的邮箱地址，所以你使用 `--commit-filter`：

><pre>git filter-branch --commit-filter '
>         if [ "$GIT_AUTHOR_EMAIL" = "schacon@localhost" ]; 
>         then
>                 GIT_AUTHOR_NAME="Scott Chacon"; 
>                 GIT_AUTHOR_EMAIL="schacon@example.com"; git commit-tree "$@";
>         else git commit-tree "$@";
>         fi' HEAD</pre>


这会遍历并重写每一个提交来包含你的新邮箱地址。 因为提交包含了它们父提交的 SHA-1 校验和，这个命令会 修改你的历史中的每一个提交的 SHA-1 校验和， 而不仅仅只是那些匹配邮箱地址的提交。

### 重置揭秘

在继续了解更专业的工具前，我们先探讨一下 Git 的 `reset` 和 `checkout` 命令。

##### 三棵树

理解 `reset` 和 `checkout` 的最简方法，就是以 Git 的思维框架（将其作为内容管理器）来管理三棵不同的树。 “树” 在我们这里的实际意思是 “文件的集合”，而不是指特定的数据结构。 （在某些情况下索引看起来并不像一棵树，不过我们现在的目的是用简单的方式思考它。）

|树|用途|
|-|-|
|HEAD|上一次提交的快照，下一次提交的父节点|
|index|预期的下一次提交的快照|
|Workgin Directory|沙盒|


##### HEAD

HEAD 是当前分支引用的指针，它总是指向该分支上的最后一次提交。 这表示 HEAD 将是下一次提交的父结 点。 通常，理解 HEAD 的最简方式，就是将它看做 该分支上的最后一次提交 的快照。

查看HEAD:
>git cat-file -p HEAD

查看每个文件的SHA-1校验和：
>git ls-tree -r HEAD

这两个命令不常用，不过它能帮助你了解到底发生了什么。

##### 索引

索引是你的**预期的下一次提交**。也叫做“暂存区”。

查看索引当前的样子：

>git ls-files -s

##### 工作目录

最后，你就有了自己的**工作目录**（通常也叫做**工作区**）。另外两颗树以一种高效但并不直观的方式，将他们的内容存储在`.git`文件夹中。工作目录会将他们解包为实际的文件以编辑。你可以把工作目录当作**沙盒**。

#### 工作流程

经典的 Git 工作流程是通过操纵这三个区域来以更加连续的状态记录项目快照的。

![reset-workflow](https://git-scm.com/book/en/v2/images/reset-workflow.png)

让我们来可视化这个过程：假设我们进入到一个新目录，其中有一个文件。 我们称其为该文件的 **v1** 版本，将它 标记为蓝色。 现在运行 `git init`，这会创建一个 Git 仓库，其中的 HEAD 引用指向未创建的 `master` 分支。

![reset-ex1](https://git-scm.com/book/en/v2/images/reset-ex1.png)

此时，只有工作目录，没有内容。

现在我们想要提交这个文件，所以用`git add` 来获取工作目录中的内容，并将其复制到索引中。

![reset-ex2](https://git-scm.com/book/en/v2/images/reset-ex2.png)

接着运行`git commit`,它会取得索引中内容并保存为一个永久快照，然后创建一个指向该快照的提交对象，最后更新`master`来指向本次提交。

![reset-ex3](https://git-scm.com/book/en/v2/images/reset-ex3.png)

此时如果我们运行`git status`,会发现没有任何改动，因为现在三棵树完全相同。

现在我们想要对文件进行修改然后提交它。 我们将会经历同样的过程；首先在工作目录中修改文件。 我们称其 为该文件的 v2 版本，并将它标记为红色。

![reset-ex4](https://git-scm.com/book/en/v2/images/reset-ex4.png)

如果现在运行 `git status`，我们会看到文件显示在 “Changes not staged for commit” 下面并被标记为红 色，因为该条目在索引与工作目录之间存在不同。 接着我们运行 `git add` 来将它暂存到索引中。

![reset-ex5](https://git-scm.com/book/en/v2/images/reset-ex5.png)

此时，由于索引和 HEAD 不同，若运行 `git status` 的话就会看到 “Changes to be committed” 下的该文件 变为绿色 ——也就是说，现在预期的下一次提交与上一次提交不同。 最后，我们运行 `git commit` 来完成提交。

现在运行 `git status` 会没有输出，因为三棵树又变得相同了。

切换分支或克隆的过程也类似。 当检出一个分支时，它会修改 **HEAD** 指向新的分支引用，将 **索引** 填充为该次提 交的快照， 然后将 **索引** 的内容复制到 **工作目录** 中。

#### 重置的作用

为了演示这些例子，假设我们再次修改了 `file.txt` 文件并第三次提交它。 现在的历史看起来是这样的：

![reset-start](https://git-scm.com/book/en/v2/images/reset-start.png)

##### 第一步：移动 HEAD

`reset` 做的第一件事是移动 HEAD 的指向。 这与改变 HEAD 自身不同（`checkout` 所做的）；`reset` 移动 `HEAD` 指向的分支。 这意味着如果 `HEAD` 设置为 `master` 分支（例如，你正在 `master` 分支上）， 运行 `git reset 9e5e6a4` 将会使 `master` 指向 `9e5e6a4`。

![reset-soft](https://git-scm.com/book/en/v2/images/reset-soft.png)

无论你调用了何种形式的带有一个提交的 `reset`，它首先都会尝试这样做。 使用 `reset --soft`，它将仅仅停 在那儿。

现在看一眼上图，理解一下发生的事情：它本质上是撤销了上一次 `git commit` 命令。 当你在运行 `git commit` 时，Git 会创建一个新的提交，并移动 `HEAD` 所指向的分支来使其指向该提交。 当你将它 `reset` 回 `HEAD~`（HEAD 的父结点）时，其实就是把该分支移动回原来的位置，而不会改变索引和工作目录。 现在你可以更新索引并再次运行 `git commit` 来完成 `git commit --amend` 所要做的事情了（见 修改最后一次提交）。

##### 第二步：更新索引（--mixed）

注意，如果你现在运行 `git status` 的话，就会看到新的 `HEAD` 和以绿色标出的它和索引之间的区别。 接下来，`reset` 会用 `HEAD` 指向的当前快照的内容来更新索引。

![reset-mixed](https://git-scm.com/book/en/v2/images/reset-mixed.png)

如果指定 `--mixed` 选项，`reset` 将会在这时停止。 这也是默认行为，所以如果没有指定任何选项（在本例中只 是 `git reset HEAD~`），这就是命令将会停止的地方。
现在再看一眼上图，理解一下发生的事情：它依然会撤销一上次 提交，但还会 取消暂存 所有的东西。 于是，我们回滚到了所有 `git add` 和 `git commit` 的命令执行之前。

##### 第三步：更新工作目录（--hard）

`reset` 要做的的第三件事情就是让工作目录看起来像索引。 如果使用 `--hard` 选项，它将会继续这一步。

![reset-hard](https://git-scm.com/book/en/v2/images/reset-hard.png)

现在让我们回想一下刚才发生的事情。 你撤销了最后的提交、`git add` 和 `git commit` 命令 以及 工作目录中 的所有工作。必须注意，`--hard` 标记是 `reset` 命令唯一的危险用法，它也是 Git 会真正地销毁数据的仅有的几个操作之一。 其他任何形式的 `reset` 调用都可以轻松撤消，但是 `--hard` 选项不能，因为它强制覆盖了工作目录中的文件。 在这种特殊情况下，我们的 Git 数据库中的一个提交内还留有该文件的 v3 版本， 我们可以通过 `reflog` 来找回它。但是若该文件还未提交，Git 仍会覆盖它从而导致无法恢复。

##### 回顾

`reset` 命令会以特定的顺序重写这三棵树，在你指定以下选项时停止：

1. 移动 HEAD 分支的指向 （若指定了 `--soft`，则到此停止）
2. 使索引看起来像 HEAD （若未指定 `--hard`，则到此停止）
3. 使工作目录看起来像索引

#### 通过路径来重置

前面讲述了 `reset` 基本形式的行为，不过你还可以给它提供一个作用路径。 若指定了一个路径，`reset` 将会跳 过第 1 步，并且将它的作用范围限定为指定的文件或文件集合。 这样做自然有它的道理，因为 `HEAD` 只是一个 指针，你无法让它同时指向两个提交中各自的一部分。 不过索引和工作目录 可以部分更新，所以重置会继续进行第 2、3 步。

现在，假如我们运行 `git reset file.txt` （这其实是 `git reset --mixed HEAD file.txt` 的简写形 式，因为你既没有指定一个提交的 SHA-1 或分支，也没有指定 `--soft` 或 `--hard`），它会：

1. 移动 HEAD 分支的指向 （已跳过）
2. 让索引看起来像 HEAD （到此处停止）

所以它本质上只是将 `file.txt` 从 HEAD 复制到索引中。

![reset-path1](https://git-scm.com/book/en/v2/images/reset-path1.png)

它还有 取消暂存文件 的实际效果。 如果我们查看该命令的示意图，然后再想想 `git add` 所做的事，就会发现他们正好相反。

![reset-path2](https://git-scm.com/book/en/v2/images/reset-path2.png)

这就是为什么 `git status` 命令的输出会建议运行此命令来取消暂存一个文件。 （查看 取消暂存的文件 来了 解更多。）

我们可以不让 Git 从 HEAD 拉取数据，而是通过具体指定一个提交来拉取该文件的对应版本。 我们只需运行类似 于 `git reset eb43bf file.txt` 的命令即可。

![reset-path3](https://git-scm.com/book/en/v2/images/reset-path3.png)

它其实做了同样的事情，也就是把工作目录中的文件恢复到 v1 版本，运行 `git add` 添加它， 然后再将它恢复 到 v3 版本（只是不用真的过一遍这些步骤）。 如果我们现在运行 `git commit`，它就会记录一条“将该文件恢复到 v1 版本”的更改， 尽管我们并未在工作目录中真正地再次拥有它。

还有一点同 `git add` 一样，就是 `reset` 命令也可以接受一个 `--patch` 选项来一块一块地取消暂存的内容。 这 样你就可以根据选择来取消暂存或恢复内容了。

#### 压缩

假设你有一个项目，第一次提交中有一个文件，第二次提交增加了一个新的文件并修改了第一个文件，第三次提 交再次修改了第一个文件。 由于第二次提交是一个未完成的工作，因此你想要压缩它。

![reset-squash-r1](https://git-scm.com/book/en/v2/images/reset-squash-r1.png)

那么可以运行 `git reset --soft HEAD~2` 来将 `HEAD` 分支移动到一个旧一点的提交上（即你想要保留的最 近的提交）：

![reset-squash-r2](https://git-scm.com/book/en/v2/images/reset-squash-r2.png)


此时你只需运行`git commit`:

![reset-squash-r3](https://git-scm.com/book/en/v2/images/reset-squash-r3.png)

现在你可以查看可到达的历史，即将会推送的历史，现在看起来有个 v1 版 `file-a.txt` 的提交， 接着第二个 提交将 `file-a.txt` 修改成了 v3 版并增加了 `file-b.txt`。 包含 v2 版本的文件已经不在历史中了。

#### 检出

最后，你大概还想知道 `checkout` 和 `reset` 之间的区别。 和 `reset` 一样，`checkout` 也操纵三棵树，不过它 有一点不同，这取决于你是否传给该命令一个文件路径。

##### 不带路径

运行 `git checkout [branch]` 与运行 `git reset --hard [branch]` 非常相似，它会更新所有三棵树使 其看起来像 `[branch]`，不过有两点重要的区别。

首先不同于 `reset --hard，checkout` 对工作目录是安全的，它会通过检查来确保不会将已更改的文件弄 丢。 其实它还更聪明一些。它会在工作目录中先试着简单合并一下，这样所有 还未修改过的 文件都会被更新。而 `reset --hard` 则会不做检查就全面地替换所有东西。

第二个重要的区别是 `checkout` 如何更新 `HEAD`。 `reset` 会移动 `HEAD` 分支的指向，而 `checkout` 只会移动 `HEAD` 自身来指向另一个分支。

例如，假设我们有 `master` 和 `develop` 分支，它们分别指向不同的提交；我们现在在 `develop` 上（所以 `HEAD` 指向它）。 如果我们运行 `git reset master`，那么 `develop` 自身现在会和 `master` 指向同一个提 交。 而如果我们运行 `git checkout master` 的话，`develop` 不会移动，`HEAD` 自身会移动。 现在 `HEAD` 将 会指向 `master`。所以，虽然在这两种情况下我们都移动 `HEAD` 使其指向了提交 A，但 做法 是非常不同的。 `reset` 会移动 `HEAD`分支的指向，而 `checkout` 则移动 `HEAD` 自身。

所以，虽然在这两种情况下我们都移动 `HEAD` 使其指向了提交 A，但 做法 是非常不同的。 `reset` 会移动 `HEAD` 分支的指向，而 `checkout` 则移动 `HEAD` 自身。

![reset-checkout](https://git-scm.com/book/en/v2/images/reset-checkout.png)

##### 带路径

运行 `checkout` 的另一种方式就是指定一个文件路径，这会像 `reset` 一样不会移动 `HEAD`。 它就像 `git reset [branch] file` 那样用该次提交中的那个文件来更新索引，但是它也会覆盖工作目录中对应的文件。 它就像是 `git reset --hard [branch] file`（如果 `reset` 允许你这样运行的话）， 这样对工作目录并不 安全，它也不会移动 `HEAD`。此外，同 `git reset` 和 `git add` 一样，`checkout` 也接受一个 `--patch` 选项，允许你根据选择一块一块地恢复文件内容。

#### 总结

希望你现在熟悉并理解了 `reset` 命令，不过关于它和 `checkout` 之间的区别，你可能还是会有点困惑，毕竟不 太可能记住不同调用的所有规则。下面的速查表列出了命令对树的影响。 “HEAD” 一列中的 “REF” 表示该命令移动了 `HEAD` 指向的分支引 用，而 “HEAD” 则表示只移动了 `HEAD` 自身。 特别注意 WD Safe? 一列——如果它标记为 NO，那么运行该命令之前请考虑一下。

||HEAD|index|workdir|wd safe?|
|-|-|-|-|-|
|**Commit Level**|||||
|reset --soft [commit]|REF|NO|NO|YES|
|reset [commit]|REF|yes|NO|YES|
|reset --hard [commit]|REF|yes|YES|no|
|checkout [commit]|HEAD|yes|YES|YES|
|**File Level**|||||
|reset [commit] <paths>|NO|yes|NO|YES|
|checkout [commit] <paths>|NO|yes|yes|YES|


### 高级合并

Git 一般只会处理无冲突的合并。

#### 合并冲突

当文件出现分歧的时候便会出现合并冲突。

#### 中断合并

`git merge --abort` 可以中断一次合并。

#### 忽略空白

`-Xignore-all-space` 或 `-Xignore-space-change` 选项，第一个在比较行时**完全忽略** 空白修改，第二个选项将一个空白符与多个连续的空白字符视作等价的。

#### 手动文件在合并

。。。。。。。忽略

#### 检出冲突

`git checkout --confilict` 可以重新检出文件并替换合并冲突标记。

可以传递给`--confilict` 参数`diff3` 或 `merge`（默认选项）。如果给`diff3`，Git 不仅仅只给你“ours"和"theirs"的版本，同时也会有”base“本本。

如果你喜欢这种格式，可以通过设置 `merge.conflictstyle` 选项为 `diff3` 来做为以后合并冲突的默认选 项。

>git config --global merge.conflictstyle diff3

`git checkout` 命令也可以使用 `--ours` 和 `--theirs` 选项，这是一种无需合并的快速方式，你可以选择留下 一边的修改而丢弃掉另一边修改。

#### 合并日志

为了得到此次合并中包含的每一个分支的所有独立提交的列表， 我们可以使用之前在 <三点 学习的“三点”语 法。

>git log --oneline --left-right HEAD...MERGE_HEAD
>< f1270f7 update README
>< 9af9d3b add a README
>< 694971d update phrase to hola world
>\> e3eb223 add more tests
>\> 7cff591 add testing script
>\> c3ffff1 changed text to hello mundo

使用`--merge`，它只会显示任何一遍接触了合并冲突文件的提交。

如果你运行命令时用 `-p` 选项代替，你会得到所有冲突文件的区别。 快速获得你需要帮助理解为什么发生冲突的 上下文，以及如何聪明地解决它，这会 **非常** 有用。

#### 组合式差异格式

因为 Git 暂存合并成功的结果，当你在合并冲突状态下运行 `git diff` 时，只会得到现在还在冲突状态的区别。 当需要查看你还需要解决哪些冲突时这很有用。....没什么说的，就是展示冲突和解决冲突后的比较文件。

#### 撤销合并

有两种方法。

##### 修复引用

`git reset --hard HEAD` 前面已经介绍了。

##### 还原提交

如果移动分支指针并不适合你，Git 给你一个生成一个新提交的选项，提交将会撤消一个已存在提交的所有修 改。 Git 称这个操作为“还原”，在这个特定的场景下，你可以像这样调用它：

>git revert -m 1 HEAD

`-m 1` 标记指出 “mainline” 需要被保留下来的父结点。 当你引入一个合并到 `HEAD`（git merge topic）， 新提交有两个父结点：第一个是 `HEAD`（C6），第二个是将要合并入分支的最新提交（`C4`）。 在本例中，我们想要撤消所有由父结点 #2（C4）合并引入的修改，同时保留从父结点 #1（`C6`）开始的所有内容。

有还原提交的历史看起来像这样：

![undomerge-revert](https://git-scm.com/book/en/v2/images/undomerge-revert.png)

新的提交 `^M` 与 `C6` 有完全一样的内容，所以从这儿开始就像合并从未发生过，除了“现在还没合并”的提交依 然在 `HEAD` 的历史中。 如果你尝试再次合并 `topic` 到 `master` Git 会感到困惑：

>git merge topic
>Already up-to-date.

topic 中并没有东西不能从 master 中追踪到达。 更糟的是，如果你在 topic 中增加工作然后再次合并，Git只会引入被还原的合并 之后 的修改。

![undomerge-revert2](https://git-scm.com/book/en/v2/images/undomerge-revert2.png)


最好的方式是在此恢复提交，返回到合并时的状态，然后在合并`topic`。

![undomerge-revert3](https://git-scm.com/book/en/v2/images/undomerge-revert3.png)

在本例中，`M` 与 `^M` 抵消了。 `^^M` 事实上合并入了 `C3` 与` C4` 的修改，`C8` 合并了 `C7` 的修改，所以现在 `topic` 已 经完全被合并了。

#### 其他类型的合并

到目前为止我们介绍的都是通过一个叫作 “recursive” 的合并策略来正常处理的两个分支的正常合并。 然而还 有其他方式来合并两个分支到一起。 让我们来快速介绍其中的几个。

##### 我们或他们的偏好

默认情况下，当 Git 看到两个分支合并中的冲突时，它会将合并冲突标记添加到你的代码中并标记文件为冲突状态来让你解决。 如 果你希望 Git 简单地选择特定的一边并忽略另外一边而不是让你手动解决冲突，你可以传递给 merge 命令一个`-Xours` 或 `-Xtheirs` 参数。

这个选项也可以传递给我们之前看到的 `git merge-file` 命令， 通过运行类似 `git merge-file --ours` 的命令来合并单个文件。

##### 子树合并

感觉很难用上

### Rerere
`git rerere` 功能是一个隐藏的功能。 正如它的名字“重用记录的解决方案（reuse recorded resolution）” 所示，它允许你让 Git 记住解决一个块冲突的方法， 这样在下一次看到相同冲突时，Git 可以为你自动地解决它。

有几种情形下这个功能会非常有用。 在文档中提到的一个例子是想要保证一个长期分支会干净地合并，但是又 不想要一串中间的合并提交弄乱你的提交历史。 将 `rerere` 功能开启后，你可以试着偶尔合并，解决冲突，然后退出合并。 如果你持续这样做，那么最终的合并会很容易，因为 `rerere` 可以为你自动做所有的事情。

可以将同样的策略用在维持一个变基的分支时，这样就不用每次解决同样的变基冲突了。 或者你将一个分支合 并并修复了一堆冲突后想要用变基来替代合并——你可能并不想要再次解决相同的冲突。

另一个 `rerere` 的应用场景是当你偶尔将一堆正在改进的主题分支合并到一个可测试的头时，就像 Git 项目自身 经常做的。 如果测试失败，你可以倒回合并之前然后在去除导致测试失败的那个主题分支后重做合并，而不用再次重新解决所有的冲突。

要启用 rerere 功能，只需运行以下配置选项即可：

>git config --global rerere.enabled true

你也可以通过在特定的仓库中创建 `.git/rr-cache` 目录来开启它，但是设置选项更干净并且可以应用到全 局。

现在我们看一个简单的例子，类似之前的那个。 假设有一个名为 `hello.rb` 的文件如下：

><pre>#! /usr/bin/env ruby def hello
>
>def hello
>   puts 'hello world'
>end</pre>

在一个分支中修改单词 “hello” 为 “hola”，然后在另一个分支中修改 “world” 为 “mundo”，就像之前 一样。

![rerere1](https://git-scm.com/book/en/v2/images/rerere1.png)

当合并两个分支到一起时，我们将会得到一个合并冲突：

>git merge i18n-world
>Auto-merging hello.rb 
>CONFLICT (content): Merge conflict in hello.rb 
>Recorded preimage for 'hello.rb'
>Automatic merge failed; fix conflicts and then commit the result.

你会注意到那个新行 `Recorded preimage for FILE`。除此之外它应该看起来就像一个普通的合并冲突。 在这个时候，`rerere` 可以告诉我们几件事。 和往常一样，在这个时候你可以运行 `git status` 来查看所有冲突的内容：

><pre>git status
>On branch master
>Unmerged paths:
>   (use "git reset HEAD <file>..." to unstage)
>   (use "git add <file>..." to mark resolution)
>   
>   both modified: hello.rb
> </pre>

然而，`git rerere` 也会通过 `git rerere status` 告诉你它记录的合并前状态。

>git rerere status
>hello.rb

并且 `git rerere diff` 将会显示解决方案的当前状态——开始解决前与解决后的样子。

解决之后提交。
>git add hello hello.rb
>git commit
>Recorded resolution for 'hello.rb'.
>[master 68e16e5] Merge branch 'i18n'

可以看到它 "Recorded resolution for FILE"。

![rerere2](https://git-scm.com/book/en/v2/images/rerere2.png)

现在，让我们撤消那个合并然后将它变基到 `master` 分支顶部来替代它。 可以通过使用之前在 重置揭密 看到的 `git reset` 来回滚分支。

>git reset --hard HEAD^
>HEAD is now at ad63f15 i18n the hello

我们的合并被撤消了。 现在让我们变基主题分支。

>git checkout i18n-world
>Switched to branch 'i18n-world'

>git rebase master
>First, rewinding head to replay your work on top of it...
>Applying: i18n one word 
>Using index info to reconstruct a base tree... 
>Falling back to patching base and 3-way merge... 
>Auto-merging hello.rb
>CONFLICT (content): Merge conflict in hello.rb Resolved 'hello.rb' 
>using previous resolution. Failed to merge in the changes.
>Patch failed at 0001 i18n one word

现在，正像我们期望的一样，得到了相同的合并冲突，但是看一下 `Resolved FILE using previous resolution` 这行。 如果我们看这个文件，会发现它已经被解决了，而且在它里面没有合并冲突标记。

><pre>#! /usr/bin/env ruby
>
>def hello
>   puts 'hola mundo'
>end</pre>

同样，git diff 将会显示出它是如何自动地重新解决的。

![rerere3](https://git-scm.com/book/en/v2/images/rerere3.png)

也可以通过 `git checkout` 命令重新恢复到冲突时候的文件状态：
>git checkout --conflict=merge hello.rb
>cat hello.rb

我们将会在 高级合并 中看到这个的一个例子。 然而现在，让我们通过运行 `git rerere` 来重新解决它：
>git rerere

我们通过 `rerere` 缓存的解决方案来自动重新解决了文件冲突。 现在可以添加并继续变基来完成它。

>git add hello.rb
>git rebase --continue
Applying: i18n one word

所以，如果做了很多次重新合并，或者想要一个主题分支始终与你的 `master` 分支保持最新但却不想要一大堆合 并， 或者经常变基，打开 `rerere` 功能可以帮助你的生活变得更美好。