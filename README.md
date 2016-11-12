# iOS Interview Questions

Here are some iOS interview topics/questions I've encountered personally or found through google/stackoverflow/Apple Documentation. I'll keep adding and removing things as I dive into new and important concepts.

Enjoy!


## Protocols

Protocol are an interface that a class can conform to, "forcing" that class to implement the listed methods. A class can be test for conformance to a protocol at COMPILE time and also at run-times using conformsToProtocol NSObject method.

Protocols declare methods that can be implemented by any class. These classes are said to conform to the protocol. Protocols can be formal or informal:
    *Formal Protocols are declared with @protocol blocks
    *Informal Protocols can be implemented in terms of @protocol block with all the methods being @optional or with a category of NSObject.

##Delegation

A delegation is a more abstract term that refers to Delegation Design Pattern. Using this design pattern, a class would have specific operations that it delegates out(perhaps optionally). Doing so, creates an alternative to subclassing, by allowing specific tasks to be handled in an applicatory manner, which would be implemented by a delegate.

This pattern is typically implemented by the means of a protocol or put it in another way, a delegate is typically an anonymous object that conforms to a protocol.

#Protocol and Delegation

Protocol and delegation are related terms because you often see a Protocol created for the purpose of Delegation. If I wanted to allow a delegate to sort something, I'd create a Protocol with a required method "sortstuff" & I would require the delegate to implement it. That way, within the class that supports calling to a delegate, I can accept a pointer to a delegate & then say "if that delegate conforms to "sortstuff" Protocol, I know it implements sortStuff, so it's safe to call that method instead of doing my built-in behavior.

Delegation is a design pattern by which an object is given an opportunity to react to changes in another object or influence its behavior. The basic idea is to get the two objects to coordinate to solve a problem while minimizing coupling between these two objects & avoiding subclassing. Subclassing crates a tight coupling between the subclass & its superclass where as delegation creates a much looser relationship based on anonymous objects.

Delegation is awidespread design pattern through Apple's frameworks
Delegation allows customization of an objects behavior & to be notified about certain events

Delegation is very flexible & straightforward communication pattern if you need to communicate between two specific objects that are in relative proximity to teach other in terms of their place in your app architecture.

Apple uses delegation pervasively. More often, you see Apple move more a lot of their API to blocks, which are similar to callbacks in other languages.

The Delegation Design Pattern helps maintain MVC which is a design pattern in itself.
It helps separate models from controller and it is very useful when you want to pass info between objects

NOTE:Delegates should be weak/assign properties, otherwise, you'll enter a retain cycle, where neither object can be deallocated.

##What are some different iOS Design/Communication Patterns?

You should be able to comfortably discuss at the minimum, all these patterns listed:
*KVO(Key-Value Observation)
*Notifications(Singleton)
*Delegation
*Blocks
*Target-Action

Things to think about:
Why or would I use one pattern over another?  (this will be in another update)f
What are the advantages and disadvantage of each? (this will be in another update)



## What is MVC?

The Model-View-Controller (MVC) design pattern assigns objects in an application one of three roles: model, view, or controller. The pattern defines not only the roles objects play in the application, it defines the way objects communicate with each other. Each of the three types of objects is separated from the others by abstract boundaries and communicates with objects of the other types across those boundaries. The collection of objects of a certain MVC type in an application is sometimes referred to as a layer

## What are “strong” and “weak” references? Why are they important and how can they be used to help control memory management & avoid memory leaks?

By default, any variable that points to another object does so with what is referred as a “strong” reference. A retain cycle occurs when two more objects have reciprocal strong references. These objects will never be destroyed by ARC. Even if every other object in the app releases ownership of these objects, these objects will continue to exist by virtue of those mutual strong references, therefore, resulting in a memory leak.

To avoid this type of memory leak one way is to employ weak references. Declaring one of two references as week will break the retain cycle.

The parent should maintain a strong reference to the child & the child should have weak reference of the parent.

## What are the main differences between xibs and storyboard?

Before storyboards existed, there were only xibs. Xib files are Layout files based in XML.
Simply put, storyboard is made of xib boards and provides a clear "story" or distinct path for xib files.

Apple encourages storyboard, but there are still companies that don't use them, so you should be comfortable with:
*using storyboard
*xibs only
*programmatic UI

Side note: When making your own framework, only xibs can be used. This is because, you can put xibs in the bundle, but not storyboards.

## Describe managed object context(represented by an instance of NSManagedObjectContext)

Managed Object Context is basically a temporary “scratch pad” in an application for a presumably related collection of objects. These objects collectively represent an internally consistent view of one of more persistent stores. A single managed object instance exists in ONLY ONE context, but multiple copies of an object can exist in different context.

We can think of managed object contexts as an intelligent scratch pad. When you fetch objects from a persistent store, you bring temp copies onto the scratch pad where they form an object graph or a collection of object graphs. You can then modify those objects however you like. Unless you save those changes, though, the persistent store remains unchanged.



## What design patterns do you know and use on iOS?

At the minimum, explain what is  MVVM. This is the holy grail that saves iOS developers from Massive View Controllers. A developer should be able to explain you what MVVM is, why it’s better than MVC, and should be able to tell you what other patterns he/she uses along with MVVM (Inversion of Control, Dependency Injection, etc.). 

One red flag, is you say you only MVC because Apple said so and you never tried MVVM.


## What are singletons? When would you use one and when would you not(pros/cons)?

The Singleton pattern is a design pattern that restricts the instantiation of a class to one object. This is useful when exactly one object is needed to coordinate actions across the system. The concept is sometimes generalized to systems that operate more efficiently when only one object exists, or that restrict the instantiation to a certain number of objects. The term comes from the mathematical concept of a singleton.

There are some who are critical of the singleton pattern and consider it to be an anti-pattern in that it is frequently used in scenarios where it is not beneficial, introduces unnecessary restrictions in situations where a sole instance of a class is not actually required, and introduces global state into an application.

Singletons should be avoided and used only for objects that need to be shared throughout your application for same reason. It should be used carefully, instantiated lazily, if it’s possible, and passed into other objects as a dependency using Inversion of Control and Dependency Injection principles.
    
Singletons prevent decoupling by creating inflexible dependencies between classes, thus severely limiting code reuse in larger projects. Using singletons goes against the idea of abstract interfaces, and has negative impact on your ability to write tests.




