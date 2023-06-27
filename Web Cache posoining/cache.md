##### If any endpoint is found that is using some caching server, then run paramminer on that endpoint. Use paramminer on JS enpoint also if they are caching js files.
&nbsp;
&nbsp;

##### Using case sensitive HOST header. VARNISH Caching server may serve as 404 not found if capitalized host header value is send.
![Screenshot from 2023-06-22 19-26-01](https://github.com/Sameer484/methodology/assets/110039044/e407fe48-de42-45a3-a33f-f1505dbce85c)
&nbsp;
&nbsp;


#### - Check if all the static files of the website are cached or not. If they are cached, find the endpoint that discloses sensitive information in the response like userinfo and session token maybe. And try to add dummy endpoint with extension js,png,avif etc.
![Screenshot from 2023-06-06 20-59-17](https://github.com/Sameer484/methodology/assets/110039044/68e6b4ac-ae22-4003-989d-aa38b208b3c1)
&nbsp;
&nbsp;

#### - Check if appending file extension results the same content when not applied. eg. browsing /home/content.css yeilds same results as /home/content
![Screenshot from 2023-06-06 21-17-17](https://github.com/Sameer484/methodology/assets/110039044/b2828ea4-c2fe-458f-9365-d9a9dd02a17a)
&nbsp;
&nbsp;

#### - If there is no reflected value in the response due the header and X-Timer header was recognized and it's value is reflected in header only , we can try to cause server error by entering large number of random value in the X-Timer header

![Screenshot from 2023-06-18 01-03-58](https://github.com/Sameer484/methodology/assets/110039044/f8b10007-ccfd-48b5-90b1-6cb0f27a96c3)


 &nbsp;
 &nbsp;
 &nbsp;
 &nbsp;

### Cache Deception

#### - If the caching server caches all the static files and you found sensitive info on any endpoint, force the caching server to cache that endpoint using path confusion attack.(sometimes appending nonexisting path maynot works).
````
example.com/account.php?name=va1   ==> this is processed by web server correctly but
example.ccom/account.php%3Fname=valsomething.css ==> caching server thinks that it should be cached.

another method using \n encoding

example.com/account.php%0Asomething.css ==> caching server often don't parse this encoding. 
````
#### After appending some random endpoint.css(or any other extensions), you may see 404 not found page. But check for view source, there may be some info leaking and check if that request has been cached or not.
![Screenshot from 2023-06-13 09-45-11](https://github.com/Sameer484/methodology/assets/110039044/aaf6360f-9f5c-4ad1-bbc9-cd51517d3a54)