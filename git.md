
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