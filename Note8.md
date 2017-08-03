# 4G

## NoSQL Systems
- Hadoop
	- Hbase
	- Hypertable
- MongoDB
- Redis
- Cassandra
- ElasticSearch
- CouchDB
- Accumulo
- OrientDB
- Neo4j

## Apache Hadoop (Distributed File System)
- Open source written in JAVA
- replication / load ballance / multiple servers
- replicates code execution at each server
	- Map (like SQL grouping)
		- Select, Transform, distribute to servers for reducing
	- Reduce
		- each server agregates/reduce its own data
		- results from one or more server merged

## Map / Reduce
- wruitten in Java
	- shipped and run on every data provider
- Map
	- compete from each data record a key
		- might be identity function
	- Sort dta by generatng key on each machine
- Reduce
	- compute summary value for each key
	- reduce to summary value acreoss machine

## Advantagse
- divide and conquer -> speeds data search
- highly parallel and scalable -> execution on local data
- robust reentrant -> node execution can be restarted
- replication -> can use first past of post response

## Disadvantage
- must be write Java Map and Reduce Logic from scratch
- have to wait for all parallel activity to complete
- not a db solution

## MongoDB (NoSQL)
- Distributed database system
- object oriented DB
	- each record encodes binary json
	- no meta schema
	- employed by java, javscript, php
- indexed searched supported
- replication / load balalnce/ sharding

## Advantages
- uses json
- uses map reduce like hadoop

## Disadvantages
- custom query language
- complexity of stored data structures
- no t as flexible
- no clear meta schema
- rsik of storing erroneous data

## Redis
- main memory storage
- pros
	- supports fast memory read and update
	- can stroe objects referenceed by name
	- can be distributed across many machines
- cons
	- db must fit in memory
	- recorvery by periodically backup

## Cassandra
- pros
	- data duplication across nodes
	- improves reliability and recorvery
	- row content can be distributed across nodes
	- parallel searching of rwo content
	- fast map/reduce capabilities
- cons
	- record read/wrtie grwos linearly with distribution
	- doesnt support relational joins

## ElasticSearch
- pros
	- can serach HTML text
	- supporst indexing of text
	- suports distribution of indices
- cons
	- lacks distributed transactions
	- if docs change, indices must be rebuilt

## CouchDB
- database are docuemtns
- pros
	- docs can change over tmie
	- docs may be offline
	- changes are timestamped
	- atomic, consisitent, isolation ,durability (ACID)
- cons
	- apps responsible for enforming ACID

## Accumulo
- built ontop of Hadoop
- pros
	- big table store
	- diff security levels for column info
	- map reduce functionality
- cons
	- uncertain future

## Other
- genetic programming
	- try to find random formulas that signal somethign intereseting
- gradient descent
	- construct cost formula for how close answer is to desired answer (0 == perfect)
	- find optimal paramter
- regression - fourier transform
	- predict future patterns

## Methodology
- filter
	- clean up
- train
	- optimise logic on given set of data
- validate
- test
	- see if results are good
- use

## basic problem
- distributed system can become partitioned
	- partitioned subsystems cant communicate
	- issue is about latency
- consistency -> read matches most recent write
- availablitity -> can read from avavilble node
- cant know if partition has latest write
	- dont worry about talking to other partition
		- availability
	- either error or wait for other partiition to repond
		- consistency

## basic proof
- consider two partitioned nodes
	- write new record to one node
	- read this same record from other node
- if partitioned other node cant know lastest version of record to be read
	- either return version earlier tha ncurrnnt
	- wait at node to obtain latest version
	- insist both nodes must remain up all the time

# Process Control Architecture

## Process-control style
- suitable for apps whose purpose is to maintain properties of output of the process given reference vaules
- components
	- process definition includes mechanism for manipulating proces variables
	- control algo for deciding hwo to manipulate process variables
- Connectors are data flow relations
	- process variables
		- input variables that measure input to process
		- maripulated variable value can be cahgned by contorller
		- controlled variable value tthe system is intended to contorl
	- set point is the desried values for a contorlled variable
	- sensor to obtain values fo process variables pertinent to contorll

## Last of feedback problems
- no regulation of software bejaviour
- fixed bejaviour in response to chagne request
- distrubancse in bejavior not considered
- no check that acutal close to desried

## FEedback benefits
- self checking
- self improving
- eg
	- prediction
	- monitor accuracy of prediction
	- employ mixture of experts

## Proces controll exmaple
- real time system software to control
	- automobile antilock brakes
	- nuclear power plants
	- automobile cruise control

# Rule based architecture

## Iterative enhacement style
- want appearance of intelligent behaviour
- impossible to quanitfy what intelligence is
- start by writing dumb program
- add logic to make less dumb
- terminate when cant improve resulting logic

## Pros/cons
- allows concurernt design and dev
- can lead to surprising itelligence
- displays same characteristics as human intelligence -> unpredictable and not always right
- hard to predict sucess of exercise willbe

## Example
- bridge program
	- deal hand
	- enforce basic rules to play
	- add rules for how to play well
	- consider making finesses
	- logic identifies least worse card to play based on rules drawn from observations
	- release code when changes do not improve play

## Cribbage
- table driven discarcd login
	- for every pair of carded can be discarded and every cut
	- what is avg value of resulting harnd
	- avg value of box
	- max score

## Pegging
- for each card might play
- every possible card played in response
- play card to max score minus their score

# Model Driven Architectures

## examples
RPCgen / DCOM
- marshalling/unmarshalling interfaces
- Object Management Group (OMG)
	- given UML produce code
- Liqui|>
	- given quantum machine expressed in F#
	- generate code to simulate machine

# Other architecures

## C2
- arch built using compnetns and connectors
	- have top and bottom
	- top and bottom of compoenent has =< 1 connector
	- opposite ends of components/connector connect
	- other end of connecter connects to anyhting
	- all communication via messages
- requests travel up
- notifications travel down
- connectors responsible for
	- routing, broadcasting, message filtering
		- components register to receive notifications
		- msesages cna be proiotized
		- requests can be ignored
	- domain translation when necessary

## Objectives
- substrate indep
	- above ahieved by domain tarnslation
	- below achieved by inforamtion hiding
	- fosters substitutability/reuseability
- message based arch
	- permits parallelism, distribution, sacling
- diff components share no satete
- components are compartmentalized

## Aspect oritened arch
- cross cutting concerns
	- runtime assetions
	- tracing
	- profiling (performance issues)
	- error handling
	- testing
	- debugging
	- reliability
	- encryption mechanism

## implmentation
- extend lagnuage to specify aspects
	- no nede to embed code
	- can be implmenetatl statically during compilation
	- dynamic at runtime via request
- consider debugging C++
	- -g option statically introduces symtol tables
	- break command in GDB dynamiically alters code
	- watch command dynamiicaly wathces variable

# END 4G
