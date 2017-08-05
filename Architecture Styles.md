Architecture vs Design
- Arch
	- higher level of abstraction
	- how modules talk to each other
- Design
	- lower level of abstraction
		- more concrete solutions
	- how is particular module structured
- All design is arch

Architecture Styles

Components
- Elements that encapsulates processing and data and architectural level
Connectors
- architectural entity tasked with effecting and regularting interactions between components
Configurations
- Bind components and connectors together in specific way
Topologies
- Minimize coupling between components
- Maximize cohesion within each component

Style: Main program & subroutine
- Decomposition of functional elements
- Components
	- main program and subroutines
- Connections
	- Function / procedure aclls
- Data elements
	- Values passed in / out of subroutines
- Topology
	- Directed graph between subroutines and main program
