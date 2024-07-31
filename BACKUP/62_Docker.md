# [Docker](https://github.com/dululu/GitNote/issues/62)

>`Docker`是一种开源的容器化平台，它可以帮助开发者**构建、打包、部署和运行**应用程序。通过使用`Docker`，开发者可以将**应用程序及其所有依赖项打包**到一个称为"容器"的独立运行环境中，然后在不同的环境中进行**部署**，而无需担心环境差异和依赖关系的问题。
### 以下是关于Docker的一些重要信息：
- **容器化技术**：Docker基于容器化技术，容器是一种轻量级、可移植的虚拟化技术。它通过利用操作系统级别的虚拟化来隔离应用程序及其依赖项，并提供**一致的运行环境**。
- **镜像和容器：**Docker使用镜像作为构建和分发应用程序的**基本单元**。镜像是一个**只读**的模板，包含了运行应用程序所需的所有文件和设置。通过镜像，可以创建运行时的容器实例。容器是镜像的可运行实例，它可以被启动、停止、删除和管理。
- **跨平台和可移植性**：Docker提供了跨平台的支持，可以在各种操作系统（如Linux、Windows、macOS等）上运行。容器化的应用程序具有高度的可移植性，可以在不同的环境中以相同的方式运行，减少了因环境差异而导致的问题。
- **管理工具和生态系统**：Docker提供了一系列管理工具，如Docker CLI、Docker Compose和Docker Swarm，用于构建、管理和编排容器。此外，Docker生态系统中有大量的公共镜像和社区贡献的工具，可以方便地共享和使用。

---

## WSL使用Docker
- **安装WSL**
- **安装Docker**:可以通过在WSL中执行适当的命令来安装Docker。例如，在Ubuntu上，可以执行以下命令：
```
sudo apt-get update
sudo apt-get install docker.io
```
-**配置Docker访问权限**：默认情况下，Docker需要`root`权限才能运行。为了在WSL中以非root用户身份运行Docker，您需要**将当前用户添加到docker用户组**中。执行以下命令将当前用户添加到docker用户组：
```
sudo usermod -aG docker $USER
```
- **启动Docker服务**：在WSL中，可以使用以下命令启动Docker服务：
```
sudo service docker start
```
- **验证安装**：执行以下命令来验证Docker是否正确安装并正在运行：
```
docker version
```
- **使用Docker**：现在，您可以在WSL中使用Docker命令来构建、运行和管理容器。您可以使用常见的Docker命令，如`docker build`、`docker run`和`docker ps`等。
<img width="728" alt="image" src="https://github.com/dululu/GitNote/assets/64392262/d65dd9b6-5cc6-42fa-b469-5d49bb30b62d">


---

## 玩转Docker
- 可以用Docker做啥
- 常用命令使用
- 基本原理解析

---

## Github Codespaces
[Codespaces](https://www.youtube.com/watch?v=Ef_8Mwi6CR4&t=581s)
- 远程访问位于Azure云中的容器
- 包含了必要的软件包和软件
<img width="272" alt="image" src="https://github.com/user-attachments/assets/e008ba3f-50f2-4abc-ba84-0f445d4a7e7b">

## 如何配置Github Codespaces
`Dockerfile`
- 自定义运行环境
### `.devcontainer.json`
- 描述此代码空间希望拥有的计算资源，如VScode插件，定义代码空间

### 创建`Dockerfile`
```
FROM ubuntu:latest
RUN apt update
RUN apt install --yes git openjdk-21-jdk python3 python3-pip
RUN pip3 install Pillow
```
### 启动codespaces
`.devcontainer.json`
```
{
  "build": {"dockerfile": "Dockerfile"}
}
```
构建镜像，然后基于镜像启动一个容器
启动一个云上的VScode
> 关闭防火墙，打开全局代理，淦
## Update `.devcontainer.json`
<img width="422" alt="image" src="https://github.com/user-attachments/assets/bcf7810a-ebab-4580-926c-a3de64acfe4c">

- 直接从Python Docker 存储库中获取Docker镜像 
- 自定义VScode
- ...

---

Docker->镜像->容器
