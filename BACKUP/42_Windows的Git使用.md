# [Windows的Git使用](https://github.com/dululu/notes/issues/42)

> Obsidian同步时一直报错，我觉得是window的git出了问题，以前一直使用的是WSL的Git进行同步。

#### 用户配置
```shell
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```
#### 查看Git的配置设置，您可以使用以下命令:
```shell
git config --list
//此命令将显示全局（--global）和本地（项目特定）配置设置。全局设置适用于整个系统，而本地设置仅适用于当前的Git项目。
```
