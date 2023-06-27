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
