__Lets Say we have a input file__
```console
root@root:~/Desktop/temp# cat file.txt 
name:age:color
one:1:111
two:2:222
three:3:333

```



__Reading Bytes__
```console
root@root:~/Desktop/temp# cat file.txt | cut -b 1
n
o
t
t

root@root:~/Desktop/temp# cat file.txt | cut -b 1,2,3
nam
one
two
thr

```



__Reading Byte Range__
```console
root@root:~/Desktop/temp# cat file.txt | cut -b 1-3
nam
one
two
thr

root@root:~/Desktop/temp# cat file.txt | cut -b -4     [Starting to 4]
name
one:
two:
thre


root@root:~/Desktop/temp# cat file.txt | cut -b 2-     [start from 2 to end]
ame:age:color
ne:1:111
wo:2:222
hree:3:333

```



__Reading 1 character__
```console

root@root:~/Desktop/temp# cat file.txt | cut -c 1
n
o
t
t
```

__Reading 1-3 characters__
```console

root@root:~/Desktop/temp# cat file.txt | cut -c 1-3
nam
one
two
thr
```

__Reading starting-3 characters__
```console
root@root:~/Desktop/temp# cat file.txt | cut -c -3
nam
one
two
thr
```

__Reading characters from 3 to end__
```console

root@root:~/Desktop/temp# cat file.txt | cut -c 3-
me:age:color
e:1:111
o:2:222
ree:3:333

```





__Using Delimiter to extract 1st field__
```console
root@root:~/Desktop/temp# cat file.txt | cut -d":" -f1
name
one
two
three
```

__Using Delimiter to extract 1st and 2nd field__
```
root@root:~/Desktop/temp# cat file.txt | cut -d":" -f1,2
name:age
one:1
two:2
three:3
```



__Using reverse Match (Not gate)__
```console

root@root:~/Desktop/temp# cat file.txt | cut -d":" -f1,2
name:age
one:1
two:2
three:3

root@root:~/Desktop/temp# cat file.txt | cut -d":" -f1,2 --complement
color
111
222
333

```



__Using Output Delimiters__
```console
root@root:~/Desktop/temp# cat file.txt | cut -d":" -f1,2 --output-delimiter=~
name~age
one~1
two~2
three~3

root@root:~/Desktop/temp# cat file.txt | cut -d":" -f1,2,3 --output-delimiter=~
name~age~color
one~1~111
two~2~222
three~3~333

```



__Example 1: Removing protocols from Urls__
```console
root@root:~/Desktop/temp# cat file.txt 
https://google.com
https://facebook.com
https://imran.com
http://example.com


root@root:~/Desktop/temp# cat file.txt | cut -d"/" -f3
google.com
facebook.com
imran.com
example.com

```



__Example 2: Extracting Domains from URLS__
```console
root@root:~/Desktop/temp# cat file.txt 
https://google.com?name=imran&age=xxx&age=xxx
https://facebook.com?name=imran&age=xxx&age=xxx&age=xxx
https://imran.com?name=imran&age=xxx&age=xxx&age=xxx
http://example.com?name=imran&age=xxx&age=xxx


root@root:~/Desktop/temp# cat file.txt | cut -d"?" -f1
https://google.com
https://facebook.com
https://imran.com
http://example.com

```



__Example 3 : Extracting Keys/Values from JSON Object__
```console
root@root:~/Desktop/temp# cat file.txt 
{
"a":"1",
"b":"2",
"c":"3",
}


root@root:~/Desktop/temp# cat file.txt | cut -d'"' -f2
{
a
b
c
}


root@root:~/Desktop/temp# cat file.txt | cut -d'"' -f4
{
1
2
3
}

```
