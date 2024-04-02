# [Django](https://github.com/dululu/notes/issues/41)

## Django[<_>](https://github.com/jaywcjlove/reference/blob/main/docs/django.md)
M models
T templates
V views
MTV
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

### **启动`Django`->`Django`检查`url.py`文件->调用与`URL`匹配的示图**

## **关于根路由**
  在与 `views.py` 文件相同的文件夹中创建一个名为 `urls.py` 的文件，并在其中输入以下代码：
  ```python
  from django.urls import path
  from . import views
  urlpatterns = [
      path('', views.index, name='index'),
  ]
  ```
  在 根路由`import`语句中添加 `include` 模块，并在列表中添加一个 `path()` 函数。文件将如下所示：
  ```python
  from django.contrib import admin
  from django.urls import include, path
  
  urlpatterns = [
    path('members/', include('members.urls')),  # 这里的是App的名称
    path('admin/', admin.site.urls),
  ]
  ```
`Django` 视图是接受 `http` 请求并返回 `http` 响应的 `Python` 函数
```python
from django.shortcuts import render
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello world!")
```
再次运行`Django`时就可以返回来自客户端的回应



---

## 创建表（模型）
在 APP 文件夹中创建一个 `templates` 文件夹，一般用来存放`html`文件,如何丰富页面：返回`templates`模板。
- 修改示图
```python
from django.http import HttpResponse
from django.template import loader

def index(request):
# 加载模板
  template = loader.get_template('myfirst.html')
# 返回响应
  return HttpResponse(template.render())
```
- `django.http` 模块包含了与 `HTTP` 请求和响应相关的类和函数。其中，`HttpResponse `是一个用于构造 `HTTP` 响应的类。你可以通过创建 `HttpResponse` 对象并将内容作为参数传递给它来构建响应。
- `django.template.loader` 模块提供了加载模板的功能。它包含了一个名为 `loader` 的对象，你可以使用它的方法来加载和渲染 `Django` 模板。模板是用于生成动态内容的文件，允许你将数据和 `HTML` 或其他文本组合在一起。

## 更改设置`setting.py`
告诉 `Django `一个新的应用程序已创建,查找`INSTALLED_APPS[]` 列表并添加成员应用程序
```python
...  # 省略默认
'xiaomi.apps.XiaomiConfig'
```
然后运行
```python
py manage.py migrate #有时需要指定Python的版本
```
`py manage.py migrate` 命令通常在 `Django` 项目中使用，用于执行待处理的数据库迁移。当你运行这个命令时，`Django` 将会检查项目中定义的数据库模型的迁移，并将必要的更改应用到数据库中，以使其与模型保持同步。在修改模型或创建新的迁移时，定期运行 `migrate`命令是一个好习惯，以确保数据库模式是最新的。

## 创建表（模型）
`models.py` 创建一个成员类,并描述其中的表字段：
```python
from django.db import models

class Members(models.Model):
  firstname = models.CharField(max_length=255)
  lastname = models.CharField(max_length=255)
```
#### 应用程序的数据库迁移文件
```python
py manage.py makemigrations appname

py manage.py migrate
```
根据模型的更改生成一个迁移文件,该迁移文件包含有关如何修改数据库结构以使其与新的模型定义保持同步的指令。
在运行该命令之后，你应该能够在` "members"` 应用程序的目录下看到一个名为 `0001_initial.py`（或类似的）的迁移文件。该文件描述了数据库结构的初始状态。
然后，你可以运行` py manage.py migrate `命令来应用这个迁移文件，将更改应用到实际的数据库中。

---

## [Django 模板](https://github.com/jaywcjlove/reference/blob/main/docs/django.md#django-%E6%A8%A1%E6%9D%BF)
---

## [添加静态文件](https://github.com/jaywcjlove/reference/blob/main/docs/django.md#%E6%B7%BB%E5%8A%A0%E9%9D%99%E6%80%81%E6%96%87%E4%BB%B6)