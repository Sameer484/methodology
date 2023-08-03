#### Testing for prototype pollution doesn't always works with '?' , try using with hash(#) also
````
example.com?__proto__[test]=test   // typing 'test' on console doesn't output test value


example.com#__proto__[test]=test // 'test' on console outputs test value
````
---
#### Try bypassing the keyword filter. If they use replaceAll() to replace the keywords like [constructor, __proto__], bypass that function with this trick
````
example.com?__pro__proto__to[test]=test
````
---
