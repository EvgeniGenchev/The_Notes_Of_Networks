# The Notes Of Networks

The following chapters will include notes that I have made during reading Computer Networking: A Top-Down Approach, 6th Edition.

# Table of contents
1. [Delay, Loss and Throughput](#dlt)
2. [Network layes](#nl)
3. [Network securrity](#ns)
4. [Application layer](#a)
5. [Transport layer](#t)
6. [Network layer](#net)
6. [Link layer](#li)

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
https://www.github.com/EvegniGenchev <br>
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
### Demultiplexing:
- Ip Datagrams:
	- Source IP Address
	- Destination IP Address
	- Segment:
		- Source Port
		- Destination Port

- in UDP:
	- Indenfiers:
		- Destination port
		- Destination IP address

	- Port numbers:
		- Well-Known Port Numbers:<br>
			`0-1023`	
		- Other Port Numbers:<br>
			`1024-65535`
- in TCP:
	- Indenfiers:
		- Source port
		- Source IP address
		- Destination port
		- Destination IP address	
			
### User Datagram Protocol(UDP):
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
### Principles of Reliable Data Transfer:
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
							- Go-N-Back:<br> <a name="go-n-back"></a>
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
								
### Transmission Control Protocol:
- Unicast:
	- one sender --> one receiver
- Reliable, In-Order Byte Stream
- Connection oriented
- Pipeline
- Full Duplex
	- bidirectional dataflow 
- Flow Control:
```
	sender will limit its sending speed in regards to the receiver
	receiving speed in order for the receiver not to be overwhelmed
```
- Congestion control:
```
	sender will limit its sending speed in respect to the bandwidth 
	of the network
```
#### TCP Seq # and ACKs:
- Example:
```
	HOST A ------Seq=42, ACK=79, data = 'C'--> HOST B
	HOST A <-----Seq=79, ACK=43, data = 'C'--> HOST B
```

When HOST A sends data to HOST B it sends the n-th byte sequence <br>
and an acknowledgement. Then HOST B echoes the data back with swapped<br>
sequence and acknowledgement and increments this way HOST B comfirms <br>
the received data.<br>

#### Round trip time and timeout:
- How to set ?
	- RTT estimation:
		- Sample RTT: 
			- messured time for segment transition to receive an ACK
		- Average RTT:<br>
		a: is a value between 0 and 1 and it used as a `weight` for <br>
		the two values. The bigger the a the smaller `weight` the previous <br>
		reading will have. <br>
		```
		estimatedRTT = (1 - a) * estimatedRTT + a * sampleRTT
			       [previous estimatedRTT]  [current sampleRTT]
		```
	- Timeout:
		`Timeout = estimatedRTT + safetyMargin`
		- Safety margin:
			```
			Safety margin is needed in order to prevent premature timeout and it
			equal an estimated deviation (devRTT) of a sampleRTT
			```
			b: is a value between 0 and 1 (look the explanation of a in "Average RTT")
			```
			devRTT = (1 - b) * devRTT + b * | sampleRTT - estimatedRTT|
				[previous devRTT]      [the current error margin]
			```
			This formula implies that the error margin and the deviation (safetyMargin)<br>
			are parallel to each other. This means the smaller the error margin the smaller <br>
			the safetyMargin. <br>
			
			`timeoutInterval = estimatedRTT + 4 * devRTT`
	- Reliable data transfer:
		- runs on top of an unrealibale service IP:
			- this implies possibility of packet loss, delay, throughput
		- In order for TCP to reliable send data through IP it uses:
			- Pipeline Segments:
				- multiple segments can be out at once
			-  Culminative ACks
				- (look at [Go-N-Back](#go-n-back))
			- Single Transmission Timer:
				- the timer equals the oldest standing unACKed package
			- Retransmission Triggered by:
				- Timeouts
				- Duplicate ACKs
		- Sender Events:
			- Data is received from App
				1. Create a segment with Seq # <br>
					`Seq # = numbering the bytes`
				2. Start a timer for the oldest stading unACKed segment <br>
					`the timer will be calculated with the formulas stated above`
			- Timeout 
				1. Retransmission of the segment that caused the timeout	
				2. restart the timer 
			- ACK is received
				1. Checks if the ACK is for a previously unACKed segment:
						`if so it updates the memory in order to have the transmission counted as success`
			- Simplified example of Sender psuedo-code:
					*This psuedo-code is not completed and more will be added
			```
					NextSeqNIM = InitialSeqNum
					SendBase = InitialSeqNum 
					loop(forever){
						switch(event){
							event : data received from the application above
								create TCP segment wiht sequence num NextSeqNum
								if(timer currently not running)
									start timer
								pass segment to IP
								NextSeqNum = NextSeqNum + length(data)
							event : timer timeout
								retransmit unACKed segment with smallest sequence num
								start timer
							event : ACK received, with ACK field value of y
								if (y  > SendBase)
									SendBase = y
									if (there are currently unACked segments)
										start timer
						}
					}
			```
			- Example of lost ACK:
			```
					X : lost
					HOST A --------Seq=92, 8 bytes data -------> HOST B [send base is 92]
					HOST A     X<------ACK=100------------------ HOST B
					*Timout runs out
					HOST A --------Seq=92, 8 bytes data -------> HOST B
					HOST A <-----------ACK=100------------------ HOST B [send base is 100 (Seq# + length of bytes)]
			```
			- Example of premature timeout:
			```
					HOST A --------Seq=92, 8 bytes data -------> HOST B [send base is 92]
					HOST A --------Seq=100, 20 bytes data -----> HOST B [send base is still 92]
					*Timer for the oldest segment (Seq=92) runs out
					HOST A --------Seq=92, 8 bytes data -------> HOST B [send base is still 92]
					HOST A <-----------ACK=100------------------ HOST B [send base is 100]
					HOST A <-----------ACK=120------------------ HOST B [send base is 120]
					HOST A <-----------ACK=120------------------ HOST B [send base is 120]
						"this states tha all the packets up until 120 are received"
			```
			- Example of cumulative ACK:
			```
					HOST A --------Seq=92, 8 bytes data -------> HOST B [send base is 92]
					HOST A     X<------ACK=100------------------ HOST B
					HOST A --------Seq=100, 20 bytes data -----> HOST B [send base is still 92]
					HOST A <-----------ACK=120------------------ HOST B [send base is 120]
			```
		- ACK Generation:
			- Receiver Events and actions:
				*events and actions numeration does not imply order rahter than separation
			```
					Event 1:
						-> Arrival of in-order segmnet with expected seq
						-> All data up to expected seq is ACKEd
					Action 1:
						-> Delay ACK
						-> Wait up to 500ms for next segment
						-> If timeout, send ACK
					Event 2:
						-> Arrival of in-order segment with expected seq
						-> One other segment has ACK pending
					Action 2:
						-> immediately send single cumulative ACK, ACKing both in-order segment
					Event 3:
						-> Arrival of out-of-order segment 
							higher-than-expected seq
						-> Gap detected
					Action 3:
						-> Immediately send duplicate ACK of next expected byte
					Event 4: 
						-> Arrival of segment that partially or completely fills gaps
					Action 4:
						-> Immediately send ACK, provided that segment starts at lower end
							gap
			```
		- Fast Retransmission algorithm:
			- Problem:
			```
				The Timout Interval is too long. During this interval the receiver
				send ACK for the last received packet multiple times but the sender
				will have to wait for the timeout before sending the lost packet again
			```
			- Soluton:<br>
				`Detect lost segments via duplicate ACKs `
			- Algorithm:<br>
			`If 3 duplicate ACKs are being received, resend the segment before timer expires.`
				- Psedo-code:
			```
						event : ACK receivedm with ACK field value of y
							if (y > SendBase){
								SendBase = y 
								if (there are currently unACKed segments){
									start timer
								}
							}else{
								increment count of duplicate ACKs received for y
								if (count of duplicate ACKs is greater than 3){
									resend segment wiht sequence num = y
								}
							}
			```
		- Flow control:
			1. Preventing a fast sender to overwhelm slow receiver
			2. Matching the speed of the sending and receiving
			- Unused Buffer Space:
				```
					rwnd : receive window or unused buffer space
					RcvBuffer : buffer space
					rwnd = RcvBuffer - [LastByteRcvd - LastByteRead]
				```
					- Receiver:
						- every ACK will contain the rwmd
					- Sender:
						- limits the number of unACKed bytes to the receive window
		- Connection Management:
			- Connection oriented:
				```
					This implies the need for a connection to be established in order
					for a transmittion to be possible.
				```
			- TCP variables:
				* these variables have to be set beforehand 
				- Seq #'s
				- Buffers
				- Flow Control
		- 3-way-handshake:
			```
				1.Client ------SYN-----> Server [contains no data]
				2.Client <---SYN-ACK---- Server [contains no data]
				3.Client ------ACK-----> Server [may contain data]
			```
			1. Clent sends a TCP SYN to the server that specifies the inital Seq
			2. Server receives the SYN, allocates buffer, specifies its own inital seq and replies with SYN ACK
			3. Clent receives SYNACK, replies wiht ACK
		- SYN Flood Attack
			- Deluge of SYNs:
				- send a lot of SYNs
			- Deplete Server Resources:
				- server allocates resources for these half open connections
			- SYN Cookies
				- used to overcome the Flood attack
		- Closing the connection:
			```
				1.Client ------FIN-----> Server
				2.Client <-----ACK------ Server
				3.Client <-----FIN------ Server
				4.Client -----ACK------> Server
			```
			1. FIN Sent
			2. ACK Sent
				- receive FIN
				- Close connection
				- Send FIN
			3. ACK Received
				- Receive DIN
				- Replies wiht ACK
			4. ACK received
				-Connection closed
		- Segment Structure of TCP:
			- U, A, P, R, S, F : control flags that indicate if on of the following is true:
			- URG: Urgent pointer is valid
			- ACK: Acknowledgement number is valid( used in case of cumulative acknowledgement)
			- PSH: Request for push
			- RST: Reset the connection
			- SYN: Synchronize sequence numbers
			- FIN: Terminate the connection
			```
				+------------------------+------------------------+
				| source port #          |  dest port #           | 
				+------------------------+------------------------+ <---+----------------
				|         sequence number (Seq #)                 | 	| counting by 
				+-------------------------------------------------+	| bytes of data
				|         acknowledgement number (ACK)            |	| (not segments!)
				+------------------------+------------------------+ <---+----------------
				| head | not |U|A|P|R|S|F| receive window (rwnd)  | 	| # bytes rcvr willing
				| len  | used| | | | | | |                        |	| to accept
				+------------------------+------------------------+ <---+----------------
				| 	    checksum     | Urg data pointer       |
				+------------------------+------------------------+
				|            Options (variable length)            |
				+-------------------------------------------------+
				|             application data (variable length)  |
				+-------------------------------------------------+ 
			```
#### Principles of Congestion control:
- What is congestion?
	- too much demand for the available supply of a resource
	- if there are too many senders trying to send a packet through the network
	- Problems: 
		- delay
		- loss
	- Costs of congestion:
		1. the sender must send retranstmissions in order to compansater for packets being dropped due to buffer overflow.
		2. uneeded retranstmissions by the sender in the face of large delays may cause a router to waste its link bandwidth forwarding uneeded copies of a packet.
		3.  when a packet is dropped along a path, the transmission capacity that was 
					used at each of the stream links to forward that packet to the point it was
					dropped have been wasted.

	- Approaches to Congestion Control
		- End-to-end:
			- No explicit feedback
			- Congestion Inferred:
				- From End-System
				- Observed Loss
				- Delay
			- TCP
		- Network Assisted:
			- Network feedback:
				- from router
				- single bit
				- explicit Rate
			- ATM
#### Congestion Control:
- Implicit End-to-end Feedback:
	- When an ACK is received try to speed up the rate at which packets are being sent
	- When an ACK is missing try to slow down the rate at which packets are being sent

- How to slow down the rate?
```
	cwnd : congestion window 
	Sender limited by min(cwnd, rwnd)
	Sending rate = cwdn / RTT
```
- How to find rate just below congestion level?
	- Bandwidth probing:
		- increase the speed until there is a packet loss than drop
- Success event:
	- increase cwnd in one of the following modes:
	1. Slowstart:
		- Increase speed exponentially (double the MSS per RTT)
		- Connection start or after timeout
		1. ssthresh is the slow start threshold 
			- cwnd threshold maintained by TCP
		2. on timeout ssthresh is set to half of cwnd
		3. when cwnd >= ssthresh the mode is being switched to congestion avoidance

	2. Congestion avoidance:
		- increase speed linearly (by 1 MSS per RTT)
		- normal opeartion
		- this mode is on when cwnd > ssthresh
		1. Implementation:
			- cwnd += MSS/cwnd for each ACK received
- Loss event:
	- decrease cwnd
	- Timeouts:
		- Cut cwnd to 1
	- 3 Duplicate ACKs
		- Cut cwnd in half
## Network layer:<a name="net"></a><br>
`provides connection between two hosts.`
### Introduction:
#### 2 Key Network-Layer Functions:
- Forwarding:
	local process 
- Routing:
	global process
- Example :<br>
	`When the GPS finds the shortest way is rounting, whereas forwarding is the annoying voice that tells you where to go on every turn`
#### Network Service Model:
- Per datagram:
	- guarantee delivery
	- guarantee delivery wiht bounded delay
- Per Flow:
	- in-order delivery
	- guarantee minimum bandwidth
	- maximum jitter:
		- variation in package spacing

### Virtual circuit and datagram networks:
#### Connection vs connection-less:
- Datagram:
	- Connection-less
	- best effort
	- No setup call
	- No state info 
	- Packets forwardrd using destination address


- Virtual Circuit:
	- Connection-ful
	- Call Setup/teardown:
		- Signaling Protocols
	- VC Identifier:
		- no destination host address
	- Router state:
	- Resource Reservation:
		- dedicated resource
	- VC Implementation:
 		- Components:
 			- Path
 			- VC Numbers
 			- Entries in Forwarding tables
 	- Forwarding:
 		- 32-bit Address:<br>
 			`~4 billion possiblities`
 		- Exaustive Forwarding Table
 		- Forwarding table:
 			- Prefix matching:
 				`encapsulation of ranges of addresses by having the longest prefix that two numbers have in common`
				- Example:
					```
					1 | 232.123.156.XXX
					2 | 232.123.157.xxx
				        ```
					- If the ip is 232.123.156.2 it will choose the first ouptup port
					- If the ip is 232.123.157.2 it will choose the second one 

#### Datagram vs VC Network:
- Datagram(IP):
 	- Purpose:
 		- use in computers
 	- Smart end systems:
 		- capable of a lot of calculations
 	- Simple network core:
 		- everything is taken care of in the transport layer
 	- Many link types

 - Virtual Circuit(ATM):
 	- Purpose:
 		- use in telephones 
 	- Dumb end systems:
 		- simple capability
 	- Complex core:
 		- everything has to be taken care of in the network core
 	- Few link types
 #### Internals of a router:
 - Architecture Overview:
 	- Functions:
 		- Rounting
 		- Forwarding
 	- Components:
 		- Input ports:
 			1. Except bits from the physical layer
 			2. Pass them to the Link Layer (Ethernet)
 			3. Pass to the Network Layer (IP)
 		- Swithcing Fabric:
 			- Types:
 				- Memory:<br>
 					`save the inputs to the memory and then copy them to the output`
 					- Old-School
 					- Slow
 					- Limited in speed by the bandwidth of the memory
 				- Bus:<br>
 					`transfer the datagram directly over shared bus`
 					- Limited in speed by the bus bandwidth
 				- Crossbar:
					- Complicatd
 					- Costly
 					- Fast
 		- Output Ports:
 			- Oposite of the input ports
 			- Output port queing when arrival rate via the switch exceed the output line speed
 			- How much buffering ?
 				C: link capacity
 				RTT: round trip time
 				N: number of flows
 				B: Buffering
				```
 					 RTT * C
 				    B = ---------
 					 sqrt(N)
				```
 		- Routing processor:<br>
 			`implements the routing table`

### Internet Protocol(IP):
#### Introduction:
- IP:
 	- addressing conventions
 	- datagram format
 	- packet handling conventions
- Routing protocols:
	- path selection
 	- RIP, OSPF, BGP
- ICMP:
 	- error reporting
 	- touter "signaling"

#### Datagram Protocol:
	 ```
 		<----------------- 32 bits ----------------->

 		+---+------+-----------+--------------------+
 		|ver|header|  type of  |      length        |
 		|   |length| service   |                    |
 		+---+------+-----------+-------+------------+
 		| 16-bit identifier    | flags | fragment   |
 		|                      |       | offset     |
 		+-----+----------------+-------+------------+
 		| TTL |  upper layer   | header checksum    |
 		+-----+----------------+--------------------+
 		|        32-bit source ip address           |
 		+-------------------------------------------+
 		|      32-bit destination ip address        |
 		+-------------------------------------------+
 		|               OPTIONS(if any)             |
 		+-------------------------------------------+
 		|         Data - variable name typically    |
 		|          TCP or UDP segment               |
 		+-------------------------------------------+
	```
- IP fragmentation & reassembly
	- Maximum transfer unit (MTU):<br>
	 	`the maximum size of link level frame (1500 bytes)`
	- Fragmentation:<br>
	 	`break down datframes that are bigger than MTU`
	- Reassembly:<br>
	 	`eassemble the broken down datframes`
	 - Exmaple"
	 	```
	 		4000 bytes of datagram:
			+------------+--------+--------------+------------+
	 		| len = 4000 | ID = x | fragflag = 0 | offset = 0 |
			+------------+--------+--------------+------------+
	 		*Fragmentation
	 		len = 1480 (bytes in data field) + header
	 		! offset is in 8 bytes units
			+------------+--------+--------------+--------------+
	 		| len = 1500 | ID = x | fragflag = 1 | offset = 0   |
			+------------+--------+--------------+--------------+
	 		1480 / 8 = 185 offset
			+------------+--------+--------------+--------------+
	 		| len = 1500 | ID = x | fragflag = 1 | offset = 185 |
			+------------+--------+--------------+--------------+
	 		offset = 2 * 185
	 		len = 4000 - 2 * 1480  
			+------------+--------+--------------+--------------+
	 		| len = 1040 | ID = x | fragflag = 0 | offset = 370 |
			+------------+--------+--------------+--------------+
		```
#### IPv4 addressing:
- Interface:<br>
	The connection between a router and physical link.<br>
	Routers have many interfaces ---> many ip addresses
- IP Addresses:<br>
	32 bit binary   
	```
			> 1101111 0000001 0000001 0000001 		
			decimal
			> 14,614,785
			dotted decimal:
			> 223.1.1.1
			slashed:
			> 223.1.1/ 24 
					in this case 24 give information about the portioning 
					of the IP adress (host vs network)
					The first 24 bits are part of the network address.
					The last * are part in the host.
		```
- Subnet Mask:
	- Address:
		223.1.1.1
	- Subnet Mask:
		255.255.255.0 
		*the same in meaning as 223.1.1/24
	- Subnet:
		223.1.1.x
	- Classless Inter Domain Routing (CIDR):
		- subnet portion of address of arbitrary length
		- x in can be different from 8 bit value 
		- Example:
					```
						200.23.16.0/23 
													 ,
						110010000.  00010111. 00010000. 00000000
						<-------------23 bits-------><--9 bits->
					```
		- Why?
			- Efficient utilization of the allocated addresses
	- How does a host get an IP address?
		- Manually 
			- Hard-Coded
				- DO NOT DO IT
		- Automatically
			- DHCP			
	- Dyanmic Host Configuration Protocol (DHCP):
		- Goal
			- Dynamically Obtain IP Address 
		- Overview
			- Discover Message:
				- alterting the need of IP addresses
			- Offer Message
				- offering available IP addresses
			- Request Message
				- request the offered IP addresses
			- ACK Message
				- ACK of the connection betweeen the 
						host and the network
		- Functionality beyond IP:
			- Default Gateway
			- DNS Server 
			- Subnet Mask
	- ICANN:
		- Internet Corporation for Assigned Names and Bumbers
	- Running out of IP addresses?
		- Network Address Translation (NAT)
			1. The router has only one IP address
			2. All the host that are connected to the same router
					have local private addresses
			`10.0.0/24`
			*this way all the hosts share one public IP address
			- How to destinguish packages ?
				- ports 
			- Motivation:
				- Usage of single IP address per LAN
				- Advantages:
					- Cost
					- Flexibility
					- Convenience 
					- Security
				- Not perfect ?
					- Crosses layers
						- router should process up until the network layer
						*ports should be processed in the transport layer
					- Violates End-to-End Principle
					- Short-Sigthed Solution
#### Internet control message protocol (ICMP):
- Network-level signaling
- Slightly Above IP
 - ICMP message
 	- Type 
 	- Code
 	- 8 bytes of the datagram
 - Traceroute and ICMP
 	- Source sends series of UDP segments to dest
 		- When n-th datagram arrives to n-th router 
 		- ICMP message TTL Expired packet (type 11, code 0)
 		- Source computes RTT.
 	- Stppping criteria
 		- Successful Arrival 
 		- Host Unreachable
 			- ICMP "host unreachable" (type 3, code 3)
 		
#### IPv6:
 - Inititial Motivation
 	- Address Space
- Additional Motivations
	- Speed
	- Quality of service
- Chnages
	- Expanded Adressing
	`128 bits 2^(128)`
	- Streamlined Header
		- 40 bytes
	 	- Fixed
	 	- No Fragmentation
	- Flows and Priority
- Header 
 	- Priority fieled 
	 	- used to identify priority among datagrams in a flow
	- Flow label
	 	- used to identify datagrams in the same flow
	- Next Header 
	 	- upper layer
	- No checksum 
		- moved to be used only from the upper layers
	- Options
		- pushed out of the header into the payload
	- ICMPv6 
		- additional messages

### Routing algorithm:
#### Routing and Forwarding:
- Graph
	- G = (Nodes, Edges)
		- Nodes 
			- routers 
			- {a, b , c, ...}
		- Edges
			- links 
			- {(a,b), (a,c), ...}
- Routing Protocol Classless:
	- Link-State:
		- complete topology
		- info broadcast 
		- global
	- Distance Vector
		- local topology
		- info exchange
		- decentralized
- Routing Alogorithm Classsification
	- Static
	- Dynamical
		- Periodic Update
		- Link Cost Changes 	
- Cost 
	- Metrics
		- Constant(1) : shortest path
		- Bandwidth-Related 
		- Congestion-Related

#### LINK-State Routing Alogorithm
	`Dijstra's Alogorithm`
- Global Knowledge
	- link Cost
- Goal
	- Least-Cost Paths
- Iterative

- Psuedo-code example 
```
	c(x,y) 	: link_cost
	D(v) 	: Current Cost to destination
	p(v) 	: Predecessor Node on Path to v
	N'      : Nodes with known path
	s       : source
	inf     : infinite
	Inititialization:
		N' = {s}
		for all nodes in n
			if n adjacent to s 
				then D(n) = c(s, n)
			else D(n) = inf
	Loop:
		find m not in N' such that D(m) is a minimum add m to N'
		update D(n) for all adjacent to m and not in N'
		D(n) = min(D(n), D(m) + c(n,m))
		/* new cost to m is either old cost to m or known
		shortest path cost to n plus cost from m to n */
		store p(m) //previous node
		if N' has all nodes inside continue
		else go to loop:
```

#### Distance Vector Routing
`[ dx(y) = minv{ c(x, v) + dv(y)}]`
- dx(y)
	- cost of least-cost path from x to y
- minv 
	- min is taken over all neighbors v of x
			```
				This equation is named after Bellman-Ford and
				it is used for calculating the shortest path.
				The way that it works is neighboring routers
				are sharing their distance vector to each
				other after every share the dx(y) is being
				updated using the bellman-ford algorithm 	
			```  			
- Characteristics
	- Iterative 
		- it repeats itself until all the
					  routers have shared their distance
					  distance vector.
	- Asynchronous
		- does not require all the nodes to
					  work concurently
	- Distributed
		- each nodes acts independatly based
					  on its neibhors distance vector
- Why not great?
	- Detect Change:
		- the algoritm recieves "good news"
					  faster than "bad news"
		- count to infinity problem 
						
#### Link-State vs Distance vector
- Summary: global knowledge vs. local knowledge
- Messages: More (Broadcast) vs. Less( Exchange)
- Message Size: Smaller(Link costs) vs. Larger(Distance vectors)
- Convergence speed: Faster vs. Slower
- Robustness: Better vs. Worse
#### Hierarchial Routing
- How it actually works
	- Gateway Router
	- Autonomous Systems (AS)
		- system created of local routers
	- Intra-AS routing 
		- should use the same routing protocol
					  in the same AS but different AS can
					  run different routing protocol
	- Intre-AS routing
		- should use the same routing protocol
					  (BGP)
#### Routing in the internet
- Types of protocols
	- Interior Gateway Protocol
	- Common Intra-AS Routing Protocols"
		- RIP
		* Routing information protocol
			- Uses Distance Vectors
			- Distance Metric 
				- number of hops
				- max 15 hops / how many subenets you go through
			- RIP Advertisements
				- sents every 30 sec
				- distance vector has
							  max lenght of 25
			- RIP Failure 
				- after 180 sec of no
							  repsonses asumes
							  connection is dead
			- Table Proccessing 
				- routed
					- uses UDP
		- OSPF 	
		* Open Shortest Path First
			- Uses Link State
			- Advertisments 
			- Advanced Features
				- Security 
				- Multiple Same-Cost Paths
				- Multiple Cost Metrics
				- Integrated Multicast
				- Hierarchical OSPF
					- 2-Level Hierarchy
						- Local Area
						- Backbone
					- 3 Roles
						- Area Border Router
						- Backbone Router
						- Boundary Router
		- EIGRP		
		* Enchanced Interior Gateway Routing Protocol
			- Cisco 
				- Proprietary 	
	- Intre-AS Routing Protocol
		- BGP
			- Uses TCP
			- Peers
			- Sessions
				- semi-permanent TCP connection
				- External Sessions (Different ASes)
				- Internal Sessions (Same AS)
			- Path Attributes 
				- prefix + attributes = route
					- advertised prefix includes BGP attributes
				- 2 Important Attributes
					- AS-PATH
					- NEXT-HOP
				- Import Policy
			- Route Selection 
				1. Local Preferences Value Attribute: Policy Decision
				2. Shortest AS-PATH
				3. Closest NEXT-HOP router: Hot Potato Routing
				4. additional criteria
	- Why Different Types in Intra vs. Intre
		- Policy
			- enforce different policies on different layers
		- Scale
			- hierarchical routing 
		- Performance 
			- interiar to be as fast as possible whereas 
						the exteriar does not necessarily need to be that way 
## Link layer:<a name="li"></a><br>
## Network Layer
### Introduction 
- Nodes 
	- Hosts and Router
- Links
	- Point-to-Point
- Frame
	- link layer packet 
- Goal 
`successfully transfer a datagram from one node to adjecent node over a link`
#### Context 
- Different Protocols for different links
- Different Services
	- Reliability
#### Services

- Framing, Link Access
	- encapsulation 
	- MAC addresses
- Reliable Delivery
	- efficient so tcp does not have to do it end to end
- Flow Control
- Error Detection
- Error Correction
- Half-Duplex and Full-Duplex
	- half duplex bidirectional sending capability between two nodes (no at the same time)
	- full duplex bidirectional sending capability between two nodes simultaneously
#### Implementation
- Network Iterface card (NIC):
- Combination
	- Hardware
	- Software 
	- Firmware

#### Adaptors Comunication
- Sender side 
	1. Encapsulates datagram in frame
	2. Adds Error Checking Bits, rdt, Flow Control, etc.
- Receiving side:
	1. Looks for Errors, rdt, Flow Control and etc.
	2. Extracts Datagram
	3. Passes to Upper layer
### Error detection and correction
#### Error detection 
- Error Detection and Correction bits (EDC)
```
These bits are appened to the datagram and contain some information about the data inside.
When received these bits are checked using some alogritm to determine if the data is correct.
```

- Error detection is not 100% reliable
```
Both EDC and the data could be corrupted in a way that the alogritm can produce false-positive.
```
#### Parity Checking 
- Single Bit Parity
	- detect single bit error
`the problem with this method is that if there are even number of bits which are messed up it won't detect it`
- Two Dimensional Bit Parity
	- Detects and correct sigle bit errors
```
Put the data into a 2D matrics. Every column and row will have a parity check bit. The problem with this
method is that in order to send 9 bits, for example, we will have to sent extra 6 parity check bits. This will
result in using more bandwidth than needed.
```
#### Internet Checksum 
- Sender
	1. treats segment contents as sequence of 16-bit integers
	2. checksum
	`addition (1's complemtent sum) of segment conetents
	3. sender puts checksum valure into UDP checksum field
- Receiver
	1. Computes checksum of received segment 
	2. Checks if computed checksum equals checksum field value:
		- NO > error detected
		- YES > no errors detected 
			*does not necesserily means there are no errors
#### Cyclic Redundancy Check
- Modulo-2 Arithmetic
	- Addition
	- Subtraction
	- XOR
- Alogrithm
	1. View data bits as a binary number     	: D
	2. Choose r + 1 bit pattern (generator)  	: G
	3. Find r CRC bits				: R
	4. Receiver divides D + R by G 
	`if ((D * 2 ^ R) XOR R) % G == 0 --> no error`
	- Example 
	```python
	D = b'101'
	R = b'01' 
	r = len(R)
	D_R = (D * 2 ^ r) xor R # 10101
	
	print('No errors detected' if D_R % G == 0 else 'Error detected')
	``` 
#### CRC vs. Checksum
- Why Checksum in Transport layer?
```
CRC is computational intesive and beacuse the Transport layer is implemented in software it will make it very slow
``` 
- Why CRC in Link layer?
```
The link layer will do CRC in hardware which will be faster.
```
### Multiple Access Links and Protocols
#### Introduction
- Types
	- Point-to-Point
	`one sender and one receiver'
	- Broadcast 
		- Shared Wire
		- Shared Medium
- Problem 
	- Single Shared Brodcast Channel
	- Collision between connection
- Solution
	- Mulpiple Acces Protocols
		
- Ideal MAP
	1. Efficient 
	2. Fair restribition of bandwidth 
	3. Fully Decentralized
	4. Simple 
#### MAC Protocols
- Channel Partitioning 
`dividing the channel in pieces`
	- Time Division Multiple Access (TDMA)
	`divides the channel in different time slots`
		- Problem 
		`slot wasiting when a connection is idle during its time slot` 
	- Frequency Division Multiple Access (FDMA)
	`divides the channel based on diffent frequency`
		- Problem
		'same as above, resources can be wasted during idle sate'
	- Code-division multiple access (CDMA)
	
- Random Access Protocols
`whoever wants to transmit, transmits`
	- Slotted ALOHA
		- Assumptions 
			- All frames same size
			- Time Divided into equal sized slots
			- Nodes start to Transmit Only at slot beginnning
			- All Nodes detect collison
		- Operations
			- Transmit in Next Slot
			- if no collision
				- send next frame
			- if collision
			`retransmits based on probability`
	```
		Pros:			| Cons:
	--------------------------------------------------------------
	- Single active node can  	| - Collisions, Wasting Slots 
	transmit at full rate of	| - Idle Slots
	channel				| - Nodes may be able to detect
	- Higly Decentralised		| collisions in less than time to
	- Simple 			| transmit paket
					| - Clock Synchronization
	
  	```
	- ALOHA
	- CSMA, CSMA/CD CSMA/CA
- Taking Turns
`only transimit when it is turn`
	- Polling
	- Token Ring





























































