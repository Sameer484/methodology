````
ssl:"target.com"
ssl.subject.cert.CN:"target.com"
asn:AS1234
````
#### Cli command to grab subdomains
`shodan search ssl:weather.com --fields hostnames | tr ";" "\n" | grep -e ".*.weather.com"`
