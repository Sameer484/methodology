##### If port isn't used as cache keys
Add the port to the host header and see if cache is hit or not. We can abuse this if the reponse contain location header as below. So we can redirect users to non existent page.

![Screenshot from 2023-05-28 23-52-04](https://github.com/Sameer484/methodology/assets/110039044/68aa1781-f61f-459e-85c7-7e3f1a7ca898)

