### Check this blog out for more information about read/write misconfiguration on firebase database.
```
https://blog.securitybreached.org/2020/02/04/exploiting-insecure-firebase-database-bugbounty/
```
Just try appending https://*.firebaseio.com/.json and it may dump entire database. 
You should get permission denied if the firebase is configured correctly.
## check this blog for reference.
```
https://medium.com/@facu.tha/critical-misconfiguration-in-firebase-e682ec4239d6
```
