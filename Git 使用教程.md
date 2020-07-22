# 第1章 了解Git
参考廖雪峰网站教程：https://www.liaoxuefeng.com/wiki/896043488029600/896067008724000

## 1.1 Git的简介

## 1.2 集中式与分布式版本控制系统
SVN 与 Git

### 1.2.1 集中式版本控制系统

### 1.2.2 分布式版本控制系统



# 第2章 安装与配置Git

## 2.1 Git安装程序的下载

### 2.1.1 官方网站
官网慢的要死，懒得找链接了，直接去镜像下载

### 2.1.2 镜像网站
  + 华为镜像网站：[Git for Windows 下载](https://mirrors.huaweicloud.com/git-for-windows/)
  + 其他

**【注意】**
+ 由于镜像网站很多都没有 GUI 界面，所以你需要学会找哪个网址是正确的下载地址，因为有时候你打开的可能是其他文件的下载地址（比如哈希值对比文件，或者其他同名但是不是该操作系统的文件等等）。
+ Windows 系统（64位）的 Git 安装程序的文件名称为：Git-2.27.0-64-bit.exe

## 2.2 Git的安装
这里介绍一些安装步骤中的设置

## 2.3 Git的配置
Git 提供了一个叫做 git config 的工具，专门用来配置或读取相应的工作环境变量。

### 2.3.1 用户信息的配置
配置个人的用户名称和电子邮件地址：
```bash
$ git config --global user.name "BitBitcode"
$ git config --global user.email 137XXXX451@qq.com
```
参数解释:
+ user.name：用户名："BitBitcode"
+ user.email：用户邮箱：137XXXX451@qq.com
+ --global 选项：修改用户主目录下的配置文件，所有的项目会默认使用此用户配置信息。

如果需要为不同的仓库配置不同的用户信息，则需要：
```bash
$ 未完
$
```

**【注意】**

+ 如果要在某个仓库中使用其他用户名和电子邮箱地址，只要去掉 --global 选项重新配置即可，新的设定保存在当前项目的 .git/config 文件里。

### 2.3.2 文本编辑器的配置
设置Git默认使用的文本编辑器, 一般可能会是 Vi 或者 Vim。如果你有其他偏好，比如 Emacs 的话，可以重新设置：:
```bash
$ git config --global core.editor emacs
```

### 2.3.3 差异分析工具的配置
还有一个比较常用的是，在解决合并冲突时使用哪种差异分析工具。比如要改用 vimdiff 的话：

$ git config --global merge.tool vimdiff
Git 可以理解 kdiff3，tkdiff，meld，xxdiff，emerge，vimdiff，gvimdiff，ecmerge，和 opendiff 等合并工具的输出信息。

### 2.3.4 查看配置信息
1、要检查已有的配置信息，可以使用 git config --list 命令：
```bash
$ git config --list
http.postbuffer=2M
user.name=BitBitcode
user.email=137XXXX451@qq.com
```
**注意：**
+ 有时候会看到重复的变量名，那就说明它们来自不同的配置文件（比如 /etc/gitconfig 和 ~/.gitconfig），不过最终 Git 实际采用的是最后一个。

2、这些配置我们也可以在 ~/.gitconfig 或 /etc/gitconfig 看到：
```bash
vim ~/.gitconfig 
```
显示内容如下所示：
```bash
[http]
    postBuffer = 2M
[user]
    name = runoob
    email = test@runoob.com
```

3、也可以直接查阅某个环境变量的设定，只要把特定的名字跟在后面即可，像这样：
```bash
$ git config user.name
BitBitcode
```

# 第3章 创建Git仓库
## 3.1 创建新仓库
### 3.1.1 在本地创建仓库
1、首先建立文件目录。这一步可以通过文件资源管理器完成，也可以用代码完成：
```bash
$ cd C:/Github      // 也可以在这个目录下右键菜单选择“Git Bash here”
$ mkdir Git-Test
$ cd Git-Test
$ pwd               // 查看当前路径
/Users/WWC/Git-Test
```

2、初始化本地仓库。确保当前位于仓库文件夹的目录下，在Git Bash中输入：

```bash
$ git init
Initialized empty Git repository in C:/Github/Git-Test/.git/
```
这时，在仓库文件夹中添加了一个名为“.git”的隐藏文件夹，路径后面多了一个“(master)”，表明现在位于主分支。


### 3.1.2 在远程创建仓库
在Github或Gitee网站上创建同名称的空仓库

#### 3.1.2.1 Github仓库
1、点击“ ”

2、选择。。。

3、readme。。。

（未完，有心情的话补充图片）

#### 3.1.2.2 Gitee仓库
1、点击“ ”

2、选择。。。

3、readme。。。

（未完，有心情的话补充图片）

### 3.1.3 链接到远程仓库
#### 3.1.3.1 获取并添加SSH密钥
1、检查是否已经存在SSH密钥：在用户目录（C:/Users/WWC）下，查看是否存在“.ssh”文件夹，如果存在，此文件夹内是否存在“id_rsa”和“id_rsa.pub”两个文件，如果已经存在，则跳过第二步。注意：“id_rsa”是私钥，必须保密，“id_rsa.pub”是公钥，无需保密；

2、创建一个SSH密钥：在Git Bash中输入以下代码，

```bash
$ ssh-keygen -t rsa -C "smilewwc@qq.com"
```
如果不需要设置密码，则全部回车即可。完成后重复第一步的检查工作；

3、在远程代码管理网站添加SSH密钥
+ Github：登陆GitHub，打开“Account settings”，“SSH Keys”页面，然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容；
+ Gitee：右上角用户头像 -> 菜单“修改资料”，然后选择“SSH公钥”，填写一个便于识别的标题，然后把用户主目录下的.ssh/id_rsa.pub文件的内容粘贴进去；

#### 3.1.3.2 将本地仓库链接到远程仓库
在Git Bash中输入以下代码：
```bash
$ git remote add origin https://github.com/Bitbitcode/Git-Test.git
```

如果遇到以下提示：
```bash
fatal: refusing to merge unrelated histories
```

这是因为系统认为这是两个根本不相干的git库，（一个是本地库，一个是远端库），然后本地要去推送到远端，远端觉得这个本地库跟自己不相干，所以告知无法合并。解决方法：
+ 如果这不是新的仓库（即这个仓库以前创建过），那么推荐使用克隆的方法：从远端库拉下来代码，本地要加入的代码放到远端库下载到本地的库，然后提交上去，因为这样的话，你基于的库就是远端的库，这是一次update了（有关克隆仓库的详细内容将在下一节讲解）；
+ 如果这是新建的仓库，那么使用强制的方法:
  ```bash
  $ git pull origin master --allow-unrelated-histories
  ```
  后面加上 --allow-unrelated-histories ， 把两段不相干的分支进行强行合并，后面再push就可以了 git push gitlab master:init

至此我们就完成了新仓库的创建工作，之后的工作不需要再次进行上述操作，只需要普通的pull、push操作即可。

## 3.2 克隆已有仓库
先导航到克隆的位置，然后在Git Bash输入：
```bash
$ git clone https://gitee.com/Acrylic-Studio/Git-Test
```

## 3.3 链接多个远程仓库
最常见的操作是将一个仓库同时链接到Github和Gitee

1、在仓库目录下查看当前链接的远程仓库
```bash
$ git remote -v
这里添加显示的内容
```

2、删除已链接的远程仓库
```bash
$ git remote remove origin
```

3、添加新的远程仓库
```bash
$ git remote add Gitee git@gitee.com:Acrylic-Studio/Git-Test.git
$ git remote add Github git@github.com:Bitbitcode/Git-Test.git
```
这时查看远程仓库信息：
```bash
$ git remote -v
Gitee   git@gitee.com:/Acrylic-Studio/Git-Test.git (fetch)
Gitee   git@gitee.com:/Acrylic-Studio/Git-Test.git (push)
Github  git@github.com:Bitbitcode/Git-Test.git (fetch)
Github  git@github.com:Bitbitcode/Git-Test.git (push)
```


# 第4章 代码的拉取与提交
## 4.1 拉取已有的远程代码



## 4.2 提交更改
```bash
$ git add .
$ git commit -m "本次提交的描述"
$ git push origin master 
```
注意，如果你设置了多个远程仓库，那么这里的 “`$ git push origin master`” 应改为 “`$ git push 远程仓库名称 master`”
