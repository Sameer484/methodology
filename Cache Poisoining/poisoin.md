- find any endpoints that are cached.(Do it even if it js files)
- Run paramminer to bruteforce headers and see if it cause some changes in the response
- Bruteforce parameter also and see if cause changes.
- Check if parameters are used as cache keys or not.
- If every parameters are used as cache keys(ie. after removing the parameter, the response doesn't give same result), then try using utm_content parameter and check if it is used as cache key or not.
- If no cache buster is found(?cb=1 cause cache to miss) , then try Origin header. Cloudflare use it as default cache key
- In every cached response, check for FAT Get request using paramminer and see if it changes the response.

  ---
- Append any random endpoints in the cached request. /random and see what happens. See if the response changes. Check if the "random" is reflected , can we do xss here? If value is reflected but encoded, cached the reponse using burp and send the link to victim
  ````
  GET /random<script>alert(2)</script>
  ````
