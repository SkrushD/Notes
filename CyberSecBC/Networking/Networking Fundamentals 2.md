### IPs and Routing
Dynamic Host Configuration Protocol
	: a client-server based protocol on your local network that is responsible for managing and assigning IP addresses.
		_DHCP uses UDP ports 67 and 68_
			DORA connection for dhcp discover, offer, request and acknowledge
Network Address Translation
	: method of mapping private ip address to a public IP address and vice versa
		Step by Step
			1. Create the packet _creates packet with destination ip/port and the source ip/port_
			2. Packet to NAT Table _The packet is sent to the inernal router, which creates a record in the NAT table._
			3. Going Public _The router modifies the packet and replaces the source IP with the network's public ip address._
			4. Source Receives Packet and Responds _source receives the packet, it creates a response packet_
			5. Back to NAT _When the router receives the packet, it checks the NAT table to see exactly which device is expecting this packet. It will update the packet and translate the IP to include the followig new packet details_
			6. Return of the Packet _your device, with private IP x.x.x.x, recieves the packet. You can now view the requested content._
DHCP Attacks
	Sending a large numner of DHCP messages over the network requesting ip addresses could cause the server to run out of IPs to issue. This is called a **DHCP Starvation** 
		Defending against this can be setting a maximum threshold for requests but this would also cause network slow downs just due to many users needing ips
	Once this DHCP server is starved an attacker may be able to use a **DHCP Spoofing** attack that would provide them man in the middle access by tricking endpoints into thinking it is the DHCP server.
		Protecting against this can be by DHCP snooping
			: a process implemented on a network switch that inspects packets to confirm that they're legitimate DHCP offers, and block those it deteminges to be unauthorized.
Routing Schemes
	Unicast
		: single device delivers a message to another single, specific device.
		_phone call between two people_
	Broadcast
		: single device broadcasts to all devices on that same network.
		_DHCP offer messagte the is broadcast to entire LAN_
	Multicast
		: device sens a message to devices that have expressed interest in receiving the message.
		_subscription based service sends network traffic to its subscribers._
Static Routing
	: the manual configuration fo a network route, typically done by a network administrator.
Dynamic Routing
	: solves the fault tolerance issue by allowing the network to act on its own to avoid network blockages.
		Routing Protocols
			: consider to primary criteria to determine the optimal path which are **distance** and **speed**.
				_distance measured in hops_ distance-vector protocols use only hops
					ex. Routing Information Protocol or Enhanced Interior Gateway Routing Protocol
				_speed is detemined by the time it takes between source and destination._ link-state protocols use speed as criteria.
					ex. Open Shortest Path First
##### Wireless Networking
Wifi protocol 802.11
	: the type of wireless technology that uses radio waves to provide wireless internet and network connections.\
Basic Service Set Identifier (BSSID) 
	the mac address for the wireless access point
		Since this is not really human readable the wap also broadcasts a **Service Set Identifier (SSID)**
Wireless Security
	Wired Equivalent Privacy (WEP)
		first kind of wifi sec. uses encryption to provide protection and privacy to wireless traffic.
	WiFi Protected Access (WPA)
		Created due to vulnerabilities discovered in WEP
	WPA2
		Decently secure with a very strong password
Wardriving
	: driving around an area with a computer and a wireless antenna to find wireless LANs that may be vulnerable.
Warchalking
	: Marking locations with chalk so sites can be exploited these acess points at a later time.
Warflying
	: Using drones to find vulnerable access points.
EvilTwinAttack
	create a fake wireless access point to trick unsuspecting users into connecting to the attacker's wireless access point.
### Email Networks and Security
Domain Name Systems
	: the phone book of the internet, looks up the ip address associated with  the domain name on the internet
		_When you send an email, your email server needs to find the mail server name for the domain receiving the email._
DNS zone file
	: an actual file containing all the DNS records for a particular domain.
		_zone files have a TTL indicating how long the DNS cache will remember the infromation before having to make a request for an updated copy._
DNS Record Types
	A record
		: translates a domain to an IP address.
			_A record for widgets.com points to 23.43.54.234_
	PTR record 
		: the opposite of A records, this transaltes an IP address into a domain.
			_record of 23.43.54.234 to widgets.com_
	CNAME record
		: an alias record used to point one domain to another domain.
			_points widegets2.com to wedgets.com so a second DNS record isn't required._
	SOA record (start of authority)
		contains admin details about a domain.
			_Email addresss of the admin, TTL value, when the domain was last updated_
	NS record (name server)
		: indicates which server contains actual DNS records for a domain, also known as authoritative name server.
			_device wants to know the IP for widgets.com and makes a DNS request for the auth naem server. Once the NS record is confirmed, the device can trust this record for obtaining the IP from the domain._
Domain vs. Subdomain
	widgets.com // marketing.widgets.com
MX record (mail exchange)
	: directs emals to a specific mail server for a domain.
		_if an email is sent to user@widgets.com, the sender will valdate that the MX record for the domain is mailhost.widgets.com, then will direct emails to that server._
TXT record (text)
	: was created to include human-readable notes, such as associated company name. These also include computer-readable data.
		_the txt record will contain an **spf record** (sender policy framework), which determines if an email is from a trusted server._
nslookup
	: allows us to easily look up the DNS records of any domain
```bash
nslookup #command
>set type=mx #checking mx records
>google.com #domain we are checking.

```
Mail Transfer Agent
	: email server
POP3 vs. IMAP (110/995 vs, 143/993)ports
	POP3 pulls the email off of the server and is not stored on the server whereas IMAP copies it off the email server so it is not missing after being retreived
![[Pasted image 20220922192510.png]]
x- headers are custom headers which could help flag certain suspicious material or deliver material that you know isnt suspicious.

Email Security Protocols
	PGP
		Pretty good privacy
	S/MIME
		Secure/Multipurpose INternet Mail Extensions
	The challenge of PGP and S/MIME is that they involve coordination and setup between the email sender and the email receiver.
		Today email is usually encrypted with TLS and is sent over port 587
Email Spoofing
	: is when an email is designed to trick the receiver into believing it is coming from a trusted source.
		_detection can be found through analyzing the **from** email header and the **received-spf** email header and also the **received** email header_
SMTP on ports 25/587
