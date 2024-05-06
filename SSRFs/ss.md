### Signup using burp collaborator email 
`user@abc123.burpcollaborator.net`
### We can use gopher protocol to redirect the internal service after getting http request to our domain. 
```
1. we give our url to internal service
2. we send back 302 response with location header being gopher://
3. scan the internal ports.
```
### Bypass the filter if the application seems to have string check like string.contains("victim.com")
```
GET /?url=https://attacker.com?q=victim.com
```
