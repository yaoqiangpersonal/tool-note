
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

### 文本编辑器
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

#### 忽略文件按

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





  





