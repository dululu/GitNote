# [git使用](https://github.com/dululu/GitNote/issues/30)

> 原则上是碰到问题再用

1. 删除GitHub文件
2. `.gitignore`
3. `stage`
4. `pull`和`push`使用
5. `ssh key`使用
6. `Personal access tokens (classic)`个人访问令牌
7. 代码回滚

- [x] 如何在本地删除传到GitHub的文件
    - 首先进入文件仓库
    - 如果想要本地和GitHub一起删除`git rm file`,只是删除云端`git rm --cached file`
    - `git commit -m "delete a file"`和`git push origin main`
    
⚠️如果删除单个文件直接删，删除文件夹`git rm file -r`

- [x] `.gitignore`
使用斜杠（/）指定目录或文件夹。
使用星号（*）表示通配符，匹配零个或多个字符。
使用问号（?）表示通配符，匹配一个字符。
使用感叹号（!）表示取反，即不忽略该模式匹配到的内容。
使用井号（#）表示注释，该行后面的内容将被忽略。
```
# 忽略编译生成的文件
*.o
*.exe
# 忽略目录
/build/
/dist/
# 不忽略特定文件
!src/main.c
```

- [x] `stage`
在Git中，"stage"是指将文件或更改添加到暂存区（也称为索引）的过程。暂存区是位于Git仓库中的一个中间区域，用于准备将要提交的更改。
当您对文件进行修改后，可以使用`git add .`命令将更改添加到暂存区.

---

### `pull`和`push`使用
> 在Git中，pull和push是用于与远程存储库进行交互的两个关键命令。
- `git pull`：pull命令用于从远程存储库获取最新的更改并将其合并到本地存储库中。

当您运行git pull时，Git会自动执行两个操作：`git fetch`和`git merge`。
`git fetch`操作会从**远程存储库下载最新的提交和分支信息，但不会将其合并到当前分支。** 🤔只下载，不合并，奇怪
`git merge`操作将**远程分支的更改合并到当前分支**，使您的本地分支与远程分支**保持同步。**
例如，`git pull origin main`将从名为`origin`的远程存储库的`main`分支获取最新的更改并将其合并到当前分支。

- `git push`：push命令用于将本地存储库中的更改推送到远程存储库。

当您运行`git push`时，Git会将当前分支的提交推送到与之关联的远程存储库。
如果您是首次推送到远程存储库，或者远程存储库中没有与当前分支相对应的分支，Git会自动创建该分支。
如果您的本地分支与远程分支存在冲突（即两者都有不同的更改），您需要先解决冲突，然后再进行推送。
例如，`git push origin main`将将当前分支的提交推送到名为`origin`的远程存储库的`main`分支。

- 首次运行 `git push` 命令
  1. 创建一个新的 Git 仓库或者克隆一个已存在的仓库到你的本地机器上。你可以使用 `git init` 命令来创建一个新的仓库，或者使用 `git clone` 命令来克隆一个已存在的远程仓库。
  2. 在你的本地机器上进行一些代码修改或者添加新文件。
  3. `git add`
  4. `git commit`
  5. 接下来，你需要指定一个远程仓库的名称和 URL，以便将你的本地仓库推送到远程仓库。使用 `git remote add` 命令来添加远程仓库。例如，运行 `git remote add origin <远程仓库的 URL>` 来添加一个名为 "origin" 的远程仓库。
  6. 现在，你可以运行 `git push` 命令来将你的本地仓库的修改推送到远程仓库。例如，运行 `git push origin master` 将你的修改推送到名为 "origin" 的远程仓库的 "master" 分支上。


✍️：都是合并代码，`pull`相当两条命令。


---

### `ssh key`之旅

> 首先我们要知道`ssh key` 的作用：用于客户端（_Windowns系统_）和服务端（_Github服务器_）之间身份验证和加密通信
所以可以将客户端生成的公钥`id_rsa.pub`分发到多个远程服务器上，进行身份验证。 

-  在 Windows 上，默认情况下，Git 客户端使用的目录是`C:\Users\<YourUserName>\.ssh`，我的Windows使用的是[Git Bash](https://gitforwindows.org/)，可以通过设置 `HOME `环境变量来指定 Git 客户端使用的目录。将` HOME `环境变量设置为你希望用于 SSH 密钥的目录路径，然后将密钥文件复制到该目录中即可。
- 在Linux中时，我使用的是WSL,直接打开`cd ~/.ssh/`,可以直接将此处的公钥复制到Github上就可以。
<img width="493" alt="image" src="https://github.com/dululu/notes/assets/64392262/828a20e6-e399-4413-ae0d-a0237edc6af0">

   
   - 在Linux中还可以有其他配置，如`config`, `known_hosts`
      - [x] `config`可以配置免密登录到云服务服务器，但是GitHub 不提供远程登录到其服务器的功能，GitHub 是一个托管代码的平台。只能自己购买，如腾讯云，阿里云等等。
      - [x] `known_hosts`是一个存储 SSH 主机密钥指纹的文件，用于验证远程服务器的身份。当你首次连接到一个新的远程服务器时，SSH 客户端会将**该服务器的公钥指纹保存在 known_hosts** 文件中。
在后续的连接中，SSH 客户端会**比对**远程服务器的公钥指纹与 known_hosts 文件中保存的指纹，以确保连接的安全性。如果远程服务器的公钥指纹与 known_hosts 文件中保存的指纹不匹配，SSH 客户端会发出警告，防止潜在的安全风险。
<img width="296" alt="image" src="https://github.com/dululu/notes/assets/64392262/282ce647-b610-47d3-9e91-cd60ee241860">

## Git Bash，设置 HOME 环境变量来指定 Git 客户端使用的目录

1. 打开 Git Bash 终端。
2. 输入以下命令来编辑你的 Bash 配置文件（一般是 `~/.bashrc` 或`~/.bash_profile`）: `vim ~/.bashrc`或`vim ~/.bash_profile`，选择其中一个命令，根据你的系统和配置文件选择。







---

`Personal access tokens (classic)`
- [Developer Settings](https://github.com/settings/apps)
个人访问令牌（Personal Access Tokens，PATs）是一种用于访问和认证各种在线服务和API的身份验证方法。它们通常用于用户或应用程序需要以编程方式与服务进行交互，而无需完整的用户登录。

“经典”个人访问令牌是指在更新的身份验证方法（如OAuth 2.0）变得更为普遍之前常用的PAT形式。这些令牌通常由服务提供商生成，并与特定的用户帐户或应用程序关联。
- 个人访问令牌可以用作**替代传统密码**的一种身份验证方式。相比于使用用户名和密码进行身份验证，个人访问令牌提供了更高的安全性和灵活性。

---

## 代码回滚
#### `github`上的代码回滚
- `git branch`显示所有分支，并且切换到所需的分支`git checkout <branch-name>`
- 查看提交记录`git log`
- 回滚`git revert <commit-hash>`
- `git push`
#### 在本地需要回滚代码可以用
`git checkout <commit-hash>`
将"<commit-hash>"替换为您想要回滚到的提交哈希值。

## 创建新的分支，提交新的代码文件