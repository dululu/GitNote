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