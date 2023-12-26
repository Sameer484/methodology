### If the server allow for uploading the executable file like test.php but the server doesn't execute the file instead render as it is, then the directory may be set as non-executable using apache config file
- uploading test.php as `<? php exec('ls');?>` and accessing the file http://localhost/files/test.php render the file as it is
![image](https://github.com/Sameer484/methodology/assets/110039044/548956cb-c617-45da-94c8-cf230cb3e05c)

If you came across this point, then try uploading the file to another directory by path traversal ie. renaming the file ../test.php (try url encoding if this traversal method fails)
