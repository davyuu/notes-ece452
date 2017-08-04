# 6-3 Behavioral Design Patterns

## Template Design Pattern
- generic algoithm or task to perform
- reuseable code
- details differ

Def:
- skeleton of operation etiehr not specifying some steps or giving generic default behavour
- let subclasses redefine steps of algo without changin behaviour or intent

## Strategy Design Pattern
- mix and match behaviours
	- across instanaces of same calss
	- across diff subclasses
- behaviour might dynamically change
- hard to do wit template pattern

## Bad approaches
- use polymorphism to alter behaviour
	- code dup
- multiple inheritance

## Solution
- separate behaviour from object
	- define generic behaviour as interface
	- implement actual behaviour as subclass
- object has a behaviour
- original objects need behaviour

## Advantages
- assignment of behavior at run time
- easy increase types of behaviour wit no new class defs
- code need to know how to invoke behaviour not how behavior implmented
- behaviorus can be shared and reused
- behaiours can be dynamically changed
- can modify object without touching behaviour

Def:
- family of algos, encapsulates each one, and makes them interchangeable
- lets algo vary indep of clients that use it

## Command Design Pattern
- can view any behaviour as action
- unify diff behav interfaces
	- execute() undo()
- can combine sequence of behavs
	- array of pointer to successive actions
- define single behav from many

## Advantage
- create no-op if no action required
- can queue future commands
- can cache commands

## Disadvantage
- cant easily paramaterize action

Def: reqeuest as an object, allowed to paramtereize objects wit requests, queue or log request and supports repead and undoable ops

## State Design Pattern
- specialisation of strat pattern
- define complete list of actions
- reps state by calss haivng interface

## Advantage
- implemented within object
- pointer to object do not change
- behav in given state in single calss
- less risk of failing when im arbitrary state

Def
- allow object to alter behav when internal state changes
- object appear to change class
- object is neither deleted or recreated
- internally object can use singleton for state, virtual proxy or array of all prossible states

## Vistor Design Pattern
- task involves acting on a lot of node typesc in tree
- dont want to add for each node
- mihgt not be permitted to chagne calss
- create parallel abstract class
- each node type is visited
- actions to be performed are implemented by templating parallel abstract class

## Advantages
- separate what changes
- classes open for extension, closed for mod
- each class should have one responsibilty
	- each visitor designed for one purpose

Def: want to add capabilities to composite of objects and encapsulation within objects is not important, undesried or not possible

## Chain of Responsibility Design Pattern
- when want to give sequence of objects in turn a chance to handle a request
- each object in chain delegates to next object in chain if cant handle request
- eg. handler

## Advantage
- decourples a reqeust from all things that hadnle it
- allows chain to change at run time
- need a catch all if certain command is handled
- harder to debug

## Interpreter Design Pattern
- convert grammer into Abstract Syntax Tree
- have nodes in tree be instance of classes
- have interpref function in each node taht computes action to be perfermed
- eg. construct and execute plan

## Advantage
- easy to implement language from grammer
- can easily change/extend langauge
- can extend plan using composite design pattern

# End 6-3
