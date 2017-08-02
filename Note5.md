# 4C Event Driven Architecture

## Pattern : Event Driven
- Context
	- event cause further events
- Problem
	- N^2 pairings of events with future events
- Forces
	- must perform events as and when they occur
	- want ot ignore relationship between events
	- asynch behaviour model
	- Parallelism

## Event Driven Logic
- logic is essentially erversed so detail is performed at highest levle
- decision to what details performed next is kept in static or dynamic table or message queue
- communication is via event generation
- useful when required to return from code

## Examples
- code called events occur (mouse)
- barber shop simulation
	- after creating initial future event, events introduce additional future events
	- servers chat with clients
	- AJAX
	- Windows OS
	- State machines

## Co-routines
- whole is bigger than parts but parts cannot easily be decompsed into sequential or layered operations
- separate parts must comminicate with each other without loosing stack state
- parts may run in separate threads. Uses tightly coupled messages, branching or language to produce the desired computation

## Co-routine example

	var q := new queue

	coroutine produce
		loop
			while q is not empty
				remove some itmes from q
				use the items
			yield to produce

## Table driven logic
- logic essentially governed by tables or data strucutres which are precomputed then compiled into code
- useful when wish to reduce run time complexity of code by precomputing behaviour in data inserted into code at compile time
- improves performance
- makes some challenges easy to solve

## Examples
- Yacc
	- tables generated which determine how parsing is to be performed
- Cribbage game
	- expacted value of cribbage hands precomputed
- Probability comulative functions
	- implemented by generating static tables
	- perhaps using Monte Carlo simulation
- Random forests

## Pros & Cons
- can produce clean solutions to difficult problems
- can be hard to understand since data generated can appear meaningless
- some programmers have difficulty making transition from conventional code to table driven code
- hard to debug

## Interpreter Style
- suitable for apps that language or machine for executing is not directly avavilable
- interpreter language says what to do
- interpreter implements how to do
- preserves high level sematics in code
- __Componenets__ include one state machine for execution engine and three memories
	- current state for execution engine
	- program being interpreted
	- current state of program being interpreted
- __Connectors__
	- procedure calls
	- direct memory access

## Exmaples
	- Programming Language compilers
		- Java, Dex
	- Rule Based Systems
		- Prolog
		- Coral
	- Scriping Langauges
		- Perl, Javascript

# START 4C

## Advantages
- simulation of non-implemented hardware, keeps cost of hardware affordable
- favilitates portability of apps or languages across variety of platforms
- behaviour of system defined by custom lagnauge or data structure
- separates how to do from how say what wnat to do

## Disadvantages
- Extra level of indreiction slows execution
- Java has option to compile code
	- JIT (Just In Time) compiler

## Message Oriented Arch
- Client/Server
- Peer to Peer
- Publicsher / Subscriber
- Message Bug
- AJAX (Synch/Asynch)
- Mobile code (javascript)

## Advantages
- distrubution of data is straightforward
- transparency of location
- mix and match heterogeneous platforms
- easy to add or upgrade servers
- functional client server interface
- simplifes distant levels of recursion
- one server can support multiple clients

## Disadvantages
- security
- no central register of names / services
	- hard to find out what is available
- Hard to asynch communicate wit server
	- eg cancel db query
- server cant initiate communication wit client
	- can provide callback
- overhead of packing and unpacking data
- potential restriction of data types and structures
	- eg int64, unicode
- uncertain server lifetime
- unpredictable server load

## Remote Procedure Calls (RPC)
- Interface Definition Language IDL
- RPCGEN
	- low level client proxy stub
		- layered arch
		- maps procedure call to message (marshalling)
		- maps message replies to precedure return value
	- High level server mainline
		- event drive arch
		- maps message to procedure calls
		- maps return value to reply message

## Componenet Object Model (COM)
- Factory
	- Dynamic Linked of objects at runtime
- IUnknown interface
	- QueryInterface
	- AddRef(void)
	- Release(void)
- All method invocation is via obtained interface
	- Implementation transparent

## DCOM
- COM
	- Dynamic loading and connection to an interface
		- class factory loads object with Iunknown interface
			- QueryInterface, AddRef, Release
- DCOM
	- Provides transparent remote COM interface
		- implemented using RPC strat
		- Microsoft reinvented own IDL

## Broker Arch (ORB)
- clients shouldnt know how to reach service
- offers additional dynamic services
	- adding, removing, exchanging, activating and locating components as needed
- Security may be enforeced by brokers
	- Who can talk to who and how
- broker may act as adaptor (Bridge)
- Load balancing

## Common Object Request Broker COBRA
- Goals
	- Language independence
	- OS independence
	- Interface mismatch translation (bridging)
	- Excapsulate and extend RPC paradigm
	- procide handles to multiple servers/services
	- security, communication of errors

## Reasons struggled
- IDL defined but no marshalling
	- not compatible across diff vendors
	- your COBRA cant talk to my COBRA
- Location transparency
	- cant treat all objects same way
- Designed by commitee (who disagreed)
	- failure to enforce common standards
	- Your COBRA not like my COBRA
- Poor implementations of standard

## Message Bus Arch
- Context
	- N^2 possible peer-peer connections
- Problem
	- Need to reduce cost of adding new connections
- Forces
	- want to reduce app dependencies
	- appls use diff interfaces
	- dont want every app to know all interfaces

## Message Bus solutions
- All peer communicates with bus
	- Bus agreed upon message schema
	- bus has common set of command messages
	- bus provides shared infrastrucutre
		- for managing peer-peer connections
		- for sending messages to recipients

# END 4D
