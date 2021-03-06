
# Protocols 
- Provide a high-performance, dynamic polymorphism construct as an alternative to interfaces
- specification only, no implementation

- Protocols are a mechanism for polymorphism.
- Protocols can be useful for defining an external boundary, such as an interface to a service. In this case it's useful to have polymorphism so we can substitute different services, or use mock services for testing.

- A protocol is a set of methods. The protocol has a name and an optional documentation string. Each
method has a name, one or more argument vectors, and an optional documentation string. That's it!
There are no implementations, no actual code.

- one important difference between protocols and interfaces: protocols have no inheritance.
You cannot create “subprotocols” like Java's subinterfaces.

- a datatype is not required to provide implementations for every method of its
protocols or interfaces. Methods lacking an implementation will throw an AbstractMethodError when
called on instances of that datatype.

## Extending protocols to already existing types
- to create a new protocol that operates on an existing datatype. and f.ex when you cannot modify the source code
of the defrecord. You can still extend the protocol to support that datatype, using the extend function:
```Clojure 
(extend DatatypeName
     SomeProtocol
        {:method-one (fn [x y] ...)
         :method-two existing-function}
     AnotherProtocol
        {...})
```
extend takes a datatype name followed by any number of protocol/method map pairs. A method
map is an ordinary map from method names, given as keywords, to their implementations. 

- Use extend-type when you want to implement several protocols for the same datatype;
use extend-protocol when you want to implement the same protocol for several datatypes.

## How protocols solve the expression problem

### Expression problem
basic problem of extensibility: our programs manipulate data types using operations.
As our programs evolve, we need to extend them with new data types and new operations.
And particularly, we want to be able to add new operations which work with the existing data types, 
and we want to add new data types which work with the existing operations.
And we want this to be true extension, i.e. we don't want to modify the existing program, 
we want to respect the existing abstractions, we want our extensions to be separate modules, 
in separate namespaces, separately compiled, separately deployed, separately type checked. 

- Multimethods already help solve the expression problem, but the main thing Protocols offer 
over Multimethods is Grouping: you can group multiple functions together and say 
"these 3 functions together form Protocol Foo". You cannot do that with Multimethods, 
they always stand on their own. 

- so why protocols when we have multimethods
any platform that you would like Clojure to run on (JVM, CLI, ECMAScript, Objective-C) has specialized high-performance support for dispatching solely on the type of the first argument. Clojure Multimethods OTOH dispatch on arbitrary properties of all arguments.
So, Protocols restrict you to dispatch only on the first argument and only on its type (or as a special case on nil).


## OO Style with protocols often hides the obvious simple thing 
```Clojure
(defprotocol Saving
  (save [this] "saves to mongodb")
  (collection-name [this] "must return a string representing the associated MongoDB collection"))

;Default implementation

(extend-type Object
  Saving
  ; the `save` method is common for all, so it is actually implemened here
  (save [this] (mc/insert (collection-name [this]) this))
  ; this method is custom to every other type
  (collection-name [this] "no_collection"))

;Particular implementations

(defrecord User
  [login password]
  Saving
  (collection-name [this] "users"))

(defrecord NewsItem
  [text date]
  Saving
  (collection-name [this] "news_items"))
```
  
instead of this where save fn won't work on User and NewsItem use : 

Make the save function a normal function:

```Clojure 
(defn save [obj] (mc/insert (collection-name obj) obj))
The protocol should only have collection-name

(defprotocol Saving
  (collection-name [this] "must return a string representing the associated MongoDB collection"))
````
And then each object that wants to be "saved" can implement this protocol.


