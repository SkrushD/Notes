### Security Information and Event Management
Continuous monitoring
	: refers to the processes and technologies used ot detect information security risks associated with an organization's operational environment in real time.
		_also known as information security continuous monitoring (ISCM)_
	Provides real-time insight into
		1. current state
		2. vulnerabilities
		3. effectiveness
Prioritizing Risks to Monitor
	Orgs consider the following factors when determining how to prioritize security risks:
		1. Compliance
			Depending on the business's industry, it may be required to monitor and analyze certain application and system acitivity i.e. remaining compliant with managing data about users credit cards
		2. Financial Impact
			How a system breach or shutdown can impact the financial performance of an organization i.e. ebay can not sell items if its down
		3. Reputational Impact
			How an incident would affect the business's reputation among customers i.e. banks with data breaches
		4. Likelihood of Attack
			While many types of security risk can occur, some are more likely than others i.e. Politically-associated businesses more likely to receive DOS attacks.
Logs 
	: record of an event occuring within a device or network
		_the contain entries, which represent specific events occurring on a device or network_
	Log types:
		1. Operating system logs
			: created on devices such as Linux and Windows systems. They record Security access and permission events
		2. Application logs
			: created by devices such as Apache and IIS servers. They record Application access events as well as Fraud events.
		3. Networking device logs
			: created on devices such as routers, switches, and DHCP/DNS servers. They record Administrative events and Network Security events
		4. Security device logs
			: created on devices such as IDS/IPS, firewalls, and endpoint devices. They record Endpoint and IDS signature events.
	Log Agggregation and Normalization
		Aggregation
			: the identification and collection of logs from multiple computing sources.
		Parsing
			: the process of converting the single string of data into structured data.
		Normalization
			: the process of standardizing fields in data from different sources and formats so it can be analyzed together.
	Log Correlation
		a single log entry may not seem suspicious, however, multiple entries paint a better picture of what is happening.
			_Imagine a single Login Failed entry; this doesn't tell us much however_
		Correlation alert
			: a notification that correlation rules have been et and an event was detected.
```
Mock-Rule Activity


Fifteen requests in fifteen seconds from the same IP 
address.

Batch requests for jpg files from outside the US.
 
```

#### Splunk Searches
Splunk
	: software tool that searches, analyzes, and monitors big data with an easy-to-use interface.
		_it can capture large amounts of data, which can be used to create visualizations, reports, and alerts._
	To flavor splunks base program with an organizations needs, you can add Splunk apps, add-ons, and suites.
		Apps
			have custom searches and features in their own interfaces.
		Add-ons
			provide additional functionality without their own interfaces.
		Suites
			collections of apps with a single focus, such as an industry or technology.
		_these apps, add-ons and suites are categorized by technology, vendor and industry._
Adding Data
	Splunk Indexer
		: receives incoming data and transforms teh incoming data into events. These events are added to repositories called indexes.
	Search Head
		: is Splunk's GUI that we use to conduct searches. It manages search requests to the indexer and provides the search results back to the user.
	Methods to Add Data
		1. Monitor
			: monitors logs from a system, device, or application that it has direct access to.
		2. Forward
			: Install a program called a forwarder on the system from which logs are collected.
		3. Upload
			: Manually upload logs directly into your Splunk repository.
Searching with Splunk
	: allows users to query upoaded and monitored data.
		types of searching
			1. Real-time search
				Returns a window of real-time data as it is happening and continues to update as the events occur.
			2. Relative search
				Returns data by date, date range, time, or time range. Results will not change even if more events occur.
			3. All time
				Returns all available data based on the search.
	SPL - Like SQL
		: Splunk processing language
			_searching with key-value pairs, wildcards, Boolean Expressions._
				Additionally regular Linux commands work with SPL as well such as,` | ; && head sort` etc.
	Search Fields
		: when files are uploaded and parsed, the data is separated into fields.