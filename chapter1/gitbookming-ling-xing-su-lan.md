Git是一款免费、开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。基本安装请点击安装教程。如果不需要从GitHub更新书到本地再编译，则可以不安装Git。

###  {#在-Windows-上安装}

### 1.安装 Git {#在-Windows-上安装}

是时候动手尝试下 Git 了，不过得先安装好它。有许多种安装方式，主要分为两种，一种是通过编译源代码来安装；另一种是使用为特定平台预编译好的安装包。

### [从源代码安装](https://git-scm.com/book/zh/v1/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git#从源代码安装) {#从源代码安装}

若是条件允许，从源代码安装有很多好处，至少可以安装最新的版本。Git 的每个版本都在不断尝试改进用户体验，所以能通过源代码自己编译安装最新版本就再好不过了。有些 Linux 版本自带的安装包更新起来并不及时，所以除非你在用最新的 distro 或者 backports，那么从源代码安装其实该算是最佳选择。

Git 的工作需要调用 curl，zlib，openssl，expat，libiconv 等库的代码，所以需要先安装这些依赖工具。在有 yum 的系统上（比如 Fedora）或者有 apt-get 的系统上（比如 Debian 体系），可以用下面的命令安装：

```
$ yum install curl-devel expat-devel gettext-devel \
  openssl-devel zlib-devel

$ apt-get install libcurl4-gnutls-dev libexpat1-dev gettext \
  libz-dev libssl-dev

```

之后，从下面的 Git 官方站点下载最新版本源代码：

```
http://git-scm.com/download

```

然后编译并安装：

```
$ tar -zxf git-1.7.2.2.tar.gz
$ cd git-1.7.2.2
$ make prefix=/usr/local all
$ sudo make prefix=/usr/local install

```

现在已经可以用`git`命令了，用`git`把 Git 项目仓库克隆到本地，以便日后随时更新：

```
$ git clone git://git.kernel.org/pub/scm/git/git.git

```

### [在 Linux 上安装](https://git-scm.com/book/zh/v1/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git#在-Linux-上安装) {#在-Linux-上安装}

如果要在 Linux 上安装预编译好的 Git 二进制安装包，可以直接用系统提供的包管理工具。在 Fedora 上用 yum 安装：

```
$ yum install git-core

```

在 Ubuntu 这类 Debian 体系的系统上，可以用 apt-get 安装：

```
$ apt-get install git

```

### [在 Mac 上安装](https://git-scm.com/book/zh/v1/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git#在-Mac-上安装) {#在-Mac-上安装}

在 Mac 上安装 Git 有两种方式。最容易的当属使用图形化的 Git 安装工具，界面如图 1-7，下载地址在：

```
http://sourceforge.net/projects/git-osx-installer/
```

![](https://git-scm.com/figures/18333fig0107-tn.png)

  


图 1-7. Git OS X 安装工具



另一种是通过 MacPorts \(`http://www.macports.org`\) 安装。如果已经装好了 MacPorts，用下面的命令安装 Git：

```
$ sudo port install git-core +svn +doc +bash_completion +gitweb

```

这种方式就不需要再自己安装依赖库了，Macports 会帮你搞定这些麻烦事。一般上面列出的安装选项已经够用，要是你想用 Git 连接 Subversion 的代码仓库，还可以加上 +svn 选项，具体将在第八章作介绍。（译注：还有一种是使用 homebrew（`https://github.com/mxcl/homebrew`）：`brew install git`。）

### [在 Windows 上安装](https://git-scm.com/book/zh/v1/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git#在-Windows-上安装) {#在-Windows-上安装}

在 Windows 上安装 Git 同样轻松，有个叫做 msysGit 的项目提供了安装包，可以到 GitHub 的页面上下载 exe 安装文件并运行：

```
http://msysgit.github.com/

```

完成安装之后，就可以使用命令行的`git`工具（已经自带了 ssh 客户端）了，另外还有一个图形界面的 Git 项目管理工具。

给 Windows 用户的敬告：你应该在 msysGit 提供的 Unix 风格的 shell 来运行 Git。在 Unix 风格的 shell 中，可以使用本书中提及的复杂多行的命令。对于那些需要在 Windows 命令行中使用 Git 的用户，必须注意：在参数中间有空格的时候，必须使用双引号将参数括起来（在 Linux 中是单引号）；另外，如果扬抑符（^）作为参数的结尾，并且作为这一行的最后一个字符，则这个参数也需要用双引号括起来。因为扬抑符在 Windows 命令行中表示续行（译注：即下一行为这一行命令的继续）。

# 2 初次运行 Git 前的配置

## 初次运行 Git 前的配置

一般在新的系统上，我们都需要先配置下自己的 Git 工作环境。配置工作只需一次，以后升级时还会沿用现在的配置。当然，如果需要，你随时可以用相同的命令修改已有的配置。

Git 提供了一个叫做`git config`的工具（译注：实际是`git-config`命令，只不过可以通过`git`加一个名字来呼叫此命令。），专门用来配置或读取相应的工作环境变量。而正是由这些环境变量，决定了 Git 在各个环节的具体工作方式和行为。这些变量可以存放在以下三个不同的地方：

* `/etc/gitconfig`
  文件：系统中对所有用户都普遍适用的配置。若使用
  `git config`
  时用
  `--system`
  选项，读写的就是这个文件。
* `~/.gitconfig`
  文件：用户目录下的配置文件只适用于该用户。若使用
  `git config`
  时用
  `--global`
  选项，读写的就是这个文件。
* 当前项目的 Git 目录中的配置文件（也就是工作目录中的
  `.git/config`
  文件）：这里的配置仅仅针对当前项目有效。每一个级别的配置都会覆盖上层的相同配置，所以
  `.git/config`
  里的配置会覆盖
  `/etc/gitconfig`
  中的同名变量。

在 Windows 系统上，Git 会找寻用户主目录下的`.gitconfig`文件。主目录即`$HOME`变量指定的目录，一般都是`C:\Documents and Settings\$USER`。此外，Git 还会尝试找寻`/etc/gitconfig`文件，只不过看当初 Git 装在什么目录，就以此作为根目录来定位。

### [用户信息](https://git-scm.com/book/zh/v1/%E8%B5%B7%E6%AD%A5-%E5%88%9D%E6%AC%A1%E8%BF%90%E8%A1%8C-Git-%E5%89%8D%E7%9A%84%E9%85%8D%E7%BD%AE#用户信息) {#用户信息}

第一个要配置的是你个人的用户名称和电子邮件地址。这两条配置很重要，每次 Git 提交时都会引用这两条信息，说明是谁提交了更新，所以会随更新内容一起被永久纳入历史记录：

```
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com

```

如果用了`--global`选项，那么更改的配置文件就是位于你用户主目录下的那个，以后你所有的项目都会默认使用这里配置的用户信息。如果要在某个特定的项目中使用其他名字或者电邮，只要去掉`--global`选项重新配置即可，新的设定保存在当前项目的`.git/config`文件里。

### [文本编辑器](https://git-scm.com/book/zh/v1/%E8%B5%B7%E6%AD%A5-%E5%88%9D%E6%AC%A1%E8%BF%90%E8%A1%8C-Git-%E5%89%8D%E7%9A%84%E9%85%8D%E7%BD%AE#文本编辑器) {#文本编辑器}

接下来要设置的是默认使用的文本编辑器。Git 需要你输入一些额外消息的时候，会自动调用一个外部文本编辑器给你用。默认会使用操作系统指定的默认编辑器，一般可能会是 Vi 或者 Vim。如果你有其他偏好，比如 Emacs 的话，可以重新设置：

```
$ git config --global core.editor emacs

```

### [差异分析工具](https://git-scm.com/book/zh/v1/%E8%B5%B7%E6%AD%A5-%E5%88%9D%E6%AC%A1%E8%BF%90%E8%A1%8C-Git-%E5%89%8D%E7%9A%84%E9%85%8D%E7%BD%AE#差异分析工具) {#差异分析工具}

还有一个比较常用的是，在解决合并冲突时使用哪种差异分析工具。比如要改用 vimdiff 的话：

```
$ git config --global merge.tool vimdiff

```

Git 可以理解 kdiff3，tkdiff，meld，xxdiff，emerge，vimdiff，gvimdiff，ecmerge，和 opendiff 等合并工具的输出信息。当然，你也可以指定使用自己开发的工具，具体怎么做可以参阅第七章。

### [查看配置信息](https://git-scm.com/book/zh/v1/%E8%B5%B7%E6%AD%A5-%E5%88%9D%E6%AC%A1%E8%BF%90%E8%A1%8C-Git-%E5%89%8D%E7%9A%84%E9%85%8D%E7%BD%AE#查看配置信息) {#查看配置信息}

要检查已有的配置信息，可以使用`git config --list`命令：

```
$ git config --list
user.name=Scott Chacon
user.email=schacon@gmail.com
color.status=auto
color.branch=auto
color.interactive=auto
color.diff=auto
...

```

有时候会看到重复的变量名，那就说明它们来自不同的配置文件（比如`/etc/gitconfig`和`~/.gitconfig`），不过最终 Git 实际采用的是最后一个。

也可以直接查阅某个环境变量的设定，只要把特定的名字跟在后面即可，像这样：

```
$ git config user.name
Scott Chacon
```

# 3.  获取帮助

## 获取帮助

想了解 Git 的各式工具该怎么用，可以阅读它们的使用帮助，方法有三：

```
$ git help <verb>

$ git <verb>--help
$ man git-<verb>
```

比如，要学习 config 命令可以怎么用，运行：

```
$ git help config

```

我们随时都可以浏览这些帮助信息而无需连网。 不过，要是你觉得还不够，可以到 Freenode IRC 服务器（irc.freenode.net）上的`#git`或`#github`频道寻求他人帮助。这两个频道上总有着上百号人，大多都有着丰富的 Git 知识，并且乐于助人。





