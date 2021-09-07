Dig
===


Asking Specific Name Server:
===================

	dig google.com 							A record
	dig @nameserver google.com 				Querying any specific name server
	dig @nameserver google.com MX 				Querying MX records
	dig google.com +short 						Show only resolved A records [only ip addresses]


Asking Specific DNS record:
==================

	dig +nocmd example.com A +noall +answer
	dig +nocmd example.com NS +noall +answer
	dig +nocmd example.com MX +noall +answer
	dig +nocmd example.com TXT +noall +answer
	dig +nocmd example.com SOA +noall +answer
	dig +nocmd example.com ANY +noall +answer (This rarely works)



Reverse Lookup
===========
	dig -x 104.27.179.12                             Reverse Lookup


Zone Transfers:
==========
	dig -t NS zonetransfer.me +short					---	Finding name Servers
	dig -t AXFR zonetransfer.me @nsztm1.digi.ninja 		---	Requesting zone files from NS1
	dig -t AXFR zonetransfer.me @nsztm2.digi.ninja		---	Requesting zone files from NS2


