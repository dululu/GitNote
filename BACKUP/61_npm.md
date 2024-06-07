# [npm](https://github.com/dululu/GitNote/issues/61)

## npm
>介绍：npm（Node Package Manager）是Node.js的包管理器，用于安装、更新和管理JavaScript模块。它是Node.js生态系统中最常用的工具之一，许多开发者使用它来管理他们的项目依赖项。
#### 常见用法：
- 安装npm：当您安装Node.js时，npm会自动安装在您的计算机上，您可以通过在终端或命令提示符中运行npm -v来验证它是否已安装。
- 初始化项目：在开始一个新的项目时，您可以使用npm init命令来初始化项目并生成一个package.json文件。package.json文件包含了项目的元数据和依赖项信息
- 安装依赖项：使用npm install命令可以安装项目所需的依赖项。您可以在命令后面指定要安装的包的名称，也可以通过在package.json文件中列出依赖项并运行npm install来安装所有依赖项。
```
npm install package-name
npm install --save package-name
npm install --save-dev package-name
npm install
```
--save标志用于将包添加到package.json文件的dependencies部分，--save-dev标志用于将包添加到devDependencies部分。
- 升级依赖项：使用npm update命令可以升级项目的依赖项。它会检查安装的包的最新版本，并更新package.json文件中的版本号。 例如：
```
npm update package-name
npm update 
```
- 全局安装：除了项目依赖项外，npm还支持全局安装包。全局安装的包可以在命令行中直接访问。要全局安装一个包，您可以使用`-g`标志。 例如：
```
npm uninstall package-name
npm install -g package-name
```