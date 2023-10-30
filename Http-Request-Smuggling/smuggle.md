### Things to keep in mind to successfully exploit http request smuggling attacks.
```
1. Make sure to use HTTP/1.1 before trying to exploit because HTTP/2 doesn't support that.
In the inspector tab in burp , change to HTTP/1.1 from request attributes

2. If you are trying to using CL.TE , make sure you include connection: keep-alive header,
cause the backend server will only include that smuggled part in next request over same connection and
 using connection: keep-alive header will keep connection over same network.
```
