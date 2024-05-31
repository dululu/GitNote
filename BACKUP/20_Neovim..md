# [Neovim ](https://github.com/dululu/Blogs/issues/20)

### Step1:安装[Neovim](https://github.com/neovim/neovim/blob/master/INSTALL.md)
Ubuntu+WSL
```powershell-interactive
sudo apt-get install python-dev python-pip python3-dev
sudo apt-get install python3-setuptools
sudo easy_install3 pip
//卸载
sudo cmake --build build/ --target uninstall
```
### Step2:Neovim 基础配置
Neovim 配置文件不是` .vimrc`

而是保存在` ~/.config/nvim/init.vim`,但是 init.vim 只作为入口，真正的配置，是加载的其他的 lua 配置文件
[写的太好了😎😎😎](https://martinlwx.github.io/zh-cn/config-neovim-from-scratch/)

😅 然而我还没弄好 @dululu [2024年01月14日 23:21:49] 