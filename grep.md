
__Input file__

```console
Imrans-Air:temp imranparray$ cat file.txt 
Hello world
i am line 1
i am line 2
44444
55555

```

__Case insenstivity__
```console
Imrans-Air:temp imranparray$ cat file.txt | grep 'h'
Imrans-Air:temp imranparray$ cat file.txt | grep -i 'h'
Hello world
```

__Reverse Match__
```console
Imrans-Air:temp imranparray$ cat file.txt | grep 'am'
i am line 1
i am line 2
Imrans-Air:temp imranparray$ cat file.txt | grep -v 'am' 
Hello world
44444
55555


```

__No of Matches__
```console
Imrans-Air:temp imranparray$ cat file.txt | grep -c 'am' 
2

```

__Searching Regular Expressions__
```console
Imrans-Air:temp imranparray$ cat file.txt | grep -E '\d{5}' 
44444
55555
```

__Get the Search pattern from the file__
```console
Imrans-Air:temp imranparray$ echo '\d{5}' > pattern
Imrans-Air:temp imranparray$ cat file.txt | grep -Ef pattern 
44444
55555

```

__Print the source of input__
```console
Imrans-Air:temp imranparray$ cat file.txt | grep -H 'am'
(standard input):i am line 1
(standard input):i am line 2
Imrans-Air:temp imranparray$ grep -H 'am' file.txt 
file.txt:i am line 1
file.txt:i am line 2

```

__Print Line number where the match is found__
```console
Imrans-Air:temp imranparray$ cat file.txt | grep -n 'am'
2:i am line 1
3:i am line 2

```

__print n number of line after last match__
```console
Imrans-Air:temp imranparray$ cat file.txt | grep -A 1 -n 'am'
2:i am line 1
3:i am line 2
4-44444

```

__print n number of line before first match__
```console
Imrans-Air:temp imranparray$ cat file.txt | grep -B 1 -n 'am'
1-Hello world
2:i am line 1
3:i am line 2
```

__print only matching part__
```console
Imrans-Air:temp imranparray$ cat file.txt | grep -o 'am'
am
am

```

__Add color to mached patterns__
```console
Imrans-Air:temp imranparray$ cat file.txt | grep 'am' --color
i am line 1
i am line 2

```
