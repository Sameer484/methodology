##### TOOLS 
- wpscan

##### ENDPOINTS
- wp-json/wp/v2/users/ ===> users/admin names information disclosure. Maynot be eligible for bounty as author usernames are public by default
- wp-json/wp/v2/pages  ===> could leak ip addresses
- xmlrpc.php ====>send the post request with the following data
````
                <?xml version="1.0" encoding="utf-8"?>
                <methodCall> 
                <methodName>system.listMethods</methodName> 
                <params></params> 
                </methodCall>

````
- /wp-admin/setup-config.php?step=1  ===> may give access to create new database if they forgot to configure the database
