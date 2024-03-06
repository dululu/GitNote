# [git使用](https://github.com/dululu/notes/issues/30)

> 原则上是碰到问题再用

1. 删除GitHub文件
2. `.gitignore`

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