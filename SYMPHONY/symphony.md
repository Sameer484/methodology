#### ENDPOINTS
don't forget to test this endpoints
- app_dev.php
- portal/app_dev.php
- app_dev.php/_profiler
- portal/app_dev.php/_profiler
- _profiler

##### Try to append _METHOD=main_method .eg _METHOD=POST to bypass CSRF
````
POST /api/user/1?_method=delete

````
