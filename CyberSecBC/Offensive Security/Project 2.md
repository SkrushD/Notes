Rekall has a brand new web application and several linux and windows servers that maanage their businesses.
flag 1 - 3
	<script>alert(xss)</script>
	![[Pasted image 20221130170156.png]]
		Reflected
		![[Pasted image 20221130170302.png]]
		Reflected xss with user input validation bypass
		![[Pasted image 20221130170439.png]]
Flag 4
	Information Disclosure
	![[Pasted image 20221130172306.png]]
Flag 5 & 6
	Local File Inclusion or File Upload vulnerability
	![[Pasted image 20221130170720.png]]
	Advanced File Upload vulnerability
	![[Pasted image 20221130170819.png]]
	checks for jpg only allows everything else.
flag 8
	Information Disclosure.
		Admin credentials are saved in the source code of the webpage.
	![[Pasted image 20221129194029.png]]
	dougquaid:kuato
flag 7
	sql injection
	![[Pasted image 20221130171236.png]]
	setting the condition to true would return the entire table that is being checked for login credentials
flag 9
	information disclosure 
		Secrets should not be hidden in the robots.txt file
Flag 10
	Command Injection
	![[Pasted image 20221130171029.png]]
	adding "&& whoami" to the string we want to lookup allows us to see at the end we are using the user www-data


hosts 
192.168.13.0/24 scan returned us ranges of 10-14, 20, and 1
	192.168.13.10 
		8009 and 8080 open
	192.168.13.11
		80 open
			Drupal CVE-2019-6340
	192.168.13.12
		8080 open
	192.168.13.13
		80 open
	192.168.13.14
		22 open
	192.168.13.20
		closed 1-1000
	192.168.13.1
		5901, 6001, 10000, 10001
OSINT
flag 1
	Dossier on osintframework.com
		![[Pasted image 20221201214744.png]]
flag 2
	34.102.136.180
flag 3
	crt.sh
		![[Pasted image 20221201214920.png]]
flag 4
	5 hosts // one is us and one is unavailable
flag 5
	192.168.13.13
flag 6
	![[Pasted image 20221201220422.png]]
	Apache struts Outdated version
flag 7
![[Pasted image 20221201220711.png]]
	nmap scan
	![[Pasted image 20221201220645.png]]
	search msfconsole **RCE**
	![[Pasted image 20221201220828.png]]
flag 8
Google search shocking exploit
	returns results for shellshock
		search msfconsole
	![[Pasted image 20221201221331.png]]
	check sudo perm // cat /etc/sudoers
	![[Pasted image 20221201221557.png]]
flag 9
	same server // cat /etc/passwd
	![[Pasted image 20221201221654.png]]
flag 10
	![[Pasted image 20221201222013.png]]
	search msfconsole jakarta
	![[Pasted image 20221201222039.png]]
	search -f *flag*
flag 11
	search msfconsole drupal
	![[Pasted image 20221201222729.png]]
	`meterpreter> getuid
	www-data
flag 12
	ssh alice@192.168.13.14
	password: alice
		![[Pasted image 20221201222928.png]]
		gives root


hosts
172.22.117.0/24
Win10 .20
DC .10
![[Pasted image 20221205190513.png]]
nmap scan
Flag 1:
![[Pasted image 20221207181105.png]]
Tanya4life
Flag 2:
![[Pasted image 20221207182931.png]]
Flag 3:
![[Pasted image 20221205190343.png]]
ftp into user with anonymous and blank password
