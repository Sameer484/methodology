### Virtual Host discovery.
- Use the tool from github to find out the virutal hosts that are hosted on the same ip address. First find out the  ip address using `host example.com` and use it to find vhosts
  ```
  https://github.com/jobertabma/virtual-host-discovery.git

  usuage:
  ruby scan.rb --ip=192.168.1.101 --host=example.com
  ```
  ---

### Getting the ssl certificate of the website
- Openssl command
  ```
  openssl s_client -connect example.com:443
  ```
 - Finding out the domains for which the ssl is valid.
    ```
    openssl s_client -connect example.com:443 | openssl x509 -noout -text  | grep DNS:
    ```
  ---
### Finding the name server using 
`host -t ns example.com`

---
### DNS Zone transfer(copying all the zone file(dns information) from one server to another). It occurs when dns allow zone transfer for  unauthorized ip addresses.
```
host -l example.com  ns.example.com

using dig

dig axfr example.com @ns.example.com 
```
---
### BIND(Berkley Internet Name Domain) is a sofware when installed on linux makes it dns server. You can query the version of BIND installed using
```
dig chaos txt version.bind @z.hackycorp.com
```

