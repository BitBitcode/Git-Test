# Git 配置
Git 提供了一个叫做 git config 的工具，专门用来配置或读取相应的工作环境变量。

## 用户信息
配置个人的用户名称和电子邮件地址：
```
$ git config --global user.name "BitBitcode"
$ git config --global user.email 137XXXX451@qq.com
```
参数解释:
+ user.name：用户名："BitBitcode"
+ user.email：用户邮箱：137XXXX451@qq.com
+ --global 选项：修改用户主目录下的配置文件，所有的项目会默认使用此用户配置信息。

**注意：**
+ 如果要在某个仓库中使用其他用户名和电子邮箱地址，只要去掉 --global 选项重新配置即可，新的设定保存在当前项目的 .git/config 文件里。

## 查看配置信息
要检查已有的配置信息，可以使用 git config --list 命令：
```
$ git config --list
http.postbuffer=2M
user.name=BitBitcode
user.email=137XXXX451@qq.com
```
**注意：**
+ 有时候会看到重复的变量名，那就说明它们来自不同的配置文件（比如 /etc/gitconfig 和 ~/.gitconfig），不过最终 Git 实际采用的是最后一个。
  
  这些配置我们也可以在 ~/.gitconfig 或 /etc/gitconfig 看到：
```
vim ~/.gitconfig 
```
显示内容如下所示：
```
[http]
    postBuffer = 2M
[user]
    name = runoob
    email = test@runoob.com
```
也可以直接查阅某个环境变量的设定，只要把特定的名字跟在后面即可，像这样：
```
$ git config user.name
BitBitcode
```

## 链接多个远程仓库
最常见的操作是将一个仓库同时链接到Github和Gitee\
在仓库目录下查看当前链接的远程仓库
```
$ git remote -v
```


# Git 操作
## 提交更改
```
$ git add .
$ git commit -m "本次提交的描述"
$ git push origin master 
```
注意，如果你设置了多个远程仓库，那么这里的 “`$ git push origin master`” 应改为 “`$ git push 远程仓库名称 master`”


# 文本编辑器
设置Git默认使用的文本编辑器, 一般可能会是 Vi 或者 Vim。如果你有其他偏好，比如 Emacs 的话，可以重新设置：:
```
$ git config --global core.editor emacs
```

# 差异分析工具
还有一个比较常用的是，在解决合并冲突时使用哪种差异分析工具。比如要改用 vimdiff 的话：

$ git config --global merge.tool vimdiff
Git 可以理解 kdiff3，tkdiff，meld，xxdiff，emerge，vimdiff，gvimdiff，ecmerge，和 opendiff 等合并工具的输出信息。

