# Nmap scanning

## Basics Concepts


__MAC__

- 48 bits
- 6 bytes long
- Hex representation

DE:AD:BE:EF:CA:FE

- First 6 is OUI (Org unique identifier)
- Last 6 is extension indentifier

__IPV4__

- 32 bit address
- 4 octets
- Can be represented as Decimal 3232323232
- Can be represented as HEX C0A8010
- 2^32 Addressse possible (4.3 billion)

__Fregmentation__

Some network has MTU (maximum transmission unit) which is the maximu packet size that can be send over netowrk so sometime
packets need to be broke down in smaller units called the process of fragmentation.


__Classful Netoworks__

The Huge 1.4 billion ip addresses are converted in small classes 

| Class  | Range  | Leading Bits  |
|---|---|---|
| A  | 1.6 million  | 0  |
| B  |  65535 | 10  |
| C  |  256 |  110 |
| D  | Undefined  |  1110 |
| E  | Undefined  | 1111  |



__ARP:__

- Adress Resolution protocol 
- Used to find the Layer 2 Mac addresses for Layer 3 Ip addresses

__ICMP:__

- Internet control message Protocol
- Use to help other protocols
- Used for troubleshooting and error reporting
- Uses Types and codes instead of ports


__PING:__
__TCP:__
__PORTS:__
__Traceroute:__





__Connect Scan__ (-sT)

Open port:

- A --> Syn --> B
- A <-- Syn Ack <-- B
- A --> ACK --> B
- A --> RST/ACK --> B (To Reset/Close the connection)

Close Port:

- A --> Syn --> B
- A <-- RST/Ack <-- B


__Syn Scan__ (-sS)

Open port:

- A --> Syn --> B
- A <-- SYN/ACK <-- B
- A --> RST --> B (To Reset/Close the connection)


Close Port:

- A --> Syn --> B
- A <-- RST/Ack <-- B

### Port Status

|Status | Meaning |
|---|---|
|Closed | ICMP Port Unrecheable error |
|Filtered | ICMP Port Unrecheable error |
|Open/Filtered | No response |
|Open | Any Response |


## Scanning

__Simple scan__

```console
root@root:~# nmap localhost

```

__Simple TCP scan__ (Explicit 3 way handshake scan)

```console
root@root:~# nmap -sT localhost

```



__Simple UDP Scan__

```console
root@root:~# nmap -sU localhost

```



__Nmap OS scan__
```console
root@root:~# nmap -p80 -O localhost

```



__Nmap Service Detection__
```console
root@root:~# nmap -sV -p80 localhost

```



__Dont ping just Scan__
```console

root@root:~# nmap -PN -p80 localhost

```



__Nmap Aggressive Scan__
```console
root@root:~# nmap -A localhost


```


__Nmap ACK Scan__
```console
root@root:~# nmap -sA localhost

```



__Nmap FIN Scan__ (Use fin Packets)
```console
root@root:~# nmap -sF localhost

```
__Nmap ACK Scan__
```console
root@root:~# nmap -sA localhost

```
__Nmap Xmas Scan__
```console
root@root:~# nmap -sX localhost

```

__Nmap Fast Mode__ (Top 100 Ports)
```console
root@root:~# nmap -F localhost

```

### Different Ping Scans

__No port scanning__ (to check if the host is up)

```console
root@root:~# nmap 127.0.0.1-5 -sn 
```
__ARP ping scan__
```console
nmap -PR 127.0.0.1
```


__No ping Scan__
```console
nmap -Pn 127.0.0.1
```
__ICMP ping Scan__
```console
nmap -PI 127.0.0.1
```
__ICMP Echo ping Scan__
```console
nmap -PE 127.0.0.1
```

__No Timestamp Scan__
```console
nmap -PP 127.0.0.1
```
__SYN ping Scan__ (Much like SYN scan but with ACK)
```console
nmap -PP 127.0.0.1
```

__UDP ping Scan__
```console
nmap -PU 127.0.0.1
```

__TCP ping Scan__
```console
nmap -P 127.0.0.1


```



__Nmap Protocol Scan__
```console
nmap -sO 127.0.0.1
```


__Nmap DNS lookup Scan__
```console
nmap -sL 127.0.0.1
```

__Nmap Never DNS lookup Scan__
```console
nmap -n 127.0.0.1
```


__Nmap Traceroute Scan__
```console
nmap --traceroute google.com
```



### Wildcards

The targets can be specified in 3 different ways

- Wildcards -- 192.168.43.*
- Range     -- 192.168.0-255.0-255
- CIDR      -- 192.168.0.0/16

### Options:

```console
nmap 192.168.43.*
```
```console
nmap 192.168.43.0-255
```
```console
nmap 192.168.43.0/10
```



### Other Options:

__Nmap debug mode__
```console
nmap -p80 localhost -d
```

__Nmap More debug mode__
```console
nmap -p80 localhost -ddd
```

__Randomize Hosts while scanning__
```console
root@root:~# nmap 192.168.43.200-239 --randomize_hosts -f
```

__Specify Network Interface__
```console
root@root:~# nmap 192.168.43.200-239 --randomize_hosts -f
```


__Nmap Use packets fragmentation__
```console
root@root:~# nmap 192.168.43.239 -f
```


__Nmap Verbose__
```console
root@root:~# nmap 192.168.43.239 -v
```

__Nmap Very Verbose__
```console
root@root:~# nmap 192.168.43.239 -vv
```

__Nmap show Reason__
```console
root@root:~# nmap 192.168.43.239 -p80,21 --open --reason
```

__To exclude the Host__
```console
nmap 127.0.0.1-255 --exclude 127.0.0.1
```
__Input list__
```console
nmap 127.0.0.1-255 -iL hosts.txt
```

__Exclude the range of ip addresses__
```console
nmap 127.0.0.1-255 --excludefile hosts.list
```


## Script Engine

__Simple Script scan__

```console
nmap 192.168.43.* --script script-name
```



__Default Script scan__

```console
nmap 192.168.43.* -sC script-name
```


__Catogary Script scan__

```console
nmap 192.168.43.* --script safe|intrusive|malware|version|discovery|vuln|auth|default
```



## Ports

__Top 1000 Ports__

```console
nmap 192.168.43.*
```


__All ports__
```console
nmap -p- localhost
```

__Port range__
```console
nmap -p 0-65535 localhost
```


__All from 1-3__
```console
nmap 192.168.43.* -p1-3


__All from 1-3__
```console
nmap 192.168.43.* -p-3
```



__All from 1 to all__
```console
nmap 192.168.43.* -p1-
```

__Specific Ports__

```console
nmap 192.168.43.1/24 -p 80
```


__Top Ports__

```console
nmap 192.168.43.1/24 --top-ports 500 80
```



__TCP and UDP Ports__

```console
nmap 192.168.43.1/24 -p T:80,U:53
```


__Show only open ports__

```console
root@root:~# nmap 192.168.43.239 -p- --open

```


__Mixed Style__

```console
root@root:~# nmap 192.168.43.239 -p80,21-25,8080-8090 --open

```


## Logging

__Show All packets Send and Receaved__
```console
nmap localhost --packet-trace
```



__Nmap Simple Human Normal Output__

```console
root@root:~# nmap 192.168.43.239 -p- -oN output.file

```


__Nmap Simple XML Redeable Output__

```console
root@root:~# nmap 192.168.43.239 -p- -oX output.file
```


__Nmap Simple Grepabel Output__

```console
root@root:~# nmap 192.168.43.239 -p- -oG output.file

```


__Nmap Simple All Output__

```console
root@root:~# nmap 192.168.43.239 -p- -oA output.file

```


## Os and Version detectio
_Nmap OS detection needs atleast one Open port and One closed Port on the machine.

__default os scan__
```console
nmap -O 192.168.43.239
```



__Nmap Service Detection__
```console
root@root:~# nmap -sV -p80 localhost

```


__Limit Os scan__(Dont waste too much time if you are not able to detect OS)
```console
nmap -O --osscan-limit 192.168.43.239
```


__Aggresive Os scan__(Spend too much time if you are not able to detect OS)
```console
nmap -O --osscan-guess 192.168.43.239
```

__Version Intensity__ (level=1,2,3,4,5,7,8,9)
```console
nmap 192.168.43.239 --version-intensity <level> 
```



__High Version Intensity__ (level=9)
```console
nmap 192.168.43.239 --version-all 
```



## Performance

__Min Parallelism__(minimum hosts to be scanned parallely)
```console
nmap 192.168.43.0-255 --min-parallelism 10

```

__Max Parallelism__(Maximum hosts to be scanned parallely)
```console
nmap 192.168.43.0-255 --max-parallelism 10

```


__Host Timeout__(give up on this target after this time default:30min)
```console
nmap 192.168.43.0-255 --host-time <time>
```

__Min Packet Rate__(rate can be 1-100000000000)
```console
nmap 192.168.43.0-255 --min-rate <Number>
```


__Max Packet Rate__(rate can be 1-100000000000)
```console
nmap 192.168.43.0-255 --max-rate <Number>
```

__Scan delay__(Adjust delay between probes)
```console
nmap 192.168.43.0-255 --scan-delay <time>
```
__Performance template__(-T(1|2|3|4|5)
```console
nmap 192.168.43.0-255 -T1
```

__T1__
```console
  hostgroups: min 1, max 100000
  rtt-timeouts: init 15000, min 100, max 15000
  max-scan-delay: TCP 1000, UDP 1000, SCTP 1000
  parallelism: min 0, max 1
  max-retries: 10, host-timeout: 0
  min-rate: 0, max-rate: 0

```

__T2__
```console
  hostgroups: min 1, max 100000
  rtt-timeouts: init 1000, min 100, max 10000
  max-scan-delay: TCP 1000, UDP 1000, SCTP 1000
  parallelism: min 0, max 1
  max-retries: 10, host-timeout: 0
  min-rate: 0, max-rate: 0

```

__T3__
```console
  hostgroups: min 1, max 100000
  rtt-timeouts: init 1000, min 100, max 10000
  max-scan-delay: TCP 1000, UDP 1000, SCTP 1000
  parallelism: min 0, max 0
  max-retries: 10, host-timeout: 0
  min-rate: 0, max-rate: 0

```

__T4__
```console
  hostgroups: min 1, max 100000
  rtt-timeouts: init 500, min 100, max 1250
  max-scan-delay: TCP 10, UDP 1000, SCTP 10
  parallelism: min 0, max 0
  max-retries: 6, host-timeout: 0
  min-rate: 0, max-rate: 0

```

__T5__
```console
  hostgroups: min 1, max 100000
  rtt-timeouts: init 250, min 50, max 300
  max-scan-delay: TCP 5, UDP 1000, SCTP 5
  parallelism: min 0, max 0
  max-retries: 2, host-timeout: 900000
  min-rate: 0, max-rate: 0
```


### How it works

#### How OS detection Works
> There is an file `/usr/share/nmap/nmap-os-db` which contain the patterns like this

```
CPE cpe:/h:2wire:1701hg
SEQ(SP=7E-9A%GCD=1-6%ISR=9E-A8%TI=I%TS=A)
OPS(O1=M5ACNNSW0NNNT11%O2=M578NNSW0NNNT11%O3=M280W0NNNT11%O4=M218NNSW0NNNT11%O5=M218NNSW0NNNT11%O6=M109NNSNNT11)
WIN(W1=8000%W2=8000%W3=8000%W4=8000%W5=8000%W6=8000)
ECN(R=Y%DF=Y%T=FA-104%TG=FF%W=8000%O=M5ACNNSW0N%CC=N%Q=)
T1(R=Y%DF=Y%T=FA-104%TG=FF%S=O%A=O|S+%F=AS%RD=0%Q=)
T2(R=N)
T3(R=N)
T4(R=Y%DF=Y%T=FA-104%TG=FF%W=0%S=A%A=Z%F=R%O=%RD=E44A4E43%Q=)
T5(R=Y%DF=Y%T=FA-104%TG=FF%W=0%S=Z%A=S+%F=AR%O=%RD=BD1AB510%Q=)
T6(R=Y%DF=Y%T=FA-104%TG=FF%W=0%S=A%A=Z%F=R%O=%RD=EA6C967D%Q=)
T7(R=N)
U1(DF=Y%T=FA-104%TG=FF%IPL=70%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)
```






#### How nmap Detect Services

> There is an file `/usr/share/nmap/nmap-services` which contain the list of port number and an expected services on those port
```
vettcp	78/tcp	0.000000
vettcp	78/udp	0.000626
finger	79/tcp	0.006022
finger	79/udp	0.000956
http	80/sctp	0.000000	# www-http | www | World Wide Web HTTP
http	80/tcp	0.484143	# World Wide Web HTTP
http	80/udp	0.035767	# World Wide Web HTTP
hosts2-ns	81/tcp	0.012056	# HOSTS2 Name Server
hosts2-ns	81/udp	0.001005	# HOSTS2 Name Server
xfer	82/tcp	0.002923	# XFER Utility
xfer	82/udp	0.000659	# XFER Utility
mit-ml-dev	83/tcp	0.000539	# MIT ML Device
mit-ml-dev	83/udp	0.001203	# MIT ML Device
ctf	84/tcp	0.000276	# Common Trace Facility
ctf	84/udp	0.000610	# Common Trace Facility
mit-ml-dev	85/tcp	0.000690	# MIT ML Device
mit-ml-dev	85/udp	0.000610	# MIT ML Device
mfcobol	86/tcp	0.000138	# Micro Focus Cobol

```

So even starting an `HTTP server` on port `3306` will result showing up `Mysql` detected by `Nmap`.

```console
root@root:~# python -m SimpleHTTPServer 3306
Serving HTTP on 0.0.0.0 port 3306 ...

```

```console
root@root:~# nmap localhost
Starting Nmap 7.70 ( https://nmap.org ) at 2020-03-24 19:22 HDT
Nmap scan report for localhost (127.0.0.1)
Host is up (0.0000060s latency).
Other addresses for localhost (not scanned): ::1
Not shown: 998 closed ports
PORT     STATE SERVICE
80/tcp   open  http
3306/tcp open  mysql

```

But using `-sV` scan flag will actually force nmap to communicate to the server and detect the service 

> There is an aother file called `/usr/share/nmap/nmap-service-probes` which containes the regular expression to detect services based on the response 

Let search `SimpleHTTPServer` in the file

```console
root@root:/usr/share/nmap# cat nmap-service-probes  | grep SimpleHTTPServer
match http m|^HTTP/1\.0 501 Not Implemented\r\nServer: SimpleHTTP/([\w._-]+) Python/([\w._-]+)\r\n.*Content-Type: text/html\r\nConnection: close\r\n\r\n<head>\n<title>Error response</title>\n</head>\n<body>\n<h1>Error response</h1>\n<p>Error code 501\.\n<p>Message: Not Implemented\.\n<p>Error code explanation: 501 = Server does not support this operation\.\n</body>\n$|s p/SimpleHTTPServer/ v/$1/ i/rPath Appliance Platform Agent; Python $2/ cpe:/a:python:python:$2/ cpe:/a:python:simplehttpserver:$1/
match http m|^HTTP/1\.0 200 OK\r\nServer: SimpleHTTP/([\d.]+) Python/([\d.]+)\r\n| p/SimpleHTTPServer/ v/$1/ i/Python $2/ cpe:/a:python:python:$2/ cpe:/a:python:simplehttpserver:$1/

```

You can see that if `^HTTP/1\.0 200 OK\r\nServer: SimpleHTTP/([\d.]+)` is matched with any of the response it will be marked as http. 

So i tried to communicate with the SimpleHTTPServer with Curl to see the response Here is what i saw

```http
root@root:/usr/share/nmap# curl -I localhost:3306
HTTP/1.0 200 OK
Server: SimpleHTTP/0.6 Python/2.7.15+
Date: Wed, 25 Mar 2020 04:42:01 GMT
Content-type: text/html; charset=UTF-8
Content-Length: 3614


```
You can see the ` SimpleHTTP/0.6` matching `SimpleHTTP/([\d.]+)` Regex which confimed nmap that its an http service.


```console
root@root:~# nmap -sV localhost
Starting Nmap 7.70 ( https://nmap.org ) at 2020-03-24 19:27 HDT
Nmap scan report for localhost (127.0.0.1)
Host is up (0.0000030s latency).
Other addresses for localhost (not scanned): ::1
Not shown: 998 closed ports
PORT     STATE SERVICE VERSION
80/tcp   open  http    Apache httpd 2.4.34
3306/tcp open  caldav  Radicale calendar and contacts server (Python BaseHTTPServer)
Service Info: Host: 127.0.0.1
```

You can have a look at on the server that direct connection was made by nmap for detecting services
```console
127.0.0.1 - - [24/Mar/2020 19:27:57] code 400, message Bad request syntax ('\x00\x1e\x00\x06\x01\x00\x00\x01\x00\x00\x00\x00\x00\x00\x07version\x04bind\x00\x00\x10\x00\x03')
127.0.0.1 - - [24/Mar/2020 19:27:57] "versionbind" 400 -
127.0.0.1 - - [24/Mar/2020 19:28:02] code 400, message Bad HTTP/0.9 request type ('\x00')
127.0.0.1 - - [24/Mar/2020 19:28:02] "
                                      " 400 -
127.0.0.1 - - [24/Mar/2020 19:28:02] code 400, message Bad request syntax ('HELP')
127.0.0.1 - - [24/Mar/2020 19:28:02] "HELP" 400 -
127.0.0.1 - - [24/Mar/2020 19:28:02] "GET / HTTP/1.0" 200 -
127.0.0.1 - - [24/Mar/2020 19:28:02] code 404, message File not found
127.0.0.1 - - [24/Mar/2020 19:28:02] "GET /nmaplowercheck1585110482 HTTP/1.1" 404 -
127.0.0.1 - - [24/Mar/2020 19:28:02] code 501, message Unsupported method ('POST')
127.0.0.1 - - [24/Mar/2020 19:28:02] "POST /sdk HTTP/1.1" 501 -
127.0.0.1 - - [24/Mar/2020 19:28:02] "GET / HTTP/1.1" 200 -
127.0.0.1 - - [24/Mar/2020 19:28:02] code 404, message File not found
127.0.0.1 - - [24/Mar/2020 19:28:02] "GET /HNAP1 HTTP/1.1" 404 -
127.0.0.1 - - [24/Mar/2020 19:28:02] code 404, message File not found
127.0.0.1 - - [24/Mar/2020 19:28:02] "GET /evox/about HTTP/1.1" 404 -

```

## Tip
> Use `diff` Linux command to see if there is any new service or host detected in the network

> Pending
<http://www.irongeek.com/i.php?page=videos/nmap-class-hfc-louisville-issa&mode=print>
