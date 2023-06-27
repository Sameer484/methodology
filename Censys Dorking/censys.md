#### Finding all the ip's related to the organization or common name
```
censys search ' services.tls.certificates.leaf_data.subject.common_name: "abb.com"' --index-type hosts  | jq -c '.[] | .ip' | sed 's/"\([^"]*\)"/\1/' >>censys.txt
````
