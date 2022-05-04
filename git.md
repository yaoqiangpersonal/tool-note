
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
