
# Typeable 



## Related TODO 
- Read paper "Scrap your boilerplate" style of generic programming. 

### class Typeable a 
The class Typeable allows a concrete representation of a type to be calculated. 

### typeRep :: forall proxy a. Typeable a => proxy a -> TypeRep 
Takes a value of type a and returns a concrete representation of that type.


