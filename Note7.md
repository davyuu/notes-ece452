# 4F

## SOA Guiding Principles
- Discovery (OASIS Reference Model)
	- electronic access to service docs
- Standard Service Contract (WSDL)
	- ability to establish porotcol to known server
- Service abstriaction

## SOA Implementation Goals
- Stateless (robust and scalable)
- Service reusability
	- generalize rather than sepcialize (usefulness)
	- loose service coupling(minimize deps)
	- composability (simplify resuabiliity)
- service autonomy
	- ability to change / ability to survive change

## Web services
- common standard to support SOA
	- focus on simplicity
- offers
	- find out about service (WSDL)
	- find instance of service (UDDI)
	- ask service to do seomthing (SOAP)
	- assisting standards
- XML based, with HTTP tranpsort layer
	- HTTP is firewall freindly

## REST vs SOA
- REST
	- simple client service interface
	- well understood established standard
	- transparency wrt client requests
	- must know URL end point
	- circumvents firewalls
	- if want, create
	- message paradigm
- SOA
	- more flexible
	- network of interaction components
	- access to rich set of WS - standards and features
	- reusable tool based architecture
	- supports distribution/replication of compennets
	- offers better securty, reliability, interoperability
	- complex evolving set of stanards
	- layered arch pardigm

# N-tier Architectures

## Action Domain Responder
- SQL -> Domain
- PHP -> Action
- HTML -> Responder
- HTML sends request via JS and PHP modifies HTML
- PHP communicates with SQL for data

## Multi teir Arch
- Level 1 : Client
	- HTTP reqeusts, fiels, SQL
- Level 2 : App server
	- receive requests
	- send replies
- Level 3 : DB server
	- communicates to DB
- DB
	- sql querys

## Three Tier
(Display <-> Process <-> State)
- Display and User interaction
	- eg client browser
		- thin (just display and front end interaction)
		- thick (a lot of front end computation)
- Processing
	- eg back end server
		- business logic
- State or Model
	- eg DB

## Multi Tier
- More than three theirs
	- routing between display and rpocess
	- distributed processing
	- distributed db layer

## LAyered vs Multi Teir
- layered arch
	- based on logical division
- Multi tier arch
	- leverages client server
	- based on physical division
	- more dependent on infrastructure
		- assume client has browser
		- assume server running apache etc

## Multi tier advantages
- code located where most efficiently run
- scalability
	- multiple clients can share server
	- can share db
- multi-trheading support
	- build in to browsers, apache, sql
- leverages exsting tech

## Disadvantages
- communcation overhead
- hadr to perform regression testing
- hard to debug
	- no single debugger
	- hard to intergret logs
- dep on remote resources
	- more points of possible failure

# Data Centric Arch

## Blackboard/Repo style
- suitable for apps which central issue is establishing, augmenting and amintaining complex cnetral body of global info
- info usually manipulated in wariety of ways, oftenl ong term persisitance required
- Components
	- central gobal data structure rep correct state of system
	- collection of indep components that operate on central data structure
- Connectors
	- procedure calls or direct memory acesses

## Blackbaord ARch
- no deterministic solution to problem
	- global state more
- a lot of exports
- have experts indep collaborate
	- team working on blackboard
	- typically without knowledge of each otehr
- any export can add to current knowledge
- each expert improve may help eothrs

## Mixture of experts
- examples
	- one is good at predicting normal load behaviour
		- bad at predicting peak load will occur
	- one is good at predicting high load behaviour
		- bad at predicting normal laods
	- weight predictions based on past accuracy
	- switch to which ever is currently best predictor

## Repository Style
- consistnecy of global data
	- policed, controled
- Database
	- SQL (relational db)
	- OMDG (object oreitned DB)
- Database is viewed as a server
	- all erquest performed by clients

## Repo style interaction
- ODBC / OLEDB / PhP connectors
- Triggers
	- Invoke PL/SQL
- External clients can be notifed of cahgens
	- implciti invocation
- SQL3 promises to be computattionaly complete

## Specializations
- Data strucutere in memory
	- realt teim
	- persistient but limited emory
	- ipod nano
- Data structure on disk
	- SQL
	- ipod classic
- Atomic transactions
- concurerent computitional data accesses

## Rule based / expert system
- repo is colelection of facts
	- new facts can be added and old facts deleted
	- can ask questions about facts
- Prolog
	- A.I. programming lanague

## Examples
- information systsmes
- programming environments
- graphical editors
- AI knownldge bases
- ipod
- Web (HTML data model)

## Advantages
- efficient way to store data
- sharing model is available as a schema
- centralized management
	- baskup
	- security
	- concurrency control
- Ability to easily extend data schema
- Reliable (no need to test)

## Disadvantages
- must address on data model
- difficult to distribute data
- data evolution is expensive
- scalability

# Distributed Repository

## Scalable Data Arch
- vertical scaling
	- buy faster cpu / more memory / larger disks
- horizontal scaling
	- buy more cheap servers
	- parallelism
	- routing

## Usage of Data
- online transaction processing (OLTP)
	- large volumes of INSERT/UPDATE/DELETE
	- simple SELECT statements
	- Goal: Storage/retreival: transactions per second
- online analytical processing (OLAP)
	- warehoused data (extract / tarnsform / load) (ETL)
	- complex operations on data
	- Goal: knowledge: response time per query

# END 4F
