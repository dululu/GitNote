# [Requests: HTTP for Humans™](https://github.com/dululu/notes/issues/36)

## [Requests](https://requests.readthedocs.io/en/latest/)
- [HTTP/1.1](https://github.com/dululu/notes/issues/37)
- [urllib3](https://github.com/dululu/notes/issues/38)
- [JSON](https://github.com/dululu/notes/issues/38)
- [Status Codes¶](https://github.com/dululu/notes/issues/34)
- SSL Cert Verification
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


---

### Advanced Usage[¶](https://requests.readthedocs.io/en/latest/user/advanced/#advanced-usage)
- Session Objects[¶](https://requests.readthedocs.io/en/latest/user/advanced/#session-objects)
The Session object allows you to persist certain parameters across requests. It also persists cookies across all requests made from the Session instance, and will use urllib3’s [connection pooling]
Let’s persist some cookies across requests:
```python
s = requests.Session()

s.get('https://httpbin.org/cookies/set/sessioncookie/123456789')
r = s.get('https://httpbin.org/cookies')

print(r.text)
# '{"cookies": {"sessioncookie": "123456789"}}'
```
- Request and Response Objects[¶](https://requests.readthedocs.io/en/latest/user/advanced/#request-and-response-objects)
- Prepared Requests[¶](https://requests.readthedocs.io/en/latest/user/advanced/#prepared-requests)
预准备请求（Prepared Requests）是指在发送HTTP请求之前，将请求参数、头部信息、URL等预先设置好的请求对象。
- SSL Cert Verification[¶](https://requests.readthedocs.io/en/latest/user/advanced/#ssl-cert-verification)
SSL证书验证（`SSL Certificate Verification`）是在进行安全的`HTTP`S通信时，验证服务器端提供的SSL证书的有效性和可信任性的过程。当客户端与服务器建立HTTPS连接时，**服务器**会向**客户端**提供一个SSL证书，其中包含了**服务器的公钥和其他相关信息。客户端需要验证此证书，以确保与服务器建立的连接是安全的、可信的。**
>Requests can also ignore verifying the SSL certificate if you set verify to False:忽略SSL证书验证
By default, verify is set to True. Option verify only applies to host certs.
```python
requests.get('https://kennethreitz.org', verify=False)
<Response [200]>
```
- Client Side Certificates[¶](https://requests.readthedocs.io/en/latest/user/advanced/#client-side-certificates)
客户端证书（Client-side Certificates）是用于**客户端身份验证的数字证书。**与传统的服务器端证书用于验证服务器身份不同，客户端证书用于验证客户端的身份。在某些安全通信协议（如`HTTPS`）中，服务器可以要求客户端提供有效的客户端证书，以验证客户端的身份。客户端证书包含了客户端的公钥和其他相关信息，由可信任的证书颁发机构（`Certificate Authority，CA`）签发。
- CA Certificates[¶](https://requests.readthedocs.io/en/latest/user/advanced/#ca-certificates)
CA证书（CA Certificates）是由可信任的证书颁发机构（Certificate Authority，CA）签发的数字证书。**CA证书用于验证其他证书的真实性和可信任性。**

