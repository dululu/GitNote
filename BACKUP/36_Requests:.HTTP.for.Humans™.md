# [Requests: HTTP for Humans™](https://github.com/dululu/notes/issues/36)

## [Requests](https://requests.readthedocs.io/en/latest/)
- [HTTP/1.1](https://github.com/dululu/notes/issues/37)
- [urllib3](https://github.com/dululu/notes/issues/38)
- [JSON](https://github.com/dululu/notes/issues/38)
- [Status Codes¶](https://github.com/dululu/notes/issues/34)
---
### Quickstart[¶](https://requests.readthedocs.io/en/latest/user/quickstart/#quickstart)
- Response Content
- Binary Response Content
- JSON Response Content
- Custom Headers
- More complicated POST requests[¶](https://requests.readthedocs.io/en/latest/user/quickstart/#more-complicated-post-requests)
- POST a Multipart-Encoded File[¶](https://requests.readthedocs.io/en/latest/user/quickstart/#post-a-multipart-encoded-file)
- Response Status Codes[¶](https://requests.readthedocs.io/en/latest/user/quickstart/#response-status-codes)
- Response Headers[¶](https://requests.readthedocs.io/en/latest/user/quickstart/#response-headers)
We can view the server’s response headers using a Python dictionary:
**HTTP Header names are case-insensitive.** 
```python
import requests
r = requests.get('https://httpbin.org/get')
r.status_code
print(r.status_code)
print(r.headers)

r.headers['Content-Type']
'application/json'

r.headers.get('content-type')
'application/json'
```
- Cookies[¶](https://requests.readthedocs.io/en/latest/user/quickstart/#cookies)
If a response contains some Cookies, you can quickly access them,Cookies are returned in a [RequestsCookieJar](https://requests.readthedocs.io/en/latest/api/#requests.cookies.RequestsCookieJar), which acts like a dict but also offers a more complete interface, suitable for use over multiple domains or paths. Cookie jars can also be passed in to requests:
- Redirection and History[¶](https://requests.readthedocs.io/en/latest/user/quickstart/#redirection-and-history)
- Timeouts[¶](https://requests.readthedocs.io/en/latest/user/quickstart/#timeouts)
You can tell Requests to stop waiting for a response after a given number of seconds with the `timeout` parameter.
- Errors and Exceptions[¶](https://requests.readthedocs.io/en/latest/user/quickstart/#errors-and-exceptions)
