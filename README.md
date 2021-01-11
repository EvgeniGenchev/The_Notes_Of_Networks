# The Notes Of Networks

The following chapters will include notes that I have made during reading Computer Networking: A Top-Down Approach, 6th Edition.

# Table of contents
1. [Delay, Loss and Throughput](#dlt)
2. [Network layes](#nl)
3. [Network securrity](#ns)
4. [Application layer](#a)
5. [Transport layer](#t)

## Delay, Loss and Throughput: <a name="dlt"></a>
### Sources of packet delay:
#### Processing
```
    The router computation that need to be done.
```
    
### Queuing 
```
The time the packet waits its turn to be transmitted to the mediam.
```

### Transmition 
``` 
The transmition of the packet from the queue to the mediam.

    L: lenght of the packet 
    R: transmission rate
    
    Formula: L/R

```
### Propagataion
```  
The time that the signal needs to move
accross to the mediam. Propagataion time
is close to speed of light.
      
      s: sec 
      D: distance from node A to B
      Formula: D/s 
```

### Throughput:
		The rate at which the bits are transfered between the
		sender and the reciever  

## Network layers: <a name="nl"></a>
### Easy way to remeber:
		All tree needs little pecans
		p   r    e     i      h
		p   a    t     n      y
		l   n    w     k      s
		i   s    o            i 
		c   p    r            c 
		a   r    k            a
		t   t                 l
		i
		o
		n

## E2E vs P2P:
		+---------------------------------+
		|End-to-end     |  Point-to-point |
		|---------------+-----------------|
		|Application    |  Network        |
		|Transport      |  Link 	  |
		|	        |  Physical       |
		+---------------+-----------------+


End-to-end: the protocols of the layer directly comunicate with the protocol
of the oposite side: 

		HTTP\Client -----> HTTP\Server
		TCP\Client -----> TCP\Server

Point-to-point: the layers comunicate on point to point basis and the to 
opposite layers are not directly comunicating:

    IP\Client ----->[ Network ] ----> IP\Server

## Layers overview:
### APPLICATION:
#### User Services:
- Email
- Web
- File Transfer
#### Protocols: 
- Domain Name System (DNS)
- Simple Mail Transfer Protocol (SMTP)
- File Transfer Protocol (FTP)
- Post Office Protocol (POP)
- Hyper Text Transfer Protocol (HTTP)	

### TRANSPORT:
			Purpose to hide defects or limitations of the network.
			If packets are lost, duplicated or unordered the transport
			layer has the job of maniging these defects.If a packet is 
			lost, it asks the application layer to send another one.
			If a packet is duplicated it deletes the duplicated packet.
			If the packeges are not in right order it reorders them.
			If a packet is too big the transport layer can brake them up
			and send them separately.

### NETWORK:

#### Functions:
- Adressing the hosts:
	- gives IP
- Provides routing data:
	- in order to route data over multiple hops
- Congestion Control:
	- coping wiht having more data than it can be sent 
			without any significant delays or loseses
 - Administration:
	- provide functionality to administer routes

### LINK:

#### Functions:
#### Data Link Layer:
- Framing:
	- Breaking the data into frames that will fit accross the network.
- Error Control:
	- Detect when packets are corrupted and perhaps correct them.
- Flow Control:
	- Process of keeping the receiver from being overwhelmed from
	the sender. If a there are more packeges arriving than the 
	receiver can take, this function will help slow down the speed
	at which the packets are arriving.
- Mediam Access Control Layer:
	- Sharing the Chanel:
		- That is the address that is used to resolve contention on the chanel.
							The MAC layer lets the chanel be shared fairly by the devices that 
							want to use it at the samr time

### PHYSICAL:
Transmittion of Raw bits:
- Transmittion of Raw bits from node to node

```
-------term---------
ENCAPSULATION:	
Adding additional information to the packege in order for the packege 
to be sent using another higher level protocol.

progression of the package:
message ---> packet ---> datagram ---> frame 

-----end term-------
```


## Network security: <a name="ns"></a>
### Malware:
- Trojan Horse:
	- Injection of malicious code through an operational app. The trjoan
				horse stays hidden in an app
- Virus:
	- infection through often gotten from email attachments or some skechy
				attachment. Typically envolves self-replicating and spreading over
				other machines.
- Spyware:
	- Keyloggers
	- Monitorloggers
	- User activity monitoring

- Botnet:
	- used for DDOS attacks


- Denial of service Attack (DDOS):
```
	The attack makes the services and resources that a server provides 
	unavailable for most or all of the legitimate users. A popular
	way that is done is by overwhelming the server with fake requests.

	Other one, is the Slow Loris, where the script feeds the server with
	requests slow enough that can bearly keep the connection alive. Onces
	all the connections are open by the loris script there is no way for
	legitimate users to connect.
```

- Packet sniffing: 
	- listening the network for foreign packets in order to obtain private user data

- IP Spoofing:
	- changing your IP address in order to impersonate other machines

- Record and Playback:
	- sniffing sensitive information and use it later while impersonating the target machine
			even if the information is encrypted it still can be sent to the server successfully
			
## Application Layer: <a name="a"></a>
### Intro:

#### Application Architectures:
- Client-Server:
	- Server: 
		permenant ip address, easy scaling, data farms
	- Client:
		client has to connect to the server in order to
					access the resources
	- Peer-to-peer:
		- No server
		- Direct comunication
		- Intermittent Connection
		- Highly Scalable 
		- Difficult to manage 
			- Example: 
				Torrenting  

- Hybrid of above:
	- Example:
		Skype
```
Centralized server that makes the connection
between clients than leave the clients connecting
between eachother

```


- Processes:
	- Process:
		- program running within a host
	- Client Process:
		- initiates comunication
	- Server Process: 
		- waits to be contacted

	- Sockets:
		- socket is a in point for communication

- Indentifier:
	- IP address: 
		- address of a host
	- Ports:
		- a way to uniquely indentify processes on a host

- App-layer Protocol Defines:
	- Message Type:
		- request or response 
	- Message Syntax:
		- description of the structure of the message
	- Message Semantics:
		- description of the meaning of the message blocks
	- Message Rules:
		- when and how processes repospond to messeges

- Protocols:
	- Public Domain:
		- defined openly
		- HTTP
		- FTP
		- SMTP
		- BitTorrent
		
	- Proprietary: 
		- Skype (You can't make your own app that comunicates in the skype network)
		- ppstream

- Transport Services:
	- Data Loss
	- Timing
	- Throughput
	- Security

- Internet transport protocols:
	- TCP:
		- Connection oriented: <br>
		```
			Setting up connection between client and server
		```
		- Reliable:<br>
		```
			it will resend packages if they are lost
		```
		- Flow control:<br>
		```
			making sure the receiver is not overwhelmed
			by proccesses by either slowing or speeding
			up the rate of packets transmittion
			AKA Slowing down because the receiver 
			cannot accept the packages at the rate 
			they are being send
		```
		- Conngestion Control:
		```     
			Slowing down the sender beacuse the netowork<br>
			is not able to accept all the packets because<br>
			otherwise that could lead to packet lost
		```
	- UDP:
		```
			NOT Reliable, Flow or Congestion control
			It is connectionless and there is no guarantee
			the packages will be transmitted 
		```
		- Why do we have it than:
			- it is faster than TCP
#### Web and HTTP:
<br>
https://  www.   github.com   /EvegniGenchev <br>
protocol  host   domain       path
 		 name         name
<br>
 - HTTP:
 	- uses the TCP protocol
 		works on requests -> response basis

 - Connections:
 	- Nonpersistant: 
	`object is transmitted per connection`
		- Steps:
		 	- client initiates TCP connection
		 	- server accepts connection
		 	- client sends HTTP request message
		 	- server receives the HTTP request, 
		 		sends response message
		 	- client receives the HTTP response
		 	- server closes the connection
		 - Response Time:
		  	- Round Trip Time:<br>
		 		is the time it takes for a packet<br>
		 		to travel client-->server-->client
		  	- Response Time:<br>
		 		time to get receive the first bit<br>
		 		which is equal to twice the round <br>
		 					trip time
		 	- Problems:<br>
		 		2 RTTs / Object
		 				
 	- Persistant:
		```
 		 multiple objects per connection
 		 reuses the open connection until all the requested packets are delivered
 		 sends requests imidiately
		```
 		- Steps:
		 	- client initiates TCP connection
		 	- server accepts connection
			- client sends HTTP request message
		 	- server receives the HTTP request, sends response message
		 	- client receives the HTTP response
		 	- comunication continues until the client initiates closing the connection

- HTTP Request Message:
	- Text Format:
		- ASCII (human-readable format)

		 			1 | POST /somedir/somepage.html HTTP/1.1
 					2 | Host: www.example.com
 					  | User-agent: Mozilla/5.0 
 					  | Connection: close
 					  | Accept-language: en-US
 					3 | 
 					4 | Hello there....
 					  | 

 	1. Request line <br>
 		Consists of:
 			-  Request methods:
	 				CONNECT
	 				DELETE
	 				GET
	 				HEAD
	 				OPTIONS
	 				PATCH 
	 				POST
	 				PUT
	 				TRACE
 			- Resources
 			- Protocol

 	2. Header lines <br>
 		- Host
 		- User-agent : 
 			the browser we ar going to use
 		- Connection:
 			indicates what are we going to do with the connection afterwards
 		- Could include Accept-language

 	3. Carriage Return <br>
 		 indicates the end of the header 

 	4. Entity Body <br>
 		 a message to be sent
 			not always needed

 	- Form Input <br>

					 POST:
					 push the data within the body of the message
					 GET:
					 attached to the URL of the message
 

 - HTTP Response Message:
 	- Text Format:
		- ASCII (human-readable format)

		 			1 | HTTP/1.1 200 OK
 					2 | Connection close
 					  | Date: Thu, 01 Jan 2000 12:00:00 GMT
 					  | Server: Apache/1.3.0
 					  | last modified: Thu, 07 Dec 1999 12:00:
 					  | Content-length: 2000
 					  | Content-type: text.html
 					4 | 
 					5 | KENOBI...

 	1. Status line:
 		- protocol
 		- status code and status phrase:
 			200 OK
 			301 Moved Permanently
 			400 Bad Request
 			404 Not Found
 			505 HTTP Version Not Supported

 	2. Header lines
 	3. EmptY line to indicate message end
 	4. requested data

 - EMAIL:
 	- Componets:
 		- User Agents:
 			web-application(gmail, mail, abv)
 		- Mail Server:
 			- hardware that excahges, stores and sends emails
 			- message queue for messages that need to be send
 		- Simple Mail Transfer Protocol (SMTP)

 	- SMTP:
 		- uses TCP in order to reliable send and recive email messeges
 		- it operates on port 25
 		- Command/Response:
 			Allows the direct transfer of messages
 			between sending and receiving server
 			- commands are sent in 7-bit ASCII
 			- response has Status code and Phase
 			- Phases:
 				- Handshake:
 					greeting 
 				- Transfer of messages
 				- Closure: 
 					closes down the connection  
 			- Example:
 				1. User agent 1 (This could be mail, gmail, outlook, etc)
 						sends that message to  mail server 1
 				2. Mail server 1 puts that message into a queue of messages
 				3. Mail server 1 sends that message over SMTP to Mail Server 2
 					1 handshake
 					2 transfer message/ -s
 					3 close the connection
 				4. Mail server 2 receives the message and puts it in its 
 						queue
 				5. Mail Server 2 checks if user agent 2 is active if so
 					sends the message id not it puts it in the queue again
 				6. User agent 2 receives the message
 			- Interaction:
			```
 					S: 220 gmail.com
 					C: HELO abv.bg               | the handshake
 					S: 250 *greeting message     
 					C: MAIL FROM: <palpatine@abv.bg>    | the transfer of message 
 					S: 250 <palpatine@abv.bg> Sender ok...
 					C: RCPT TO: <the_senate@gmail.com> 
 					S: 250 <the_senate@gmail.com> Recipient ok
 					C: DATA
 					S: 354 Enter mail, end with '.' on a line by itself
 					C: I love democracy
 					C: .
					S: 250 Message accepted for delivery
 					C: QUIT   | the closure
 					S: 221 gmail.com closing the connection
			```
 			- Characteristics:
 				- Persistant connection:
 						one connection to do multiple messages
 				- 7-bit ASCII
 				- CRLF.CRLF: <br>
 						end of a message <br>
 						'\n.\n'
 		- Mail Message Format:	
			- It uses the RFC 822 format
			```
 				1 | HEADER 
 				2 | BLANK LINE
 				3 | BODY
 			```	
 			1. Header:<br>
 				- contains: 
 					To
 					From
 					Subject
 					different form of SMTP commands
 			2. Blank line:<br>
 				single blank line to separate the 
 				headers and the body
 			3. Body:<br>
 				contains the 'message' in ASCII 
 				characters only
 		- Mail Access protocols:
 			- Post Office Protocol (POP3):
 				- Phase:
	 				- Authorization Phase:
	 				 	- client commands: 
	 						user: declaration of username
	 						pass: declaration of password
	 					- server responses:
						```
	 						+OK
	 						-ERR
						```
	 				- Transaction Phase: <br>
					```
	 						list: list of message numbers/ids <br>
	 						retr: retrieve message by number <br>
	 						dele: delete message <br>
	 						quit: quit the service <br>
					```
	 				- Example: <br>
					```
						S: +OK POP3 Server ready | authorization phase
						C: user Mando
						S: +OK
						C: pass lovesGrogu123
						S: +OK 
						C: list  | transation phase
						S: 1 243
						S: 2 594
						S: .	 | '.' in order to indicate the end
						C: retr 1
						S: <some data>
						S: .
						C: dele 1 | dele doesn't have response
						C: quit
						S: +OK
					```
			- Internet Mail Access Protocol (IMAP):<br>
						really complicated, involves folders
				- Example:
				```
							C: <open connection>
							S:   * OK IMAP4rev1 Service Ready
							C:   a001 login mrc secret
							S:   a001 OK LOGIN completed
							C:   a002 select inbox
							S:   * 18 EXISTS
							S:   * FLAGS (\Answered \Flagged \Deleted \Seen \Draft)
							S:   * 2 RECENT
							S:   * OK [UNSEEN 17] Message 17 is the first unseen message
							S:   * OK [UIDVALIDITY 3857529045] UIDs valid
							S:   a002 OK [READ-WRITE] SELECT completed
							C:   a003 fetch 12 full
							S:   * 12 FETCH (FLAGS (\Seen) INTERNALDATE "17-Jul-1996 02:44:25 -0700"
							      RFC822.SIZE 4286 ENVELOPE ("Wed, 17 Jul 1996 02:23:25 -0700 (PDT)"
							      "IMAP4rev1 WG mtg summary and minutes"
							      (("Terry Gray" NIL "gray" "cac.washington.edu"))
							      (("Terry Gray" NIL "gray" "cac.washington.edu"))
							      (("Terry Gray" NIL "gray" "cac.washington.edu"))
							      ((NIL NIL "imap" "cac.washington.edu"))
							      ((NIL NIL "minutes" "CNRI.Reston.VA.US")
							      ("John Klensin" NIL "KLENSIN" "MIT.EDU")) NIL NIL
							      "<B27397-0100000@cac.washington.edu>")
							      BODY ("TEXT" "PLAIN" ("CHARSET" "US-ASCII") NIL NIL "7BIT" 3028
							      92))
							S:   a003 OK FETCH completed
							C:   a004 fetch 12 body[header]
							S:   * 12 FETCH (BODY[HEADER] {342}
							S:   Date: Wed, 17 Jul 1996 02:23:25 -0700 (PDT)
							S:   From: Terry Gray <gray@cac.washington.edu>
							S:   Subject: IMAP4rev1 WG mtg summary and minutes
							S:   To: imap@cac.washington.edu
							S:   cc: minutes@CNRI.Reston.VA.US, John Klensin <KLENSIN@MIT.EDU>
							S:   Message-Id: <B27397-0100000@cac.washington.edu>
							S:   MIME-Version: 1.0
							S:   Content-Type: TEXT/PLAIN; CHARSET=US-ASCII
							S:
							S:   )
							S:   a004 OK FETCH completed
							C    a005 store 12 +flags \deleted
							S:   * 12 FETCH (FLAGS (\Seen \Deleted))
							S:   a005 OK +FLAGS completed
							C:   a006 logout
							S:   * BYE IMAP4rev1 server terminating connection
							S:   a006 OK LOGOUT completed
					```
 			- POP vs IMPA:
 				- POP:
 					- stateless
 					- dowload and delete 
 					- dowload and keep
 				- IMPA:
 					- server 
 					- folders
 					- stateful
 		- SMTP vs. HTTP:
 			- Both work on command/response basis
 			-  Both use ASCII <br>
 				SMTP uses 7-bit ASCII <br>
 				HTTP uses 8-bit ASCII <br>
 			- Interactions: <br>
 				SMTP pushes message from client to server <br>
 				HTTP pulls from the server (html, css, javascript) <br>
 			- Messages: <br>
 				HTTP supports single-part message <br>
 				SMPT supports multiple-part message <br>

#### Domain Name System (DNS):
 - Purpose: <br>
 	Map domain names with IP addresses 
	- Example: <br>
 		<www.google.com : 172.217.3.206 > <br>
 		<www.github.com : 140.82.113.3 > <br>

 - Indenfiers:
 	- IP Address: <br>
 		*address that is used by routers <br>
 		(0-255).(0-255).(0-255).(0-255) <br>
 	- Domain Name: <br>
 		*human readable name 
 		- starwars.com
 		- google.com
 		- github.com
 		- etc.
- Characteristics:
	- Distributed: <br>
 		It exist in pieces everywhere
 	- Hierarchical: <br>
 		It structure so its components are hierarchically defined
 	- Database: <br>
 		A lot of structured information

- Centralized vs. Distributed:
 	- Centralized:
	 	- single point of failure
	 	- traffic volume
	 	- dinstance 
	 	- maintaince 

	 - Distributed:
	 	- if one DNS fail other can substitute
	 	- you can shut down a sigle DNS to maintain
	 				and the service won't fail

- Features:
	- Hostname to IP address Translation
	 - Host Aliasing: <br>
	 			two names that point to one address
	 	- Example:<br>
	 			google.com and www.google.com point to
	 				the same IP
	 	- Mail Server Aliasing: <br>
	 			allow systems to look up IP address and name
	 			of the mail server for domain
	 	- Load Distribution:<br>
	 			couple ip addresses for one domain name in order<br>
	 			to distribute the clients of that are connected<br>
	 			for better performance and efficiency. Anoter plus<br>
	 			is defence against DDOS attacks.<br>

- TLD and Authorutative Servers:
	 - Top-level domain (TLD) Servers:
	 	- com, org, net, edu
	 	- All top-level coutry domain uk,fr, ca, jp

	 - Authorutative Servers:
	 	- Organisation's DNS servers
	 	- Maintained by Organisation or Service Provides

- Hierarchy:

	 Root Servers --> Top-level domain servers --> Authoritative Servers
	- Types of queries:
		- Iterated Query:
			```
			localhost -'starwars.com ?'-> localDNS
			localDNS -'starwars.com ?'-> rootDNS
			localDNS <-'don't know but check .com server'- rootDNS
			localDNS -'starwars.com ?'-> .com server
			localDNS <-'don't know but check disney.com server'- .com server
			localDNS -'starwars.com ?'-> disney.com server
			localDNS <-'23.53.34.49'- disney.com server
			localDNS -'23.53.34.49'-> localhost
			```
	 	- Recursive Query:
			```
			localhost -'starwars.com ?'-> localDNS			
			localDNS -'starwars.com ?'-> rootDNS
			rootDNS -'starwars.com ?'-> .com server
			.com -'starwars.com ?'-> disney.com server
			.com <-'starwars.com ?'- disney.com server
			rootDNS <-'starwars.com ?' - .com
			localDNS <-'starwars.com ?'- rootDNS
			localhost <-'starwars.com ?'- localDNS
			```<br>
	 - DNS caching and updating:<br>
		 Everything is cached usually
	 - DNS records:<br>
	 	- Distributed DB storing Resource Records
	 				- (Name, Value, Type, TTL )
	 					- TTL:
	 						time to die is between 1 - 2^31 sec ~= 68 years 
	 	- Records Types:
	 		- Type  A:<br>
	 			- mapping name to ip addresses
	 				1.Name:
	 					host name
	 				2.Value: 
	 					Ip address
	 				3. Type : A
	 			- Example: <br>
	 				(www.google.com, 216.58.193.78, A, [time in seconds] )
	 		- Type NS (Name server):
	 				1. Name:
	 						domain
	 				2. Value:
	 						Hostname: of Authorutative Name server
	 				3. Type: NS
	 			- Example: <br>
	 						(www.google.com, NS3.ZONEEDIT.COM, NS, [time in sec])
	 		- Type CNAME:<br>
	 			- aliasing
	 				1. Name:
	 						Alias for some 'canonical' (real) name
	 				2. Value: 
	 						Canonical name
	 				3. Type: CNAME
	 			- Example: <br>
	 						(www.ibm.com, servereast.backup2.ibm.com, CNAME, [time in sec])
	 		- Type MX (mail server):
	 				1. Name:
	 						hostname
	 				2. Value: 
	 						Name of Mail Server
	 				3. Type: MX
	 			- Example: <br>
	 						(www.google.com, www.gmail.com, MX, [time in sec])
	 - DNS Protocol Messages:
	 	- Messages:<br>
	 		- Query and Reply
	 		- Same Format
	 	- Header: 
	 	 	- ID:
	 		- Flag:
	 	- Structure:
		```
	 			+-------------------------+--------------------------+  <-+
	 			|     indentification     |          flag            |	  |
	 			+-------------------------+--------------------------+    | 
	 			|   number of questions   | number of answer RRs     |    | 12 bytes
	 			+-------------------------+--------------------------+    |
	 			| number of authority RRs | number of additional RRs |    |
	 			+-------------------------+--------------------------+  <-+
	 			|      questions (variable number of questions)      |
	 			+----------------------------------------------------+
	 			|      answers (variable number of resource records) |
	 			+----------------------------------------------------+
	 			|    authority (variable number of resource records) |
	 			+----------------------------------------------------+
	 			| 	        additional information               |
	 			|          (variable number of resource records)     |
	 			+----------------------------------------------------+
		```
		<br>
	 - Inserting Records;
	 	- Register Name networkutopia.com at DNS Register:<br>
	 				provide names, IP addresses of authoriative name server
	 	- when registrating 2 RRs (resource records) are added into com TLD server:<br>
			```
	 			(networkutopia.com, dns1.networkutopia.com, NS)<br>
	 			(dns1.networkutopia.com, 212.212.212.1, A) <br>
			```
- Pure P2P Architecture:
	- No Always-On Server
	- Arbitrary End Systems:
		- Directly Communicate
	- Intermittently Connections
		- Changing Ip addresses
	- File Distributiobution: 
		- C-S vs P2P: <br>
				Us: server upload speed<br>
				Ui: peer upload speed <br>
				Di: peer download speed<br>
				N - number of sytems for the info to be delivered to<br>
				F - how many bits the message is<br>
			- C-S (Client-Server):	
					- Server: <br>
						NF/Us bits/sec<br>
					- Client:<br>
						F/Di bits/sec<br>
					Dcs = max { NF/Us, F/min(Di)}<br>
					whichever has bigger value will be the bottleneck<br>
			- P2P (Peer-to-peer):<br>
			In this case the server has to upload the data only ones beacuse users can both upload and download
				- Server:<br>
					F/Us
				- Client:<br>
					F/Di<br>
				Dp2p = max {F/Us, F/min(Di), NF/(Us + sum{Ui})} <br>
				the more clients the faster it gets to users<br>
			- Conclusion:<br>
			```
					With respect to the increasing clients in the c-s file<br>
					distribution the dowload speed increases linearly. <br>
					However, this is not the case in the P2P where the more<br>
					users there are in the system the better the dowload speed up<br>
					to one point. <br>
			```
			
## Transport layer <a name="t"></a>

### Transport Service and Protocols:

#### Purpose:

		Providing of logical comunication between processes mostly
		running on different hosts. It consists of end to end systems
		that talk to eachother. 
		
- Network Vs Transport<br>
		The Network is responsible is logical communication between host<br>
		The Transport is responsible is logical communication between processes<br>
	- Internet Transport Layer Protocols
		- TCP:
			- Reliable
			- Flow control
			- Congestion control
			- in order
		- UDP:
			- unrealibale
			- unordered
			- "best effort"
			
#### User Datagram Protocol(UDP):
- Low effort:
```
	this processes is the low effort transport protocol
	it does not care if a packet is lost or out of order.
```
- Connectionless:
	- no handshake is needed before sending the data

- Why is there UDP :
	- No connection establishment:
				- no delay
	- No connection state:
				- Simpler to send
	- Small Segment Header:
				- less wasted bandwidth
	- No congestion control:
				- no speed limit

- Usage:
	- Streaming Multimedia:
		- Loss Tolerant
		- Rate sensitive
	- DNS:
		-should be quick
	- SNMP

- Format:
```

			+------------32 bit---------+
			|source port    | dest port |
			+---------------+-----------+
			|length (bytes) | checksum  |
			+---------------+-----------+
			|           message         |
			+---------------------------+
			
```

- UDP Checksum:
```

			Sender --->   1.sequence of 16-bit ints
				      2.binary sum of the 16-bit
				      3. one's complement of the sum = checksum
			Receiver ---> 1. computes again
				      2. check if it is the same
				      3. if so "No error detected"
				      4. in not "Error Detected"
```

- Checksum wraparound:<br>
carry that goes out of the 16 bits returns from the beginning
	- Example: 
```
		a = 10101010
		a << 1
		a = 01010101
```

- Why do Checksum at Transport layer?
	- no guarantees that the link layer is reliable
	- End-to-end principle:
	```
		Comunications protocol operations should
		be defined to occur at the end-points of
		a comunication system.
		Functions placed at the lower levels may be
		redundant or of little value when compared to
		providing them at the higher levels.
		No layer can check the layer above so having the
		checksum is guarantee that the network layer had no
		corruptions.
	```
#### Principles of Reliable Data Transfer:
- Reliable Data Transfer:
	- Incremental Development:
	```
		incremental development is when you gradually increase the
		possible errors in a system, program , etc in order to cope
		with possible flaws one by one. In this example rdt is the
		reliable data transfer program that we gradually introduce
		problems to
	```
	- rdt1.0:
		- No Bit Errors
		- No Packet Loss

	- rdt2.0:
		- No Packet Loss 
		- Bit Errors
		- How to detect them bit errors:
			- Checksum 
			- Than what?
		- How to recover from errors:
			- Receiver Feedback:
				- Acknowledgements: ACKs
				- Negative Acknowledgements: NAKs
			- Retransmission:
				```
					Stop and wait protocol. The sender
					waits for a feedback based on the 
					checksum algo. If it gets ACK it continues
					else it resends
				```
		- What if ACK/NACK are corrupted?
			- Use sequence numbers for packets

	- rdt2.1: <br>
		Resend current packet when corrupted ACK/NAK is recieved.
		- Problem: <br>
				If the ACK/NAK are corrupted duplicate data could
						be sent
		- Solution:<br>
				Sequence numbers (0-1)
		- Why only two sequence numbers ?
			```
				1 packet is being sent at a time.
				if the sender sends two 1s the reciever will
				know there is a packet missing and vice versa
			```

	- rdt2.2: <br> 
		Does not use NAK
		- How ?
			```
				In the ACK there is a sequence number if
				the receiver returns ACK with a sequence number 1
				when the sender sended ACK with a sequence number of 0
				the sender would know that a packet was corupted
			```

	- rdt3.0:
		- Bit Errors
		- Packet Loss
		- Error Detection:<br>
						Checksum, ACKs Seq#, Retransmission
		- Loss Detection:<br>
			- Timeout
				-  Real life example:
					```
								If your mother texts you and you don't answer
								(don't acknowledge) your mother will w8 reasonable
								amount of time and then will text you again.
					```
				- Contdown timer: <br>
							if we don't get acknowledgement we send it again
				- What if the packet is just delayed?<br>
					- A duplicate will arrive. Solution?<br>
						The solution is already introduced with the sequence numbers.
			- EXAMPLE:
			```
						sender --pkt 0--> receiver
						sender <-ACK 0--- receiver
						sender --pkt 1--> receiver
						sender <-ACK 1--- receiver
						sender --pkt 0--> packet is lost
						sender: *waits until the countdown timer runs off
						timer: *runs off
						sender --pkt 0--> receiver
						sender <-ACK 0--- receiver
			```
			- Stop and wait operation:<br>
				t : time<br>
				L : packet length<br>
				R : speed<br>
				```
				sender --pkt 0-->receiver // first packet bit is transmitted at t = 0
							 	last packet bit is transmitted at t = L/R
				sender <--ACK 0---receiver // first packet bit arrives,
								last packet bit is arrives,
									Send ACK
				The problem is that in the time the countdown is going many packets
				could be sent
				``` 
				- Utilization: 
					- Fraction of Time Sender is sending: 
					```
						If the countdown is 0.01 and and it takes 0.00001sec to
						send a packet a packet. This is 0,1 % utilization of the 
						bandwidth. Anything else is just lost.
					```
				- How to improve the utilization?
					- Pipeline protocol:
					 	- sending multiple packets
							- Increase amount of Seq#
							- Buffering 
						- Types: 
							- Go-N-Back:<br>
							send all the packets from N on again
								1 Sender:
									- send up to N unACked pkts in pipeline
								2 Receiver:
									- only sends cumulative ACKs
									- does not send ACK if there is gap
								3 Sender:
									- timer for oldest unACKed pkt
									- if timer expires, retransmit all unAcked pkt
							```
							- Selective Repeat:<br>
								send only packet N, all the other are buffered
							1 Sender: 
								- up to N unACKed packets in pipeline
							2 Receiver: 
								- ACKs individual pkts
							3 Sender: 
								- Timer for each unACKed pkt
								- If timer expires, retransmit only unACKed pk



