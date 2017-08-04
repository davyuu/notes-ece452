# 6-2

## Decorator Design Pattern
- Objective: want tot add attributes to an object
- num of atributes to add is unspecified
- should be able to easily add newly defined attributes to code with minimal change

- Reify -> convert into or regard as a concrete thing, each attribute making fully dledged object
- treat object and attributes as compositie object using composite design pattern
- extend functionality for objec tot operate on tree instead of node

## Advantages
- provides alternative to sub classing
- decorators change behaviour of component by adding functionality before, after or in place of method calls to child/children
- component can have any num of decorators
- decorators can add state to decoratee
- presence of decorators are typically transparent

Def
- a decorator attaches additional  responsibilities to an object dynamically
- decorator provides flexible alternative to sub classing for extending functionality

Caution: decorators can resut in many small objects in design and overuse can be complicated and inefficient

## Facade
- intent: provide unified, higher level, interface to a whole module making esier to use
- motivation: composing classes into subsystems reduces complexity. Using a Facade minimizes communication dependencies between subsystems.
- Applicability
	- want simple interface to a complex subsystem
	- many dependencies between clients and subsystem
	- want to layer subsystem

## Facade Design Pattern
- simplified interface
- does not exclude direct access to components of subsystem
- makes life easier for clients, have set of actions alwyas perform
- permits clients to know nothing about real subsystem

- participants
	- facade
	- subsystem classes
- collaboration
	- clients interact subsystem via facade
- consequences
	- sheilds clients from sybsystem comps
	- promotes weak coupling

## Adapter vs Facade
- main diff is intent
	- adapater: change an interface so matches clients needs
	- facade: provide client with simplified interface to subsystem

## Flyweight Design pattern
- lots of same objects but each with small amount of differing state
- dont want allocate space for all
- Extract what changes from what does not
- client object contains changing state
- invokes methods of flyweight providing state as parameter
- flyweight is stateless permitting sharing/reuse
- state can be stored in array, on disk or in db

## Front controller design pattern
- route code through common front end controller which handles task that must be performed on every access
	- eg security
	- unmarshalling web parameters
	- deciding scripts to be invoked
	- logging of requests received
	- load balalncing

## advantages
- avoids repeat code
- centralize routing
- simplifies nagivation
- spawn trhead for bulk work
- preserve javascript state on client

## Proxy design pattern
- provides surrogate or placeholder for another object to control access
- uses
	- remote: transparent communcaiton w object
	- virtual: creats real object only when needed
	- protection: refuse access unless needed

# End 6-2
