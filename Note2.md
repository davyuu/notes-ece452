# Architecture
- Architecture is:
	- All about communication
	- What parts are there
	- How do the parts fit together
- Arch is not:
	- About development
	- About algorithms
	- About data structures

## Software Architecture
- All arch is design but not all design is arch
- arch focuses on those aspects of system that would be difficult to change once build
- captures
	- Structure
	- Communication
	- Nonfunctional requirements

## Attacks on complexity
- high level languages
- development tools & environments
- component based reuse
- development strategies
	- incremental, evolutionary, spiral models
- emphasis on design
	- design centric approach taken from outset

## Architectural approaches
- creative
	- engaging
	- potentially unnecessary
	- dangerous
- methodical
	- efficient when domain is familiar
	- predictable outcome
	- not always successful

## Design process
1. Feasibility stage
	- identify set of feasible concepts
2. Preliminary design stage
	- select and develop best concept
3. Detailed design stage
	- develop engineering descriptions of concept
4. Planning stage
	- evaluate / alter concept to fit requirements

## Abstraction
- Definition
	- a concept or idea not associated with specific instance
- Top down
	- Specify down to details from concepts
- Bottom up
	- Generalize up to concepts from details
- Reifications
	- The conversion of a concept to a thing

## Components
- elements that encapsulate processing and data at an architectural level
- def: architectural entity that
	- encapsulates a subset of functionality
	- restricts access via explicit interface
	- has explicit envionmental dependencies

## Connectors
- def:
	- an architectural entity tasked with effecting and regulating interactions between componenets
- connectors are often more challenging than components in large systems
- often consists of method calls

## Configurations
- bind components and connectors together in a specific way
- def:
	- architectural configuration or topology
	- is a set of specific associations between the components and the connectors of the systems arch
- differentiates a bag of components and connectors from implementable system

## Topological goals
- minimize coupling between components
	- less components know about each other, the better
- maximize cohesion within each component
	- components should be responsible for a logical service
	- extraneous functionality should not be present

## Cohesion
- relationship of code within routine
- how string are the relationships
- routines should do a single thing
- Goal: Create routines with internal integrity
- 50% of highly cohesive routines fault free
- 18% of low cohesion reoutines fault free

## Coupling
- usefulness and effectiveness of connection between routines
- compliment of cohesion
- want small, direct, meaningful, visible, flexible relations
- wnat loose coupling
- routines hsould not depend on caller
- should be detached and self contained
- should be sufficiently general
- routines should not share global data
- routines should fulfill a purpose rather than be viewed as performing specific actions

## Levels of coupling
- simple-data coupling (simplest/best)
	- only non-structured data shared
	- all data passed as parameters/return result
- strong data-structure coupling (ok)
	- structured data passed between routines
	- all data passed as parameters/return result
	- most/all of strcture passed relevant
- weak data-structure coupling (weak)
	- little inforamtion in strctures passed relevant
- control coupling (poor)
	- parameters tell called routine how to behave
	- caller understands internal workings of callee
- global data coupled (horrible)
	- two routines operate on same global data
	- connection neither intimate nor visible
- pathologically coupled (disaster)
	- one routine directly uses another routines code
	- one routine directly alters another routines data
