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

