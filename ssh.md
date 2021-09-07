SSH
====



		apt-get install openssh-server			---	Server Side
		apt-get install openssh-client				---	Cleint Side
		service ssh start 						--	Server side

		ssh username@host.com				---	Cleint side		
		ssh username@127.0.0.1				---	Client side




Disabling root login on ssh

	$nano /etc/ssh/sshd_config
	>Search "PermitRootLogin yes"
	>Change "PermitRootLogin No"
	$service ssh restart

Note: So now if anyone want to login as root he has to login as user account first then use `su` command to login to user account if he is added to sudoers file

How to Connec to amazon intance via ssh
===========================

	Download the key 
	chmod 400 key.pem
	ssh -i root@public-ip.com



Transfering files between systems
======================
	$sftp -i key.pem ubuntu@public-ip.com
	$ls 				--> list files on remote host
	$lls 				--> list files on local host
	$put local_file.txt	 --> Upload my local_file on remote server
	$get remote_file.txt	 --> Download remote_file.txt to local machine
