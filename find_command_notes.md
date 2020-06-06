	
Finding Files
------------------------
#### By Name:
	------------	
	locate NAME
	locate *.extension
	find / -name nmap				---	Find from root all file with name "nmap"
	find / -iname nmap				---	Find from root all file with name "nmap" regardless of case sensitive
	find / -name 'nmap*'				---	Find from root all files with starting name as root
	find / -name 'nm??'				---	Find from root all files with starting name as root
	find / -name 'nm??*'				---	Find from root all files with starting name as nm and the two chars or more
	find ~ -iname '*.txt'				---	Find all the files in the root directory with txt extension
	find /usr/share -name '*nmap*'			---	Find all the files in the /usr/share which contains text nmap
	
#### Bysize:
	-------
	
	find . -size 300b				---	Find all file with size 300 bytes
	find . -size +300b				---	Find all file with size more than 300 bytes
	find . -size -300b				---	Find all file with size less than 300 bytes
	find ~ -empty 					---	Find all file with emptysize
	
	
#### ByTime:
	-------
	
	find ~ -mtime 1					---	Find all the files which were modiefied before one day [24 hours]
	find ~ -mmin 5					---	Find all the files which were modified befire 5 minutes
	find / -mtime 2 -mtime -4 			---	Find all the files which were modified before 2 to 4 days
	
	
#### By owners:
	----------
	
	find /usr/share/fonts -user imran		---	Find all the files in /usr/share/fonts owened by imran
	find /dev -group hackers			---	Find all the fiels in /dev which are owened by group hackers
	
	
#### Finding and Executing commands on Found files:
----------------------------------------------
	
	find . -name '*.html' -exec cat '{}' ';'		---	Find all the files with html extension and execute cat command in them
									here {} represents the set of files found by found command
	
	find . -name '*.html' -ok rn '{}' ';'			---	Find all the html files and check which command will be executed on them just to confirm
									the removal of files. This is a test command and it should be run before -exec
	
	
	
#### combining things:
-----------------
	find / -name '*.html' -size +300b 			---	Find all the html files who size more than 300
	 
	
