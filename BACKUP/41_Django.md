# [Django](https://github.com/dululu/notes/issues/41)

## Django
---
### 环境配置
- 安装`Django`
```python
pip3.10 install django    // 最好指定Python的版本
```
需要将`Python`加入环境变量path中
在终端中输入`django-admin`,出现提示即可
## 创建项目
> django-admin startproject  su7

- 项目文件目录
- App

> **创建app:** python manage.py startapp app01

**所以最终一共有两个主要的文件目录：一个是默认的文件，一个是项目生成时创建的文件。**
<img width="326" alt="image" src="https://github.com/dululu/notes/assets/64392262/ea5d9ce5-38b6-43fc-ae3e-79e3f43b4509">

## 启动运行Django
```python
python manage.py runserver
```
<img width="388" alt="image" src="https://github.com/dululu/notes/assets/64392262/ab693d14-023f-40eb-a52d-75279f44892d">

##### 名为 `views.py` 的文件。这是我们**收集发送回正确响应所需的信息的地方**。
- `Django` 接收 `URL`，检查 `urls.py` 文件，并调用与 `URL` 匹配的视图。
- 位于 `views.py` 中的视图检查相关模型。
- 模型是从 `models.py` 文件中导入的。
- 然后视图将数据发送到模板文件夹中的指定模板。
- 模板包含 `HTML` 和 `Django` 标记，并使用数据将完成的 `HTML` 内容返回给浏览器




