# 4A - architecture

## Arch conception
- graphics
	- pixel arrays
	- transformation matrices
	- widgets
- word processing
	- structured docuemnts
	- layouts
- process control
	- finite state machines
- income tax software
	- hypertext
	- spreadsheets
	- form templates

## Separation
- components
	- what does what
- communication
	- how parts communicate
- external software
	- what are interfaces, how to use
- user interfaces
	- what it looks like
- configurability, security etc

## Hardware architecture
- __RISC__ machines empasize small fast instruction set
- complex insturcutions are implemented using this simple fast set

- __Pipelined and multi-processor__ machines emphasize configuration of architectural pieces of hardware and overlapped flow of instruction and operation

- __micro-coded__ machines employ fast interpreter to translate from rich end user instruction set, to underlying instruction set. Can emulate many machine archectures

- Pentium incorporates all of the logic to perform dynamic memory allocations, page faults, within hardware

## Network architecture
- networked architectures achieved by abstracting design elements of network into nodes and connections
- Topology is most emphasized aspect
	- Star networks
	- Token ring networks
	- Ethernet
- Synchronous vs asynch
- Re-use of software: TCP/IP has TCP using IP protocol to make unreliable communications reliable.
- Layered communication protocol
- ISO/OSI Ethernet Reference Model is layered network arch

## Pattern: Pipes and Filters
- Context
	- Data can arrive in diff formats
- Problem
	- Need to provide series of ordered indep computations
- Forces
	- Explot existing programs / enforce data flow
	- partition into step wise processes
	- debug partitioned problem independently
	- support parallelism

- __Pipelines__ restricts topologies to linear sequences of filters
- __Batch Sequential__ a degenerate case of pipeline arch where each filter processes al input data before producing any output
- __Unix Shell Scripts__ prove notation of connecting Unix processes via pipes
	- cat file | grep Erroll | wc -l
- __Traditional Compilers__ compilation phases are pipelined, though phases are not always incremental. Phases in pipline include
	- lexical analysis + parsing + semantic analysis + code generation

### Pipe and Filter advantages
- easy to understnad overall input/output behavior as simple composition of behaviors of indiv filters
- supporst reuse, since any two filters can be hooked together, provided they agree on data
- easily maintained and enhanced, since new filters can be added to existing systems and old filters can be replaced
- permit certain kinds of specialized analysis, such as throughput and deadlock analysis
- naturally support concurrent execution

### Pipe and Filter disadvantages
- not good for handling interactive systems because of transformational character
- excessive parsing and unparsing leads to loss of performance and increased complexity in writing filters themselves

## Domain Specific Software Architecutres p34
- DSSA
	- refenrence architecture for the domain
	- libraries of tools for use within domain
	- configuration of target solution
- Game engines, 3D visualisation, parsers, shells
	- takes work out of the work
	- hard to say how it works

## Pattern: Layer
- Context
	- app has multiple layers of abstraction
- Problem
	- both high and low level issues tobe addressed
	- higher levels depend on lower levels
- Forces
	- Localize changes to single components
	- Separate concerns into diff componenets
	- reuseable logic easily accessible
	- components cohesive but loosely coupled

### OSI/Ethernet Layers
- Physical
	- wire, usb, bluetooh, RS232
- Data link
	- ATM, SDLC
- Network
	- IPv4, IPv6, AppleTalk
- Transport
	- UDP, TCP, DCCP
- Session
	- Named Pipe, SOCKETS, NetBios
- Presentation
	- MIME, XDR
- Application
	- Telnet, FTP, HTTP, NSF, SMTP

## Software Layer Architecture
- Simple
	- divide and conquer
- Clean
	- each layer is independent
- Potential problems
	- procedural implies tight binding of code
	- synchronous
	- lack of hierarchical flow
	- excapsulation denies acess to important details
	- interrupts and exceptions

## Layered style examples
- Layered Communication Protocols
	- each layer provides substrate for communication
	- lower levels define lower lvls of interactions
	- lowest level is hardware communication
- Operating System
	- Unix

## Overlaid Layered Architectures
- dynamically load code as needed
	- can instantiate many diff capacbilities at run time
- Free memory for reuse when no longer needed
- COBOL (initial, mainline, final)
- COM/OLE
	- refernece counting
- Garbage collection

## Pattern: Microkernel
- Context
	- core functionality must deploy on diff platform
- Problem
	- connections to hardware / OS subject to change
- Forces
	- Preserve abstraction rather than focus on detail
	- Encapsulate what may change soeasier to change
	- Share abstraction across all apps
	- Memory protection within OS as well as outisde

## Characteristics
- minimal capabiities in reduced Kernel
	- process creation / deletion / scheduling
	- foundational inter-process communication
	- secure memory managemnet
- Much implemented as app software
	- file system / network software / drivers
- offers choice, variety, extension, change
- adaptable (OS not set in stone)

## Layered style advantages
- design
	- based on increasing levles of abstraction
- enhancement
	- since changes to function of one layer affects at most two other layers
- reuse
	- diff implemnetaions of smae layer can be used interchangeably

## Layered style disadvantages
- not all systems are easily strcuted in layered fashion
- performance requirements may force coupling of high lvl functions to their lower-level implementations
- adding layers increas risk of error

## Object-Oriented Style
- metaphor
	- dynamic creation and deletion of objects
	- clear encapsulation of functionality
	- more restrictions on legit usage
	- inheritance
	- polymorphism
	- pure abstract interfaces

## Implicit Invocation
- Model/View/Controller
	- Data forms Model
	- Controller changes Model
	- Controller announces to requesting views change
- Publish/Subscriber
	- Publishes to topics
	- Subscribers listen to topics
- Observer design pattern
	- Underlying implementation

## Pattern: Model View Controller
- Context
	- System retrieve and display data in many formats
	- user interface may need new or altered views
- Problem
	- dont want core app to be concerned wit supporting User Interface behaviour
- Forces at work
	- user interface expected to evolve
	- paraleel tasks handled in diff ways
	- partition how things appear from how they change

- business logic does not sit between display and state
- changes to model broadcast to listener
- view responsible for presentation of model
	- diff parts of dashboard all listen for change
- Controller
	- responsible for handling input
	- maintains model consistency

## Model View Presenter
- Problem
	- hard to test/generate pseudo user interaction
- Solution
	- Separate logic for visual display
		- View (software that writes to screen)
		- Preseneter (sees interactions that occur on screen)
	- Impose strict interface between two
		- can test presenter without having screen
		- simply invoke interface from test software

## MVC vs MVP
- MVP can be a refinement of MVC
- Andorid MVP looks a lot more like 3 tier

## Why avoid 3 tier
- in a dashboard can hash many sub-views
	- new subview shuold be easy to dev
	- subview may not be visible all the time
- putting all view management in presenter makes presenter even fatter
- risks breaking presenter if have to change
- presenter doesnt care about views
	- subview listening osftware better encapsulated
	- subview can easily be deactivated/reactivated

## Implicit Invocation Style
- suitable for apps that involve lossely-coupled collection of components, each carries out operations and may in process enable other operations
- generalization of event driven code in which relevant state is included wit event and multiple processes can see event.
- instead of invoking procedure directly
	- A __component__ can accounce or broadcast one or more events
	- other componenets can register an interest in event by associating procedure wit event
	- when event is annouced, broadcast system (connector) invokes all procedures registered
- An event announcement implcitly causes invocation of procedures in other modules

## Implicit Inovation Invariants
- accouncers  of events dont know which components affects by events
- components cant make assumptions about processing as result of event
- component cannot make assumption on order of processing

## Implicit Invocation Specializations
- often connectors in implcit invocation system include traditional procedure call in addition to bindings between event announcements and procedure calls

## Implicit Invocation Examples
- used in programming environments to integrate tools
	- debugger stops at brekapoint and makes announcement
	- editor reponds to announcemente by scrolling to appropriate source line of program and highlights line
	- LSEdit
- used to enforce integrity constraints in database management systems (triggers)
- used in user interfaces to separate presentation of data (views) from applications that manage data
- used in user interfaces to allow correct mapping of function keys to logic
- used in forms to allow generic logic

## Implicit Invocation Advantages
- strong support for resue since any component can be introduced to system by registering for events
- eases system evolution since compoennets may be replaced by other components without affecting interfaces of other componetns in system
- easy to add new views
- eases system dev since only have to map events that occur to software that manages them and these events are predefined
- case tools hide complexity of managing flow of events
- asynch interface improves performance, response time
- parallelism

## disadvantages
- when component announces event
	- does not know what componenets will respond
	- cannot reply on order of responses
	- does not know when response are finished
- feedback involves generating additional events that are routes to callback routines
- no single defined flow of logic
- hard to consider all possible events that may occur and interactions
- hard to maintain and debug
- risk of communicating with Trojans

END 4B
