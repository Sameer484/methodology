##### Finding the confidential information related to aws s3 misconfiguration
````
inurl:samsung site:http://s3.amazonaws.com confidential | top secret | classified | undisclosed
````
#### Dorking by file extension. Searching for subdomains that uses php file type like (subdomains.com/forgetpassword.php)
````
site:*.abb.com ext:php
````
####  yml which Mostly Contain backend Structure such as credentials , users etc
````
ext:yml inurl:Orgname
````

#### Unique google dorking to find jucy subdomains
```
site:*<*.target.*
site:*<-*.target.*
site:*>*.target.*
site:*->*.target.*
site:*<->*.target.*
```
#### Some good dorks to find login panels
```
site:*<*.target.com intext:"login" | intitle:"login" | inurl:"login" | intext:"username" | intitle:"username" | inurl:"username" | intext:"password" | intitle:"password" | inurl:"password"
```
