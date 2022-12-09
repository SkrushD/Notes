Offensive Security
	: using proactive measures to protect networks, systems, and applications from malicious attacks.
		_Involves testing a technology for potential vulnerabilities. 
		Requires a thorough understanding of the technology being tested._
Attack
	: The method or action used to exploit the vulnerability.
Vulnerability
	: The weakness within a function fo the web application that can be exploited.
Injections
	: when an attacker supplies untrusted input to an application.
		_that malicious input, also known as a **payload**, contains malicious data or code that is then processed as part of a query or command that alters the way a program is intended to function._
			**Injections commonly occur in fields and forms on web apps**
	Cross-Site Scripting (XSS)
		an injection type that occurs when an application takes in malicious user input which inadvertently executes user-supplied code.
			_stored xss would plant the exploit script on the database and could be executed by the database every time someone accesses the website._
			_Reflected (non-persistent XSS) depends on the user input being immediately returned to the user and not stored on the application's server._
		JavaScript
			: a programming language that allows web developers to add complex web features that dynamically update web content and add life to a webpage.
	SQL Injection
		: works against an application by sending requests to a SQL database through user input
			Input Validation
				: a method of validating the data input with a predefined logic, ensuring that the input is what the application is expecting.
Mitigation Methods
	Client-Side
		: involves coding the predefined logic into the webpage.
	Server-Side
		: adding the predefined logic into the code on the web server.

#### Back-End Component Vulnerabilities
: vulnerabilities in back-end components could potentially allow a malicious actor to access or display confidential files or documents that exist on an orgainzation's private server.

Directory or Path Traversal _(reads files)_
	: occurs when an attacker accesses files and directories form a web application outside a user's authorizd permissions.
		_could be leveraged to access confidential business documents, source code, or system files that exist within an organization's private server- directly from a web application._
			uses relative and absolute paths in order to read other files on the target system. 
		mitigation for this type of attack could be using input validation to restrict the user's ability to modify the file being accessed. The web server user "www-data" should not be able to access /etc/shadow and other system files which is another mitigation to this attack.
Local File Inclusion
	: a web application vulnerability in which an attacker tricks the aplication into running unintended back-end code or scripts that are local to the application's filesystem
		_could be used to leverage execution of scripts or files that the user would not normally have access to on the server._
Remote File Inclusion
	: a web application vulnerability in which an attacker trick the application into running unintended back-end code or scripts that are remote to the application's filesystem.
		_could be used to leverage execution of scripts or files that are not local to the web application's server and provides the user remote code execution._
OWASP #1 Broken Access Control
	: Restrictions on what authenticated users are allowed to do are often not properly enforced.

```bash
python3 -m http.server 9001 # to stand up webserver to host shell.php for RFI
```

Identification and authentication failures
	: are risks that permit an attacker ot either access or bypass the authentication methods that are used by a web application.
Web Proxy
	: an intermediary betweent hte client and the server. Internet traffic flows through the proxy on the way to its intended destination.
Sessions
	: Unique server-side sets of user data that are used to customize webpages for the specific user accessing them.
Cookies
	: small pieces of text data that, when sent by an HTTP server's response header  are saved by the user's http client.
Session Hijacking
	: a malicious user can obtain another usas unique session cookie and hijack the victim's private session.
![[Pasted image 20221108192350.png]]
Burp Repeater
	we can use repeater to simply reissue the same HTTP request, Burp Repeater can be used to modify the request one at a time
		On the HTTP Request panel, an attacker can simply change any data in the request to check how it changes the response.
			Attackers can use this to try attacks against different hosts, resources, and types of HTTP requests.
Burp Intruder
	we can use intruder to automate issuing multiple http messages.
		