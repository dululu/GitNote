# [Status Codes¶](https://github.com/dululu/notes/issues/34)

HTTP状态码（Status Codes）是在HTTP协议中用于表示请求的处理结果的三位数代码。每个状态码都具有特定的含义，用于指示请求是否成功、遇到错误、需要进一步操作等。
以下是一些常见的HTTP状态码及其含义：
- 200 OK：请求成功。服务器成功处理了请求并返回所需的内容。
- 201 Created：已创建。请求成功，并在服务器上创建了新的资源。
- 204 No Content：无内容。请求成功，但响应不包含任何内容。
- 400 Bad Request：错误的请求。服务器无法理解或处理请求，通常是由于请求语法错误。
- 401 Unauthorized：未授权。请求需要身份验证，但未提供有效的身份凭据。
- `403 Forbidden`：禁止访问。服务器拒绝请求，因为请求的资源禁止访问。
- `404 Not Found`：未找到。请求的资源在服务器上不存在。
- `500 Internal Server Error`：服务器内部错误。服务器在处理请求时遇到意外错误。
>4XX client error or 5XX server error response
---
```python
import requests
r = requests.get('https://httpbin.org/get')
r.status_code
print(r.status_code)
```
- If we made a bad request (a 4XX client error or 5XX server error response), we can raise it with [Response.raise_for_status()](https://requests.readthedocs.io/en/latest/api/#requests.Response.raise_for_status):
```python
bad_r = requests.get('https://httpbin.org/status/404')
bad_r.status_code
404

bad_r.raise_for_status()
Traceback (most recent call last):
  File "requests/models.py", line 832, in raise_for_status
    raise http_error
requests.exceptions.HTTPError: 404 Client Error
```

---

- 301 Redirection : HTTP状态码301表示"Moved Permanently"（永久重定向）。当服务器收到请求后，它会返回301状态码来指示请求的资源已永久移动到了一个新的位置。