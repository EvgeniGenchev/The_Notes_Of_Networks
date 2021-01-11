# The_Notes_Of_Networks

The following chapters will include notes that I have made during reading Computer Networking: A Top-Down Approach, 6th Edition.

## Delay, Loss and Throughput:
### Sources of packet delay:
#### Processing
```
    The router computation that need to be done.
```
    
### Queuing 
```The time the packet waits its turn to be transmitted to the mediam.```

### Transmition 
``` The transmition of the packet from the queue to the mediam.

    L: lenght of the packet 
    R: transmission rate
    
    Formula: L/R

```
### Propagataion
```   The time that the signal needs to move
			accross to the mediam. Propagataion time
			is close to speed of light.
      
      s: sec 
      D: distance from node A to B
      Formula: D/s 
```

### Throughput:
		The rate at which the bits are transfered between the
		sender and the reciever  

## Network layers:
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

##E2E vs P2P:
		+---------------------------------+
		|End-to-end     |  Point-to-point |
		|---------------+-----------------|
		|Application    |  Network        |
		|Transport      |  Link 	      |
		|			    |  Physical       |
		|---------------|-----------------|


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
Adressing the hosts:
    -gives IP
Provides routing data:
    -in order to route data over multiple hops
Congestion Control:
-coping wiht having more data than it can be sent 
			without any significant delays or loseses
 Administration:
		-provide functionality to administer routes

		LINK:

			Functions:
				Data Link Layer:
					Framing:
						-Breaking the data into frames that will fit accross the 
							network.
					Error Control:
						-Detect when packets are corrupted and perhaps correct them.
					Flow Control:
						-Process of keeping the receiver from being overwhelmed from
							the sender. If a there are more packeges arriving than the 
							receiver can take, this function will help slow down the speed
							at which the packets are arriving
				Mediam Access Control Layer:
					Sharing the Chanel:
						-That is the address that is used to resolve contention on the chanel.
							The MAC layer lets the chanel be shared fairly by the devices that 
							want to use it at the samr time

		PHYSICAL:

			Transmittion of Raw bits:
			 	-Transmittion of Raw bits from node to node


		-------term---------
		ENCAPSULATION:

			Adding additional information to the packege in order for the packege 
		to be sent using another higher level protocol.

		progression of the package:
		message ---> packet ---> datagram ---> frame 

		-----end term-------


