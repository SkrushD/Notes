![[Pasted image 20221003205447.png]]
### Network Security
	: the process of taking physical and software preventative measures to protect the underlying networking infrastructure from unauthorized access, misuse, malfunction, modification, destruction, or improper disclosure, thereby creating a secure platfrom for computers, users and programs to perform their permitted critical programs to perform their permitted critical functions within a secure environment.
Firewalls
	: techincal security control that distinguish between trusted and untrusted network traffic and network connections.
		_provide a layer of protection by analyzing data leaving and entering a network._
	Network Firewall
		: in front of a router to block malicious internet traffic from entering the private network.
	Host Firewall
		: runs on the machine that it blocks traffic to and from
	_both firewalls work the same way as far as what they monitor and protect from._
	**Firewalls on the OSI**
		MAC Layer Firewall
			: compare the MAC addresss of a device against an approved list.
		Packet-Filtering Firewalls (stateless)
			: create checkpoints within a router and examine packets as they progress through an interface. If the information does not apss the inspection, it is dropped.
		PFF (stateful) & (stateless)
			: stateful firewalls determine if a packet is trying to establish a new connection(**new state**), is part of an existing connection(**established state**) or neither new or existing (**rogue**)
				_stateful firewalls examine the connection as a whole instead of each packet_
			: stateless firewalls inspect each individual packet and create checkpoints within a router examining packets as they rogress through an interface.
		Circuit-Level Firewalls
			: verifies the three-way TCP handshake to ensure packets are form legitimate sources
		Application(proxy) Firewalls
			: obscures the destination from the source, creating an additional layer of anonymity and protection for the network.
				_these firewalls use deep packet inspeciot and stateful inspection to determine if incoming traffic is sage or harmful._
	Uncomplicated Firewall (UFW)
		: multifunctional firewall that provides stateless and stateful packet filtering.
		![[Pasted image 20221004185840.png]]
	Firewalld
		: dynamically managed firwall that uses zones to divide network interfaces into groups of shred trust level. The zones are assigned sets of rules dependong on the needs and restrictions of each zone's interfaces
UFW DEMO
```bash
#Reset all rules to defaults
sudo ufw reset

#Check status of firewall
sudo ufw status
	"shows inactive"
#Enable ufw at boot
sudo ufw enable
sudo ufw status

#Setup default rules
sudo ufw default deny incoming
sudo ufw default deny outgoing

#Setup needed rules
sudo ufw allow 80 #http
sudo ufw allow 443 #https
sudo ufw allow 22 #ssh
sudo ufw allow 110 #pop3

#Check rules
sudo ufw status

#Setup deny rule
sudo ufw deny 110
sudo ufw status

#Delete rule
sudo ufw delete deny 110
sudo ufw status
sudo ufw status verbose

#Restart ufw
sudo ufw reload
sudo ufw disable
sudo ufw enable

# All these rules are for current run time and will be gone on reboot. There is a permanent argument.
```
FIREWALLD DEMO
```bash
#Start firewalld
sudo /etc/init.d/firewalld start

#Zone views
sudo firewall-cmd --list-all-zones
	#observe work zone

#Bind zone to interface
ifconfig
	#observe interfaces
sudo firewall-cmd --zone=work --change-interface=eth1
sudo firewall-cmd --zone=work --list-all
	#observe eth1 set

#List running services
sudo firewall-cmd --get-services

#Block target ip traffic
sudo firewall-cmd --zone=work --add-rich-rule='rule family="ipv4" source address="10.10.0.10" reject'

sudo firewall-cmd --zone=work --list-all
	#observe rich rule
	#note lost when rebooted, use --permanent

#Block icmp
sudo firewall-cmd --zone=work --add-icmp-block=echo-reply --add-icmp-block=ehco-request

sudo firewall-cmd --zone=work --list-all
	#observe icmp blocks
```
USEFUL PROCESS COMMANDS 
```bash
systemctl status <port> #checks port services like ssh

ss -auntp <port> #shows socket layer information showing listening ports

```
Firewalking
	: allows attacker to perform network analysis to determine which Layer 4 protocols a specific firewall allows.
NMAP DEMO
```bash
#OS Fingerprint Scan
sudo nmap -O -p 1-500 --osscan-guess "target"
	#compare on target machine with:
uname -a

#Service/Daemon Name Scans
sudo nmap -sV "target"
	#observe service versions
	#https://cve.mitre.org/ can be used to find vulns based on service version

#Service Type and OS detection, Fast
sudo nmap -A -T4 "target"

#Device and Port enumeration
sudo nmap -sU -F "target" #udp fast scan
sudo nmap -sA "target" #ack scans; stateful detection
```

### IDS and Snort
Intrusion Detection Systems
	: tools that can both analyze traffic and look for malicious signatures.
		_IDS is passive and will not respond to attacks but logs and documents information for future analysis._
			Network flavors and host flavors of IDS systems
				NIDS sniff packets and log them in a server to be evaluated by a security professional while several HIDS all log traffic locally and send it to a central server.
	Signature-based
		Compare patterns of traffic to predefined signatures.
	Anomaly-based
		Compares patterns of traffic against a well-known baseline.
	IDS connects through a network TAP or a mirrored SPAN port.
		TAP
			hardware device that provides access to a network. transit both in and outbound data streams on separate channels at the same time, so all data will arrive at the monitoring device in real time.
		SPAN 
			also known as port mirroring, sends a mirror image of all network data to another physical port where the packets can be captured and analyzed.
Intrusion Prevention System
	: do everything an IDS can but also respond to these attacks by blocking malicious traffic, preventing it from being delivered to a host on the network.
		IPS connects inline with the flow of data between the firewall and network switch, requiring more robust hardware due to the amount of traffic, and will block and log a threat not requiring an administrator to intervene.
IDS alerts
	: a message that is sent to an analyst's console as an indecator of attack (IOA)
		Indicator of attack
			indicate attacks happening in real time. Allows for a proactive approach to intrusion attempts, and is more of a focus on revealing the goal and intent of an attacker.
Snort
	: performs real time traffic analysis and can log packets on a network.
![[Pasted image 20221006190204.png]]
		Snort uses rules to detect and prevent intrusions by
		1. Reading a configuration file.
		2. Loading the rules and plugins.
		3. Captruring packets and monitoring traffic for patterns specified in rules.
		4. When traffic matches a rule pattern, generating an alert and logging the matching packet for later inspection.
	![[Pasted image 20221006190405.png]]
```bash
alert= action snort will take
tcp= applies rule to all TCP packets.
any= Applies to packets coming from any source IP address.
any= Applies the rule to packets from any port
any= destination IP address.
any= 21
msg:= the message printed with the alert.
```
Network security monitoring
	: uses a variey of data analysis tools to detect and stop threats after most front-end layers are compromised.
		_threat-centric, focusing on the adversary and visibilities of the attacks and not the response._
	Detection
		: alert is generated in the sguil analyst console.
			Collection
				: the event is observed and the data is tored in the from of a PCAP file.
			Analysis
				: the alert data is identified, validated, documented, and categorized according to its threat level.
			Escalation
				: All relevant parties are notified about hte security incident.
			Resolution
				: The process of containment, remediation, and any additional necessary response.
	Response
		security team responds to a security incident.
Command and Control (C2/CnC)
	: are used to create a specific type of aler for attacks that use persistence as part of their attack campaigns.
		_Infected hosts make callbacks to C2 servers. These callbacks (referred to as "keep alives" serve as beacons that keep the back channel open to enable access in and out of the network._
End-point Detection Response (EDR)
	: these are host based intrusion detections systems (HIDS) that can detect commands being run the same way snort analyzes packets coming into the network. i.e. set rules to recognize patterns or odd commands being used on host machines.
Endpoint telemetry
	essentially host-based monirtoring of system data.
### Threat Intelligence
![[Pasted image 20221011203941.png]]
Threat Intelligence Cards
	: document the TTPs used by an adversary to infiltrate a network, which are established by Computer and INcident Response Teams (CIRTs).
		_includes actors and capability and intents of threat groups_
Cyber Kill Chain Framework
![[Pasted image 20221011204357.png]]
	_a military resource that has been largely overshadowed by the MITRE ATT&CK framework._
