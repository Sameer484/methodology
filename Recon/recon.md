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
