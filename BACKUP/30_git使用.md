# [git使用](https://github.com/dululu/notes/issues/30)

> 原则上是碰到问题再用

1. 删除GitHub文件
2. `.gitignore`
3. `stage`
4. `pull`和`push`使用
5. `ssh key`使用

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

✍️：都是合并代码，`pull`相当两条命令。


---

### `ssh key`之旅

> 首先我们要知道`ssh key` 的作用：用于客户端（_Windowns系统_）和服务端（_Github服务器_）之间身份验证和加密通信
所以可以将客户端生成的公钥`id_rsa.pub`分发到多个远程服务器上，