##### - Check if all the static files of the website are cached or not. If they are cached, find the endpoint that discloses sensitive information in the response like userinfo and session token maybe. And try to add dummy endpoint with extension js,png,avif etc.
![Screenshot from 2023-06-06 20-59-17](https://github.com/Sameer484/methodology/assets/110039044/68e6b4ac-ae22-4003-989d-aa38b208b3c1)


##### - Check if appending file extension results the same content when not applied. eg. browsing /home/content.css yeilds same results as /home/content
![Screenshot from 2023-06-06 21-17-17](https://github.com/Sameer484/methodology/assets/110039044/b2828ea4-c2fe-458f-9365-d9a9dd02a17a)
 
 &nbsp;
 &nbsp;



##### - If the caching server caches all the static files and you found sensitive info on any endpoint, force the caching server to cache that endpoint using path confusion attack.(sometimes appending nonexisting path maynot works).
````
example.com/account.php?name=va1   ==> this is processed by web server correctly but
example.ccom/account.php%3Fname=valsomething.css ==> caching server thinks that it should be cached.

another method using \n encoding

example.com/account.php%0Asomething.css ==> caching server often don't parse this encoding. 
````
