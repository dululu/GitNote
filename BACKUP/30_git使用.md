# [git使用](https://github.com/dululu/notes/issues/30)

> 原则上是碰到问题再用

1. 删除GitHub文件

- [ ] 如何在本地删除传到GitHub的文件
    - 首先进入文件仓库
    - 如果想要本地和GitHub一起删除`git rm file`,只是删除云端`git rm --cached file`
    - `git commit -m "delete a file"`和`git push origin main`
    
⚠️如果删除单个文件直接删，删除文件夹`git rm file -r`