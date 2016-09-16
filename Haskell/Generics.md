
# Generics


## data (f :+: g) p (infixr 5) -- its a data type 
Sums: encode choice between constructors
Constructors
L1 (f p)	 
R1 (g p)	 

## data (f :*: g) p (infixr 6)
Products: encode multiple arguments to constructors 

## type Rec0 = K1 R 
Type synonym for encoding recursion (of kind *) 



## TODO 
-> what are some other constructs in haskell and idris that are based on Isomosphisms ? 
-> what other constructs in haskell generate code (by the compiler) ? 
-> is there any link between Generics in Haskell and lisp macros ? 
-> are there some macros examples that encode more higher level recursion constructs ? 
   
