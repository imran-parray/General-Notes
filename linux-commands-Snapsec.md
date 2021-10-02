## PS

__list terminal process__
```console
ps -a
```


__list all processes__
```console
ps -x
```


__kill a process__
```console
kill <PID>
```


## uname

__list system info__
```console
uname -a
```

## df
__list all disks__
```console
df -a
```


__list all information in Human Readable Format__
```console
df -h
```

## cut

__Lets Say we have a input file__
```console
root@root:~/Desktop/temp# cat file.txt 
name:age:color
one:1:111
two:2:222
three:3:333

```



__Reading Byte 1__
```console
root@root:~/Desktop/temp# cat file.txt | cut -b 1
n
o
t
t
```

__Reading Byte 1,2 and 3__
```console
root@root:~/Desktop/temp# cat file.txt | cut -b 1,2,3
nam
one
two
thr

```



__Reading Byte Range from 1-3__
```console
root@root:~/Desktop/temp# cat file.txt | cut -b 1-3
nam
one
two
thr
```


__Reading Byte range from 1-4__
```console

root@root:~/Desktop/temp# cat file.txt | cut -b -4     [Starting to 4]
name
one:
two:
thre
```


__Reading Byte 2-end__
```console

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

root@root:~/Desktop/temp# cat file.txt | grep ':'
"a":"1",
"b":"2",
"c":"3",

root@root:~/Desktop/temp# cat file.txt | grep ':' | cut -d':' -f1
"a"
"b"
"c"

root@root:~/Desktop/temp# cat file.txt | grep ':' | cut -d':' -f2
"1",
"2",
"3",
root@root:~/Desktop/temp# 

```

## Grep
__Lets Say we have a input file__
```console
root@root:~/Desktop/temp# cat file.txt 
name:age:color
one:1:111
two:2:222
three:3:333

```



__Reading Byte 1__
```console
root@root:~/Desktop/temp# cat file.txt | cut -b 1
n
o
t
t
```

__Reading Byte 1,2 and 3__
```console
root@root:~/Desktop/temp# cat file.txt | cut -b 1,2,3
nam
one
two
thr

```



__Reading Byte Range from 1-3__
```console
root@root:~/Desktop/temp# cat file.txt | cut -b 1-3
nam
one
two
thr
```


__Reading Byte range from 1-4__
```console

root@root:~/Desktop/temp# cat file.txt | cut -b -4     [Starting to 4]
name
one:
two:
thre
```


__Reading Byte 2-end__
```console

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

root@root:~/Desktop/temp# cat file.txt | grep ':'
"a":"1",
"b":"2",
"c":"3",

root@root:~/Desktop/temp# cat file.txt | grep ':' | cut -d':' -f1
"a"
"b"
"c"

root@root:~/Desktop/temp# cat file.txt | grep ':' | cut -d':' -f2
"1",
"2",
"3",
root@root:~/Desktop/temp# 

```



## Sed



Learn ed in Linux to get started in sed. Understanding how ed works will improve your understanding about sed.


__Cheat Sheet__

```
:  # label
=  # line_number
a  # append_text_to_stdout_after_flush
b  # branch_unconditional             
c  # range_change                     
d  # pattern_delete_top/cycle          
D  # pattern_ltrunc(line+nl)_top/cycle 
g  # pattern=hold                      
G  # pattern+=nl+hold                  
h  # hold=pattern                      
H  # hold+=nl+pattern                  
i  # insert_text_to_stdout_now         
l  # pattern_list                       
n  # pattern_flush=nextline_continue   
N  # pattern+=nl+nextline              
p  # pattern_print                     
P  # pattern_first_line_print          
q  # flush_quit                        
r  # append_file_to_stdout_after_flush 
s  # substitute                                          
t  # branch_on_substitute              
w  # append_pattern_to_file_now         
x  # swap_pattern_and_hold             
y  # transform_chars    
```




__Symbols:__

	^	---		Beginning of The Line
	$	---		Termination of the line
	[ ]	---		Range
	&	---		Matched String
	\*      ---		OR Eg: th  t or th
	\	---		Escape Character


__Options:__

	p	---	print
	d	---	delete
	q	---	Quit
	g	---	globally
	I 	---	ignore case sensivity
	-n 	---	silent mode
	-i 	---	Make changes in file

__Substituing the text__


	sed 's/t/T/' file.txt			---	Substitute t with T in file.txt [ It only replaces the 1st t not all]
	sed 's/t/T/g' file.txt			---	Substitute t with T in globally in file.txt
	sed -i 's/t/T/g' file.txt		---	Modify the original file




__Delete the text__

	echo "
	imran
	nazir
	parray" | sed '/imran/d'

	nazir
	parray




__Transform text__

	replace 
	a->x
	b->y
	c->z
	
	root@root:~/Desktop# echo '
	abc
	bca ' | sed 'y/abc/xyz/'

	xyz
	yzx 








__The script file__

    $cat sedscr
    s/ MA/, Massachusetts/ 
    s/ PA/, Pennsylvania/ 
    s/ CA/, California/
    s/ VA/, Virginia/
    s/ OK/, Oklahoma/

     sed -f sedsec filename



__Replacing nth Occurance__

	echo "imranimranimra" | sed 's/imran/nazir/2'

	imrannazirimran








__Substituing at the beginning of the line:__


	sed 's/^t/ooo/' test.txt		---	replacing  t if they are at the beginning of the line
	sed 's/d$/ooo/' test.txt		---	replacing  d if they are at the beginning of the line


__using Apersand and wildcards__


	sed 's/[0-5]/1/' test.txt			---	replacing anything from 0-5 and replace it with 1
	sed 's/[A-Z]m/1/' test.txt			---	replacing anything starts A-Z fallowed by m [eg: Am Bm Cm ]
	sed 's/[0-9]/(&)/' test.txt			---	replacing all mached with string inside ( ) 
	sed 's/[0-9]/(&&)/' test.txt		---	replacing all mached with string+string  inside [10 to (101)]
	sed 's/[0-9][0-9]/(&)/' test.txt		---	repcing all two digit numbers 




__Using Astrick:__



	sed 's/Th*/00/' test.txt			---	replacing all T and Th with 00
	sed 's/Thr*/00/' test.txt			---	replacing all Th and Thr with 00
	sed 's/There*/00/' test.txt		---	replacing all Ther and There with 00
	sed 's/[0-9][0-9]*/00/' test.txt	---	replacing all one digit and two digit numbers with 00

	sed 's/[a-z]/00/' test.txt			---	replacing all small alphabits with 00
	sed 's/[a-z][A-Z]/00/' test.txt		---	replacing all small alphabits with 00 [Eg: t -> 00 and tH->00 ]
	sed 's/[A-Z]/00/' test.txt			---	replacing all A-Z  with 00
	sed 's/[a-zA-Z]/00/' test.txt		---	replacing all a-zA-Z  with 00
	OR
	sed 's/[A-z]/00/' test.txt			---	replacing all a-z A-Z  with 00
	sed 's/[0-z]/00/' test.txt			---	replacing all numbers and alphbits  with 00





__Using Delimiters:__



	We can use anything as delimiter in SED
		Eg: sed 's/A/a/g' file.txt 			---	Here the / is the delimiter
		Eg: sed 's_A_a_g' file.txt 		---	Here the _ is the delimiter
		Eg: sed 's:A:a:g' file.txt 			---	Here the / is the delimiter
	All of them will perfrom the same function.


__Using Proper Delimiters:__



	Using proper delimiter will always keep you away from the mess.
	
		Eg: sed 's/\/etc\/passwd\//000/' file.txt			---	Replacing /etc/passwd/ with 000  [ Full of mess]
		Eg: sed 's_/etc/passwd_000_' file.txt 			---	Replacing /etc/passwd/ with 000  [ Less Mess ] 















__Using Not ^__

	sed 's/[^0-9]/*/' file.txt			---	Replace Everything which is not a number with *
	sed 's/[^0-z ]/*/g' file.txt			---	Replace Everything which is not a [0-z] means 
								Alphanumric Which means all special chars




