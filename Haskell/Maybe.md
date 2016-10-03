
# Maybe 

## data Maybe a Source #
The Maybe type encapsulates an optional value. A value of type Maybe a either contains 
a value of type a (represented as Just a), or it is empty (represented as Nothing). 
Using Maybe is a good way to deal with errors or exceptional cases without resorting to drastic measures such as error.

The Maybe type is also a monad. It is a simple kind of error monad, where all errors are represented by Nothing. 
A richer error monad can be built using the Either type. 


## mapMaybe :: (a -> Maybe b) -> [a] -> [b]
The mapMaybe function is a version of map which can throw out elements.
In particular, the functional argument returns something of type Maybe b.
If this is Nothing, no element is added on to the result list. If it is Just b, then b is included in the result list.

## catMaybes :: [Maybe a] -> [a] Source #
The catMaybes function takes a list of Maybes and returns a list of all the Just values. 

## MaybeT 

