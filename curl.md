cURL
====


__GET request__
```console
curl http://example.com/posts/3
```


__Show only head of the response__
```console
curl --head http://www.example.com/posts/3				 
```

__Save the Output to output.txt file__
```console
curl -o output.txt http://www.example.com/posts/3			 
```


__Download the Remote File__
```console
curl -O http://www.example.com/posts/3					 
```
  

__Sending Post Requests:__
```console
curl --data "username=admin&password=admin" http://www.example.com/login
curl --d "username=admin&password=admin" http://www.example.com/login
```

__Put requests:__
```console
curl -X PUT -d curl --data "title=change me" http://example.com/posts/3
```

__Delete Request:__
```console
curl -X DELETE http://www.example.com/posts/3
```

__Adding Authantication:__
```console
curl -u username:password http://www.example.com/posts/3
```


__Curl and FTP__
```console
Uploading: curl -u account@website.com:password  -T local_file.txt ftp://ftp.example.com
Donwloading: curl -u account@website.com:password -O ftp://ftp.example.com/ftp_file.txt
```
__Show req/res headers:__
```console
curl -i http://www.example.com/posts/3
```


__Fallow Redirection:__
```console
curl -L http://www.example.com/posts/3
```

__Output:__
```console
[verbose]          curl -v http://www.example.com/posts/3
[Too Verbose]      curl -vv http://www.example.com/posts/3
[silent]           curl -s http://www.example.com/posts/3

```

__User Agent__
```console
curl -A "User Agent String" http://www.example.com/posts/3
```

__Adding Cookies to Requests__
```console
curl -b name=value http://www.example.com/posts/3
```

__Adding Cookies to Requests from file__
```console
curl -b cookies.txt http://www.example.com/posts/3
```


__Adding Custom Headers to Requests__
```console
curl -H "Header:Value" http://www.example.com/posts/3
```


__Use Compression [deflate/gzip]__
```console
curl --compressed http://www.example.com/posts/3
```

__Save response to file__

```console
curl -o results.txt http://www.example.com/posts/3
```
