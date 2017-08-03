6-1

# Design patterns
- general solution to a common problem in a context

## Good design principles
- program to interfaces not to an implementation
- separate what chagnes from what does not

# Creational Design Patterns

## Problems with using new
- myClass = new MyClass()
	- might be invoked from many places
	- might be replaced by new MyBetterClass()
	- many subclasses might exist
		- want to be able to decide subclass at runtme
		- create correct subclass not old superclass

## Factory Solution
- Wrap code that creats objects inside method
	- Interface = createMyClass(params)
	- can change class in one place

## Example
public class PizzaStore {
	SimplePizzaFactory factory;

	public PizzaStore(SimplePizzaFactory factory){
		this.factory = factory
	}

	public Pizza orderPizza(String type){
		Pizza pizza;

		pizza = factory.createPizza(type);
		pizza.prepare();
		pizza.bake();
		pizza.cut();
		pizza.box();
		return pizza;
	}
}

## Advantages
- protects higher level of code from ugly lower level
- changes to class once
- dynamically create objects
- can override createMyClass in subclass

## Factory Pattern definition
- an interface for creating an object, but lets subclasses decide which class to instantiate

## Abstract Factory Pattern Advantages
- protects from creating compeonents from many frameworks taht cant communicate
- easy to decide at run time which framework

## Abstract Factory definition
- interface for creating families of related or dependent objects without specifying their concrete classes

## Builder design pattern advantage
- objects built according to actions, not code
- Builder Pattern encapsulates constrictuion of a product and aloows to be constrcuted as a sequence of steps

## Singleton
- ensure only one instance of object
- ensure global objects are not misused

- use factory to construct
- factory return if already constructed
- constructors private
- factory method in class

## Example
public class Singleton {
	private static Singleton uniqueInstance;

	private Singleton(){}

	public static Singleton getInstance() {
		if(uniqueInstance == null) {
			uniqueinstance = new Singleton();
		}
		return uniqueInstance;
	}
}

Definiition: Singleton pattern ensures class has onle one instance and provides global point of access

## Multiton Pattern
- generalisation of Singleton patern
- creates singleton associated with given key
- forces 1-1 mapping between keys and object

## Object Pool Design Pattern
- if have a lot of objects same type constantly created and deleted
- factory maintains list of constructed but releases objects
- creation involves returning object from pool if exists else create new object
- deletion involves adding deleted object to pool for later use

## Advantages
- Malloc/new are expensive operations
- can return elements in large array instead of creating new element indeply
- can maanage max num of objects of a type created
- can control num threads created

## Prototype
- collection of poto-typical instantiations of calss exist
- to create new instace, clone from prototype

## Advantage
- simplify construction of complex object

# Structure Design Patterns p39

## Adapter
- intent: convert interface of one class to make it compatible with another
- motivation: componenets often have imcompatible interfaces that cannot be used by a client but cannot be modified
- applicability
	- intermediate rep btw one componenet and antoher required
	- isolate client from changes in external componenets interface

- Two kinds of adapters
	- Object adapters (use composition)
	- Class adapters (use multiple inheritance)

- participants
	- client: calls adapter; completely isolated from adaptee
	- adapater: forwards calls between client and adaptee. may have to interact with multiple calsses
	- adaptee: compoenent being adapted

- might be no exact match between old and new interfaces
- clients have to watch for potential exceptions

## Bridge Design Pattern
- separates abstraction from implementation
- abstraction uses code to bridge differences
- replaces inheritance / implementation relationship wit composition relationship
- essential a wrapper hiding implementation

## Composite Design pattern
- do not distinguish between actions on leaf and actions on a subtree
	- eg move location of leaf / subtree
	- traverse all nodes in / under node
	- print tree

- Composite pattern allows to compose objects into tree structure to rep part whole hieracrchies
- lets client treet individual objects and composition of objects uniformly, irrespective of how the objects within the hierarchy differ

# End 6-1
