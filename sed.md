SED
===

Learn ed in Linux to get started in sed. Understanding how ed works will improve your understanding about sed.


Cheat Sheet
===========

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




Symbols:
======
	^	---		Beginning of The Line
	$	---		Termination of the line
	[ ]	---		Range
	&	---		Matched String
	\*      ---		OR Eg: th = t or th
	\	---		Escape Character


Options:
======
	p	---	print
	d	---	delete
	q	---	Quit
	g	---	globally
	I 	---	ignore case sensivity
	-n 	---	silent mode
	-i 	---	Make changes in file

Substituing the text
=============

	sed 's/t/T/' file.txt			---	Substitute t with T in file.txt [ It only replaces the 1st t not all]
	sed 's/t/T/g' file.txt			---	Substitute t with T in globally in file.txt
	sed -i 's/t/T/g' file.txt		---	Modify the original file




Delete the text
=============
	echo "
	imran
	nazir
	parray" | sed '/imran/d'

	nazir
	parray


Insert | Append | Change
=================
	root@root:~/Desktop# cat file
	imran
	nazir
	parray


	Inserts an text Before the matched line
	root@root:~/Desktop# sed '/imran/i\pppp\ asdasd' file
	pppp asdasd
	imran
	nazir
	parray

	Inserts an text after the matched line
	root@root:~/Desktop# sed '/imran/a\pppp asdasd' file
	imran
	pppp asdasd
	nazir
	parray

	Changes the text in the matched line
	root@root:~/Desktop# sed '/imran/c\pppp asdasd' file
	pppp asdasd
	nazir
	parray


Transform text
==========
	replace 
	a->x
	b->y
	c->z
	
	root@root:~/Desktop# echo '
	abc
	bca ' | sed 'y/abc/xyz/'

	xyz
	yzx 


printing Line Number using = sign
======================

	echo '
	a
	b
	c' | sed '/b/='

	a
	3
	b
	c


Printing Non Printable chars
==================
	-l Option prints the non printable character as two digit ascii

	root@root:~/Desktop# cat /bin/ls | sed -n -e "l" | head
	\177ELF\002\001\001\000\000\000\000\000\000\000\000\000\003\000>\000\
	\001\000\000\000\320V\000\000\000\000\000\000@\000\000\000\000\000\
	\000\000H\a\002\000\000\000\000\000\000\000\000\000@\0008\000\t\000@\
	\000\035\000\034\000\006\000\000\000\005\000\000\000@\000\000\000\000\
	\000\000\000@\000\000\000\000\000\000\000@\000\000\000\000\000\000\
	\000\370\001\000\000\000\000\000\000\370\001\000\000\000\000\000\000\
	\b\000\000\000\000\000\000\000\003\000\000\000\004\000\000\0008\002\
	\000\000\000\000\000\0008\002\000\000\000\000\000\0008\002\000\000\
	\000\000\000\000\034\000\000\000\000\000\000\000\034\000\000\000\000\
	\000\000\000\001\000\000\000\000\000\000\000\001\000\000\000\005\000\


Grouping commands
===============
	root@root:~/Desktop# cat file 
	imran
	nazir
	parray
	
	if(x=1)
	{
	print(X is one)
	}
	
	if(x==2)
	{
	print(X is two)
	}
	
	root@root:~/Desktop# cat file  | sed '/if/{
	p
	=
	}'
	imran
	nazir
	parray
	
	if(x=1)
	5
	if(x=1)
	{
	print(X is one)
	}
	
	if(x==2)
	10
	if(x==2)
	{
	print(X is two)
	}
	
	root@root:~/Desktop# 



Next line
=======
	You can select next line using n. This will search imran and then go to
	 next line and delete the whole line.


	root@root:~/Desktop# cat file  | sed '/imran/{
	n
	/^.*$/d}'
	

	imran
	parray


Quit Command
==========
	
	root@root:~/Desktop# cat file 
	imran
	nazir
	parray

	root@root:~/Desktop# cat file | sed '2q'
	imran
	nazir3


Execute multiple commands at once
==========================
    sed ‘
    s/three/3/
    s/four/4/‘ file


The script file
==========
    $cat sedscr
    s/ MA/, Massachusetts/ 
    s/ PA/, Pennsylvania/ 
    s/ CA/, California/
    s/ VA/, Virginia/
    s/ OK/, Oklahoma/

     sed -f sedsec filename



Replacing nth Occurance
================
	echo "imranimranimra" | sed 's/imran/nazir/2'

	imrannazirimran



Using Regular Expressions
=================
	echo "
	imran123
	nazir123imran" | sed 's/[0-9]/(&)/g'

	imran(1)(2)(3)
	nazir(1)(2)(3)imran




print only matched lines
==================
    by default sed will print all the lines after performing the operation.
    -n option can be used to print no lines
    but p can be used to print the matched lines 

    sed -n ‘s/three/3/p’ file.txt

    which prints only matched lines 





Substituing at the beginning of the line:
=========================

	sed 's/^t/ooo/' test.txt		---	replacing  t if they are at the beginning of the line
	sed 's/d$/ooo/' test.txt		---	replacing  d if they are at the beginning of the line


using Apersand and wildcards
===================

	sed 's/[0-5]/1/' test.txt			---	replacing anything from 0-5 and replace it with 1
	sed 's/[A-Z]m/1/' test.txt			---	replacing anything starts A-Z fallowed by m [eg: Am Bm Cm ]
	sed 's/[0-9]/(&)/' test.txt			---	replacing all mached with string inside ( ) 
	sed 's/[0-9]/(&&)/' test.txt		---	replacing all mached with string+string  inside [10 to (101)]
	sed 's/[0-9][0-9]/(&)/' test.txt		---	repcing all two digit numbers 




Using Astrick:
=========


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





Using Delimiters:
===========


	We can use anything as delimiter in SED
		Eg: sed 's/A/a/g' file.txt 			---	Here the / is the delimiter
		Eg: sed 's_A_a_g' file.txt 		---	Here the _ is the delimiter
		Eg: sed 's:A:a:g' file.txt 			---	Here the / is the delimiter
	All of them will perfrom the same function.


Using Proper Delimiters:
===============


	Using proper delimiter will always keep you away from the mess.
	
		Eg: sed 's/\/etc\/passwd\//000/' file.txt			---	Replacing /etc/passwd/ with 000  [ Full of mess]
		Eg: sed 's_/etc/passwd_000_' file.txt 			---	Replacing /etc/passwd/ with 000  [ Less Mess ] 




Using Multi Expression:
===============

		sed 's/A/a/g' file.txt 	| sed 's/Z/z/g' file.txt		---	Replacing A with a and Z with z [ Full of mess]
		sed 's/A/a/;s/Z/z/' file.txt						---	Replacing A with a and Z  with z [ Less Mess ]







Last and first Word of line
=================


	\w* 			---	First Word
	\w*$		---	Last word
	\w*.			---	First Word with space
	\w*.			---	First Word with space

	sed 's/\w*./000/' file.txt			---	Removing First word of the line with 000
	sed 's/\w*$./000/' file.txt		---	Removing last word of the line with 000







Using Not ^
=======
	sed 's/[^0-9]/*/' file.txt			---	Replace Everything which is not a number with *
	sed 's/[^0-z ]/*/g' file.txt			---	Replace Everything which is not a [0-z] means 
								Alphanumric Which means all special chars


Printing Matched Lines Only
===================
	-n	--- 	Silent Mode
 	p	---	print matched strings

	sed -n 's/imran/Nazir/gp' file.txt	---	Replace imran and Nazir and dont print Anything 
								execpt Mached lines
	sed -n 's/imran/imran/gp' file.txt	---	Seach imran and print the matched line
	sed -n 's/imran/&/gp' file.txt		---	Seach imran and print the matched line




Using Filters in File
============
	cat filters.txt
		s/[a-z]/aaa/
		s/[A-Z]/AAA/
		s/[0-9]/0000/

	sed -f filters.txt file.txt	---			Will apply all filters in the filters.tx on file.txt



Ignoring Case Sensitivity:
================
	sed 's/imRan/Nazir/'gI file.txt	---		Replace imran with Nazir without checking case-sensitivity






Find Full Works at the last and the beginning
============================
	\bWORD\b				---	Find Whole match for WORD not a partial Match 
	sed 's/\bnew\b/old/' file.txt	---	Find new everywhere and replace it with old 





Displaying Number of line in Sed
=====================
	head -n 5 file.txt	---		Displays 5 lines of file.txt
	sed '5 q' file.txt	---		Displays 5 lines of file.txt
						q -> Quit




Deleting Lines with Matched Strings:
=======================

	sed '/new/d' file.txt	 	---				Remove Lines with new 
	sed '/new/Id' file.txt 	---				Remove Lines with new without checking case 
									senstitivitty
	sed '/\bnew\b/new/Id' file.txt		---		Remove Lines with full word new
	sed '/imran$/d' file.txt			---			Remove all the line which ends with the imran
	sed '/^imran/d' file.txt			---			Remove all the line which starts with the imran





Printing the number of lines File:
=====================

	sed '=' file.txt			---	print the line number before you print the line
	sed -n '=' test.txt 		---	print the line numbers without line
	sed -n '$=' test.txt 		---	print number of line in test.txt
		-n	 	dont print any line
		$= 	 	print last line numbers
		text.txt	in file test.txt





Excluding Lines in the Seacrch Proces
========================
	
	sed '1!{/imran/nazir;}' file.txt
	
	Explaination : Sed  replace  imran with nazir but dont search in line 1 




Numbering Lines in Sed
===============

	sed '=' file.txt			---			Print Lines numbers with lines
									Eg:
									1
									new is new
									2
									old is gold
									3
									newer is badder
									4
									older is golder


	sed -n '=' file.txt				---			Print Line numbers without printing the lines

	sed -n '$=' file.txt				---			Print Last Line Number without printing the line

	sed '=' file.txt  | sed 'N ; s/\n/-- /'	--- 		prints Line numbers witn Lines on same line.				
	Explanation:     Send Number each line in file.txt and for every line N
					replace \n [new-Line-Character] with -- .

								1 new is new
								2 old is gold
								3 newer is badder
								4 older is golder
								5 news is bads


Skipping Lines:
==========	
	
	sed 'n;d' file.txt			---		Dont print line after Line print like [1 3 5 7..]
	sed '!1n;d' file.txt		---		Dont print Line after line prin but ignore 1st one so it will print like [2 4 6 8 10...]
	
	We can do it in same way:
	sed 'p;n' file.txt			---		Print lines by line but skip one line after printing a line [1 3 5 7..]
	sed 'p;n;n' file.txt		---		Print line by line but skip two lines after printing one line [1 4 7 10 ... ]








