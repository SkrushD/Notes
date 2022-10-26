Client-server model
	: a network computing model that defines how resources and services are shared across a network.
		_this two-way conversation between the client and server is known as the request and respone method of device communication._
Network security
	: the practices and policies used to protect and monitor a computer network's resources against threats and risks.
Local Area Network
	: a private computer network that connects devices in smaller physical areas.
		_advantages include network speed and performance, network security and versatility._
Wide Area Network
	: a network used to connect multiple LANs.
		_advantages include being able to share or access resources across a much larger geographic area.
		while disadvantages come in forms of security. Your data is travelling wide distances increasing attack surfaces and making troubleshooting significantly more difficult._
Network topology
	: the design or technique with which computers are set up on a network.
		- can determine the way data flows within a local area network.
		- can also impact the performance and speed of a network.
		- there are variteies of network topologies, with names based on the geometric shape of their design.
	Ring Topology
		: each device is connected to the next device in the chain.
			Bidirectional or Unidirectional
				: Bidirectional allows traffic to move in either direction, while unidirectional flows in a single direction.
	Linear Topology
		: In a linear topology, each device is connected to the adjacent device by a two-way link.
	Star Topology
		: all devices in the network are attached to a central node.
	Bus Topology
		: every device is attached to a central data link. when a device transmits data, it sends it on the link, at which point every device on the network can receive it simultaneously.
	Tree Topology
		: a special type in which many connected devices are arranged like the branches of a tree. In a tree, there can be only one connection beteween any two connected devices.
	Fully Connected
		: every device on the network is directly connected to every other.
	Mesh
		: similar to fully conected however not every device is directly connected.
	Hybrid
		: any combination of the above.
##### Devices
Router
	: a networking device that forwards (routes) resources to other networks.
		_routers connect two LANs, two WANs, or a LAN to a WAN_
Switch
	: a networking device that forwards resources within a network. In other words, switches connect devices within a LAN.
		_- typically used in large businesses that have many computers.
		- feed into routers.
		- intelligent devices, which means they can be programmed to direct resources to certain comuters._
Hub
	: serves the exact same purpose as a switch, except it is not an intelligent device. Therefore, hubs cannot be programmed.
		_Instead, they direct a copy of the exact same resource to all computers they are connected to._
Bridge
	: basically a switch that only has two connections. One in, and one out.
Network Interface Controller (NIC)
	a type of computer hardware that connects a computer to a computer network.
		_usually a cicuit board or chip installed on a computer. Computers must have a NIC in order to receive or send resources._
Modem
	: converts resource data into a formate that the next ype of connection can understand.
		_your computer speaks digital and ISP speaks analog. this translates._
Wirelesss Access Point (WAP)
	: give wireless devices the ability to connect to a wired network.
Firewall
	: an intelligent nework security deveice that monitors incoming and outgoing traffic based on security rules.
Load Balancers
	: an intelligent network security device that distributes that incoming network traffic across multiple servers.
		_balance traffic so that systems can not be overwhelmed._
Demilitarized Zone (DMZ)
	: a smaller subnetwork within a LAN used to add an additonal layer of security to an organizations LAN, protecting secure data within the internal networks.

Internet Protocol address
	: a numerical network address associated with a device such as a computer, printer, router or server.
MAC address
	: the address to your computer which is how your switch knows what computers are on the network and directs traffic accordingly.
		==xx:xx:xx==:xx:xx:xx
		==show the manufacturer==
Uniform Resource Locator
	: full address of a resource on the internet.
![[Pasted image 20220913211243.png]]
DNS hijacking
	: a type of network attack that exploits DNS vulnerabilities to divert web traffic away from legitimate servers and towards fake or malicious servers.

#### Day 2 Ports, Protocols and the OSI model

Protocol
	Impose strucfture by specifying the precise meaning of keywords, and where in a message they must appear.
Network packet
	message adhering to protocol rules
Header
	helps to identify details about what is giong on with the packet.

IPV4 packet structure (0100)
![[Pasted image 20220915184144.png]]
IPV6 header 0110 (_ipv6 has different identifiers in its headers, less than ipv4_)
![[Pasted image 20220915184310.png]]
Common ports and services.
![[Pasted image 20220915191443.png]]

Encapsulation
	the process of placing headers, and sometimes trailers, around the data to direct it to its destination.
Decapsulation
	the process of removing the headers, and sometimes trailers, around the data to confirm the data has reached the destination.

Why does OSI matter?
	Helps us easily understand new protocols.
		_you find NetBIOS is a layer 5 protocol, you immediately know that its involved in manging user sessions, even if you've never heard of NetBIOS before._
	Helps deremine where problems in the network are occurring, even if we don't have frull knowldge of the issue.
		_you realize you're haveing a layer 3 issue, you know you should start investigating your routers, even if you don't know exactly what the problem is._
	Makes it easier to communicate where a security attack has occurred and what should be done.
		_you know a SQL injection attack is occurring, you can explain to your management that you need a Layer 7 web application firewall to identify and mitigate the attack._

### Wireshark
```bash
sudo wireshark
# select device to capture from (NIC)
	Packet list
	Packet details
	Raw hex and ascii data
```

### Day 3 Layer 3, 4, and 5

Enumeration
	: the process of gathering data for a specific network, usually for the purpose of finding ways to gain acces into that network.
#### Layer 2
Arp requests
	send out to everyone on the LAN to find the address
		_correct IP responds while others ignore the connection request_
ARP Cache Timeout
	Dynamic arp entries can be changed with furture arp replies
		_Dynamic ARP entries will only stay in the ARP cache for a limited period of time, known as the ARP cache timeout.
		ARP cache timeout expires, the record is removed form the ARP cache and any future requests for the host require a new ARP request._
ARP Spoofing / ARP Cache Poisoning
	attackers can send a spoof arp message to the lan, directing all traffic intended for the good host to the attacker's MAC address.
		_Protect against it with static arp entries_
ping
	: a utility used to determine whether a host is operating and responding to echo requests
		_accessed through the ICMP protocol (Internet Control Message Protocol)_
`ping -c "count" domain/ip`
`fping -f file.txt`
Pings TTL can tell you the operating system of device
windows TTL 127
linux TTL 64
TCP three way handshake
	: the process of establishing a reliable connection to transmit data between devices.
![[Pasted image 20220919202349.png]]![[Pasted image 20220919202410.png]]
UDP
	: connection-less protocol - it doesn't require a handshake
Port states are as follows
	Open
		_port is accepting connections._
	Closed
		_port is not accepting connections._
	Filtered
		_the port may be open, but a firewall or another network device is likely blocking it._
