### Major security roles for web technologies
Web application security engineers
	: must deeply understand how their company's web application works and how to secure it.
Penetration testers
	: ethical hackers who try to find and exploit vulnerabilities and gain privileged access to web applications.
Risk assessors
	: must understand the risk profiles and tolerances within web applications so they can help companies follow best practices and policies.
### HTTP Requests and Responses
client-server model
	: an  exhange of infromation, a cycle of requests and responses between clients and servers.
**HTTP HAPPENS  ON THE APPLICATION LAYER OF THE OSI MODEL**
HTTP methods
![[Pasted image 20221013184514.png]]
	_head useful in diganostics_
		_options gives http methods that the server supports_
			_get and post are the two most common methods_
	Get method
		open a browser and when you go to amazon.com the client (browser) asks to GET the data that the URL points to.
			![[Pasted image 20221013184830.png]]
			1. Request line contains the request method, the name of the requested resource and the version of HTTP in use
			2. Headers contain additional details about the requested resource.
			3. A blank line indicating the end of the request.
			4. Request body (optional) 
	Post method
		Once your browser goes to amazon.com, you log in to your account sending a post request that contains your credentials to log in.
		![[Pasted image 20221013185751.png]]
Headers
	can include important infromation
		![[Pasted image 20221013185122.png]]
Requests with Query Parameters
	"?" signifies the start of the query
	"tag=latest" is a key-value pair where the key would be tag and the value would be latest
	"&" signifies a second key-value pair
	"author=jane" another key value pair
curl
	a command-line client that allows us to send data to and from servers.
#### Cookies
**Remember http is stateless meaning an open constant connection between the client and web server. We solve this with cookies.**
Sessions
	: unique server-side sets of user data used to customize webpages for the specific user accessing them.
Cookies
	: small pieces of text data the, when sent by an http server's response header, are saved by the user's http client (browser)
#### Components of a typical web server
Front-end Server
	: responsible for displaying webpages and styling them in a readable format
Back-end Server
	: Executes business logic and writing or reading corresponding data to and from a database.
Database
	: Stores infromation about employess, such as their IDs and names.
Application -> Front-end Server -> Back-end Server -> Database
Monolith
	: a single machine that hosts all the components required to sere a website or application.
		_the monolith contains the components of a web server  i.e. front end back end and database_
Microservices
	: Separating application components into their own machines is called microservices.
		_this gives opportunity to scale by adding more servers and creates an ability to isolate compromised services._
API
	: implementation of new protocols or features onto an existing software application to alter the wayt hat application is used or accessed.
		_machine to machine communication and can deliver that data to multiple systems._
Stacks
	Contain a base opoerating system, front-end software, back-end software and a database.
		BaseOS
			_alpine, redhat, ubuntu, suse_
		Font-end
			_apache, microsoft IIS, NGINX_
		Back-end
			_php python nodejs_
		Database
			_Mysql, microsoft sql, mariaDB, CouchDB, PostgreSQL, mongoDB_
	LAMP
		Linux
			Apache
				Mysql
					PHP
	WIMP
		Windows
			Microsoft IIS
				Microsoft SQL
					Powershell
	LEMP
		Linux
			NGINX
				MariaDB
					PHP
Docker
	: command line utility for running virtual containers
Containerization
	: the process of packaging all the requirements for a microservice into a container
`docker-compose up

```bash
cd /home/instructo/Cybersecurity-Lesson-Plans/14-Web_Dev/deploying_testing_demo
less docker-compose.yml
	# observe the configuration services adn properties

docker-compose up

#open Firefox -> browse to 192.168.1.2
	#observe "It works!"

docker container-ls
docker exec -it demo-db bash
	> env
		#observe user/pass
	> mysql -u demouser -pdemopass
		> quit
	> exit
docker-compose down
```
#### SQL
Databases store data like a spreadsheet in a table. columns are a piece of data and rows are an item.
	CRUD is how we interact  with the data.
		Create
			add new entries to the database.
		Read 
			View entries in a database.
		Update
			Modify existing data in a database.
		Delete
			Destroy data in the database
	SQL injections
		: a type of web apoplcation attack intended to manipulate queries so that an attacker can use a data base in ways the developers did not originally intend.
```bash
docker exec -it activitydb bash
	> mysql -u admin -p123456 -D goodcorpdb
		> SELECT * FROM employees;
		> SELECT * FROM employees WHERE department='Operations';
		> INSERT INTO employees (firstname, lastname, email, department) VALUES ('Luke', 'Latte', 'llatte@goodcop.net', 'Logistics'):
		> SELECT * FROM employees;
		> DELETE FROM employees WHERE email='llatte@goodcop.net'
		> SELECT * FROM employees;
```
