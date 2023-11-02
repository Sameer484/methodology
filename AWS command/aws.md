### List of aws cli commands. This will make you easier to look what command to run for things that are difficult to find.

- Connecting to dynamoDB endpoint and listing the tables.
  ```
  aws dynamodb --list-tables --endpoint-url http://s3.bucket.htb
  ```
- Listing the items in tables
  ```
  aws dynamodb scan --table-name users --endpoint-url http://s3.bucket.htb
  ```
- List the available buckets from the url if bucket listing is available
  ```
  aws  --endpoint-url http://s3.bucket.htb s3api --list-buckets
  ```
- List the bucket contents
  ```
  aws s3  --endpoint-url http://s3.bucket.htb ls bucket_name_here
  ```
