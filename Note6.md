# 4E

## Enterprice Service Bus
- Customized company message broker
	- Arriving SOA requests
		- using TCP/IP, SOAP, JMS, FTP protocol
	- Wrapped by ESB layer
	- provide web based inputs to organization legacy business process orchestration tech
- buzz word

## Asynchronous Messaging
- Peer-to-Peer
	- Peers talk to other peers one at a time
	- expect synch or asynch response
	- asynch hanlded by callback (new thread)
- public-subscribe
	- provider communicates wit Topics
	- subscrier dynamically subscribe to Topics
		- implit invocation / observer design pattern
	- Topics may be organized hierarchically
	- Topics forward messages to subtopics/servers

## Application Servers
- Client/Browser Side
	- HTML, Javscript, Ajax
- Web Tier (Apache, Tomcat)
	- Receives requests
	- invokes web server-hosted componenets
		- JSP (Java Server Pages), ASP, PHP
			- invokes business componenet tier
				- JavaBeans, .NET, COBRA
			- invokes Enterprice Information Systems Tier
				- MySQL, Backend Mainframe

## Enterprise JavaBeans (EJB)
- Top layer is Java Vitual Machine
- hosts components
	- Session Beans (Synchronous)
		- Stateless (consecutive requests to any instance)
		- Stateful (caller binds to one specific instance)
	- Message driven Beans (Asynch)
		- No explicit reply

## Examples
- Software downloaded before execution
- Java Applets download jar when used
- Javascirpt embedded in transmitted HTML
- Viruses (Liquid, Hadoop)
- Hadoop
	- Move code to where needed
	- Move code to become local to data
	- Not massive amounts of data to remove code

## Message Oriented Choices
- Delivery: best effort, persistient, transactional
	- UDP, TCP/IP, Message Queues
- Blocking, Nonblocking, asynchronous sockets
	- blocking good for simple connection (layered)
	- nonblocking more flexible since no waiting (layered)
		- cancel attempt to connect, switch to diff web page
	- Asynch efficient/elegant/scales well (event driven)
		- keeps track of connection state - not every connection
- Interface: Sockets, RPC, HTTP, SOA, AJAX, Stream

## Representation State Transer (ReST)
- URL + Parameters returns Document
	- Leverages Standard Web Tech
		- GET/POST/PUT Built on top of Email
	- Stateless
		- Except for Cookies and/or Session
	- Server indicates cacheability
- AJAX
	- Small document transfers while viewing

## RESTful Web Services
- Web services only uses HTTP as transport layer (to fool firewalls)
- Represetnational State Transfer (REST)
	- Resources identified by URL
	- Message passing mechanism
		- GET
		- POST
		- PUT
		- DELETE

## ReST Constarints
- Client/Server -> Parallel evolution (adapable)
- Stateless -> Scalabale
- Cacheable -> efficient
- Layered -> transparency
- Mobile Apps -> Powerful
- Uniform Interface -> Usable

p12
## Uniform Interface
- Identification of all universal resources
	- naming of things (conceptual separation)
	- URL /URI
- Maniipulation of resources
	- client read, change or delete a named resource
- Self descriptive emssages
	- nothing assumed by server
- Hypermedia
- Circumvents Firewalls using HTTP ports

- Get -> Retreive Parameterized URL
	- Visible -> bad for sensitive data
	- can be changed -> bad for security
	- can be cached, bookmarked in history
	- length restrictions on parametsr
- POST -> Send data to server in email
	- hidden so better for sensitive data
	- cant be cached, bookmarked or remembered
	- No length restrictions

## Semantic Web
- effort to give XML entities real sematics
	- namespace disamiguates entity names
	- XML Schema types the content of an entity
	- RDF describes semantic information as graph
		- Resource Description Framework
	- RDFS uses RDF to describe objects
	- OWL defines ontologial relationships
	- SPARQL permits queries about semantics

## Service oriented Arch (Web Servces)
- Fix interoperability problems
	- vendors agree on standards for application integration
	- provies interoperability across hardware, software, companies and infrasturcuters
- provies internet-scale distributed systems
	- vendosr agree on standards for distributed computing

## SOA design consideration
- Boundaries are explcit
	- crossing process, machine, trust expensive
- Services are autonomous
	- can change code, language, machine transparently
	- must preserve backwards compatitibility
- Services simply receive messages and reply
	- no objects, no interfaces, inheritance
- Client/server polcy part of connecting design
	- things like message reliability, security and encodings

# END 4E
