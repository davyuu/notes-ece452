# 6-4

## Observer Design Pattern
- also caleld implicit invocation
- observers also called listners
- permits other objects to
	- register and unregister
	- on one or more defined interface
- invokes all registered objects on interface when event occurs

## Advantage
- decouples observation of action from consequence of action
- new consequences can be added without impactive Observable code
- Observable code not cluttered with code conerting conseqeucens
- complexity replaced by simplicity

def: one-many dependency between objects so when one object changes state, all its depedendts are notified and updated

## Iterator Design Pattern
- problem
	- many ways of iterating over a list
- principle
	- encapsulate what varies
- supporst
	- get first
	- get next
	- seen all
- may be implemented by operator overloading
- may also be inplemented by language
	- eg. for(Object obj: objs) [Java 5]

## Example
interface Iterator{
	hasNext()
	next()
}

MenuIterator implements Iterator{
	hasNext();
	next()
}

## Problems
- adds potentially needless layer of completxity
- hard to know where it is
	- might break if structure modified while iterating
- reader might not understand what iterator does

Def:
- a way to access elements in aggregate object sequentially without exposing aggregate object's underlying rep
- places task of traversal on iterator object, not aggergate or user -> simplifies

## Composite Iterators
- have to remember where we are
- easy to directly traverse compostive tree structure
- harder to wrtie an iterator to do

## Mediator Design Pattern
- alot of things talking to a lot of things
- everytime new added, gets worse
- put a mediator (bus) between all things
- everyhting reports state chagne to mediator
- everyhing repsonds to request from mediator

## Advantage
- all communication between objects centralized
- objects dont nede to know about other objects
- reduce space
- easier to test
- easier to chagne

## Memento Design Pattern
- backup state for compositve object
- save state to new memento object
- to restore object/collection, pass saved state to restoreState method
- eg. saveInstanceState, restoreInstanceState

## Advantage
- compartmentalizes backup and restore
- can be implmeented using serialization
- can have many save check points
- can restore to any state
