}Default windows structure
C:\
	PerfLogs\
	ProgramFiles(x86)\
	ProgramFiles\
	ProgramData\     [ususally hidden]
	Users\
		username
			desktop
			downloads
			documents
		Windows\
			System32
				config
				drivers
					etc
						hosts
						networks

Environment variables
	: special values that contain informatiuon about the syste, such as the user's homje directory or the system's program files directory
Common Env Variables // wrapped with %percent%
	CD // Current Date
	DATE
	OS
	ProgramFiles
	ProgramFiles(x86)
	TIME // Current Time
	USERPROFILE // C:\Users\{username} 
	SYSTEMDRIVE // C:\Windows
	SYSTEMROOT // C:\Windows
CMD basic commands and linux alternates


CMD
**Must be run as administrator for roo commands there is no sudo command.**
		-help // "/?"
Windows Management Instrumentation Command (wmic)
	: a tool used to query system information and diagnostics, such as OS and hard disk info.
WMIC command
![[Pasted image 20220912183158.png]]
![[Pasted image 20220912183214.png]]
		alias // is the windows component that wmic queries
		verbs // are actions we want to complete with the wmic command.
			get, push, etc.
		properties
			caption // one-line description of the given alias like `get caption'
			value // properties and values of an alias and lists each on separate lines. `get value`
Net command
	: manage users accoutns, groups, and password policies
		net user // lists all users
		net user _username_ /add
		net localgroup Administrators _username_ /add
		Local Group Policy Editor for Editing password policy
			computer config
			windows settings
				security settings
					account policies
						password policy
PowerShell
	: a powerful scripting langueage we can use to locally and remotely manage microsoft's line of products.
Object
	: is Microsoft's name for every component in a system that PowerShell recognizes and interacts with.
Powershell cmdlets and bash equivalents
![[Pasted image 20220912184418.png]]

Paramaters
	-Path // specifying the location of the cmdlet
	-Name // parameter specifying the directory's name for the cmdlet
	-ItemType // specifying the type of item we want to ceate.

`Get-command` // search
`get-help` _cmdlet_

##### Day 2

Log files
```PowerShell
	`Get-WinEvent -loglist` # lists log files
	`Get-WinEvent -logname` # pulls logs of a specific process i.e. specify "Security" or "Application"
	`Get-WinEvent -logname Security -maxevent 10 } | convertto-json | out-file -filepath C:\Logs\Recent_Sec_Logs.json`
	#example from Activity 1
```

Choco = windows version of apt
```Powershell
Choco info *package* // package info
Choco install *package* // install package
```
CSV files
	: comma separated variables _contain lists with multiple columns_
![[Pasted image 20220912194944.png]]
	appxpkg, name, description
	_Microsoft.ZuneMusic, Zune, Microsoft's Zune Music Player_
Foreach Loops
```PowerShell
	Foreach ($value in $value) {
		#dosomething // command goes here.
	}
```

##### Day 3 Active Directory

Active Directory
	: the central databasing and management system for enterprise-scale windows environments.
		Security principals
			: are AD ==objects== that can be authenticated, such as users and groups. Permissions can be assigned to Security Principals giving them only the access they need.
		Resources
			: are the files, networking components, and printers that users need permission to access. Permissions depend on roles and responsibilities within the company.
Authentication
	: Allows users to prove their identity useing a password, token, or biometric key.
Authorization
	: Provides or denies users permission to material.
Objects 
	: are the users, groups, and computers, and the file shares, network printers, and other resources that users need to access.
AD Authentication
	LDAP
		: _Lightweight Directory Access Protocol_ is a standardized protocol for adding, deleting, and editing objects. If Active Directory is a jounral of information, LDAP is the pencil and eraser
	Kerberos
		A ticket-based protocol now the default authentication protocol for Windows Server domains. Provides direct encrypted sessions between users and networked resources.
	NTLM
		: _New Technology LAN Manager_ is an authentication protocol that has become outdated because of pass the hash attacks. (not really it is still around and used alot.)
Organizational Units (not groups)
	: are logical groupings fo an organizations assets and accounts.
		_You can link group policies to OUs, bur not groups.
		You can give file, folder, sharing, and other resource permissions to groups, but not OUs.
		Groups have security idntifiers, but OUs do not.
		Users can belong to manyh groups, but only one OU_
Group Policy Objects (GPOS)
	: are packages of policy settings that fonain one or more groyup policy
