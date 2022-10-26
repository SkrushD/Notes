Complexities of Cloud Networks
	_Complex Architecture, Extensive managemnet, Different threats, Ensuring Availability_
Roles in Cloud Computing
	Coloud Security Analyst
		: must understand cloud architecture in order to test the security settings for a given environment.
	Cloud Architect
		: builds out a cloud envronment for an organization. They're expected to understand how to build in security from the ground up.
	DevSecOps
		: responsible for maintaining production and testing environments for an organization. They're expected to build and maintain secure systems at every step of the development process.
Cloud Service Model
	1. Ground-up Security
	2. Easy configuration
	3. Quick turnaround
	4. Personalized provisions from cloud providers
	5. High availability and fault tolerance
	6. Easy implementation
	7. Affordability
Cloud services
	Infrastructure as a Service (IaaS)
		: A service provider offers pay-as-you-go access to storage, networking, servers, and other computing resources in the cloud
	Platfrom as a Service (PaaS)
		: supplies the underlying infrastructure.
	Software as a Service (SaaS)
		: delivers software and applications through the internet.
	Data/Database as a Service (Daas/DBaas)
		: provides a company's data product to the user on demannd, regardless of geographic or organizational distance between provider and consumer.
_VM REGION SWITZERLAND NORTH_ // 50.39.164.224
Containers
	: a lot like a lightweight VM
		_They are smaller than Virtual Machines (megabutes rather than gigabytes) and require fewer CPU resources._
	Workload
		: a type of processing that you want a server to do - e.g. processing http requests, converting image fromats, sending emails, etc.
		![[Pasted image 20221020201619.png]]
Provisioners
	: tools that automatically configure VMs or containers for you. // software application used in IaC setups that makes automated configuration changes to computers.
Infrastructure as Code (IaC)
	: the idea that the configureations for all of the VMs, containers, and networks in your deployment should be defined in text files, which you can use with provisioners to automatically recreate machines and networks whenever necessary.
		_the primary benefit to IaC is that everyone can see exactly how the network is configured by reading text file. Theses can be easily version controlled with tools like git, time machine, OneDrive_
Continuous Integration/Continuous Deployment (CI/CD)
	: the concept of automatically updating machines on your network whenever your IaC files change.
		Continuous Integration (CI)
			: ensures that a new version of that machine is built immediately.
		Continuous Deployment (CD)
			: ensures that htis new version is automatically deployed to your live environment.
Secure Configuration vs. Secure Architecture
	Config
		: setting secure "rules" for individual machines and networks, as well as connecting these machines and networks in safge ways.
	Architecture
		: Can effectively mitigate the fallout of a breach, but the machines deployed according to that architecture must be securely configured in order for the architecture to fully deliver its security guarantess.
Horizontal vs. Vertical Scaling
	Horizontal
		: makes the system more resilient and prevents a single point of failure, as you can redirect requests to the other machines as needed.
	Vertical
		: scaling has a limit when you must add machines in to get more RAM and CPU resources.
```bash
sudo docker container start <container_id>
sudo docker container attach <container_id>
sudo docker exec -it <container> /bin/bash
```
#### Load Balancing
YAML
	: YAML Ain't Markup Language
Module resources for ansible
	https://docs.ansible.com/ansible/latest/collections/ansible/builtin/pip_module.html
	https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html
Load Balancer
	: provides the external IP address that the rest of the internet can access. It then recieves traffic that comes to the website and distributes it across multiple servers.
