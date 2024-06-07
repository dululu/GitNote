# [npm](https://github.com/dululu/GitNote/issues/61)

## npm
>介绍：npm（Node Package Manager）是Node.js的**包管理器**，用于安装、更新和管理JavaScript模块。它是Node.js生态系统中最常用的工具之一，许多开发者使用它来管理他们的项目依赖项。
#### 常见用法：
- 安装npm：当您安装Node.js时，npm会自动安装在您的计算机上，您可以通过在终端或命令提示符中运行`npm -v`来**验证**它是否已安装。
- 初始化项目：在开始一个新的项目时，您可以使用`npm init`命令来**初始化**项目并生成一个`package.json`文件。package.json文件包含了项目的**元数据和依赖项信息**
- 安装依赖项：使用`npm install`命令可以安装项目所需的依赖项。您可以在命令后面指定要安装的包的名称，也可以通过在package.json文件中列出依赖项并运行npm install来安装所有依赖项。
```
npm install package-name
npm install --save package-name
npm install --save-dev package-name
npm install
```
`--save`标志用于将包**添加到`package.json`文件**的dependencies部分，`--save-dev`标志用于将包**添加到devDependencies部分。**
- 升级依赖项：使用`npm update`命令可以升级项目的依赖项。它会检查安装的包的最新版本，并更新`package.json`文件中的版本号。 例如：
```
npm update package-name
npm update 
```
- 全局安装：除了项目依赖项外，npm还支持**全局安装包**。**全局安装的包可以在命令行中**直接访问。要全局安装一个包，您可以使用`-g`标志。 例如：
```
npm uninstall package-name
npm install -g package-name
```

---

## 下面是一些关于`npm`和`pip`之间的相似性和区别：

#### 相似性：
- 包管理器：`npm`和`pip`都是包管理器，用于安装、升级和卸载软件包和依赖项。
- 软件包生态系统：两者都有庞大的软件包生态系统，提供了大量的开源软件包供开发者使用。
- 命令行工具：npm和pip都是通过命令行界面使用的工具，开发者可以使用命令来执行各种操作，如安装包、查看已安装的包、更新包等。
#### 区别：
- 编程语言：npm主要用于JavaScript生态系统，用于Node.js项目，而pip主要用于Python生态系统。
- 默认安装位置：npm**将包安装在项目的本地目录**中，而pip**将包安装在Python环境的目录**中。
- 依赖管理：npm使用`package.json`文件来管理项目的依赖关系，可以指定包的版本范围和依赖关系。pip使用`requirements.txt`文件来指定项目的依赖项。
- 脚本管理：`npm`允许在`package.json`中定义脚本命令，可以通过`npm run`来运行这些脚本。`pip`没有类似的内置脚本管理功能。

---

## npm包管理
>问题描述：在`C:\Users\86138>npm install -g hexo-cli`安装在哪里了

当你在命令提示符下运行`npm install -g hexo-cli`命令时，`hexo-cli`模块将被**全局**安装，通常会被安装在`Node.js`的全局模块目录中。

在`Windows`上，默认情况下，全局模块目录位于以下位置之一：

`%AppData%\npm` 目录
`%ProgramFiles%\nodejs\node_modules` 目录
如果你的系统上没有设置其他的**全局**模块目录，那么 `hexo-cli` 应该安装在其中一个目录下。你可以打开文件资源管理器，导航到该目录，然后查找 `hexo-cli` 目录。

### 全局安装与本地安装
>全局安装和本地安装是npm包管理器中安装包的两种常见方式，它们在**安装位置**和**使用方式**上有所区别。
#### 全局：
- 安装位置：全局安装将包安装到系统的全局环境中，通常是在操作系统的特定目录下（如`Windows`上的`C:\Users\{用户名}\AppData\Roaming\npm`或`macOS/Linux上的/usr/local/bin`）。
- 使用方式：全局安装的包可以在命令行中直接访问，可以作为命令行工具使用。安装的包的可执行文件将添加到系统的环境变量中，因此可以从任何位置运行。
#### 本地安装：
- 安装位置：本地安装将包安装到项目的特定目录中，通常是项目根目录下的`node_modules`文件夹。
- 使用方式：本地安装的包只能在项目的上下文中使用。您需要通过相对路径或使用模块加载器（如require）来引入和使用本地安装的包。
