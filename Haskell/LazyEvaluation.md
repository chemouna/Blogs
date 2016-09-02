
# Lazy Evaluation

## Prep

### Thunk 


## Lazy vs non-strict 
https://wiki.haskell.org/Lazy_vs._non-strict 

## Non-strict Semantics 


## Examples 


## Examples of working with conceptually infinite data structures 

## Examples of how non-strictnes allows writing your own control structures

ifThenElse :: Bool -> a -> a -> a
ifThenElse True  x _ = x
ifThenElse False _ y = y


## Advantage of writing non strict code 
the real and major advantage that non-strictness gives you over strict languages is you get to write cleaner and more composable code.
 In particular, you can separate production and consumption of data: don't know how many prime numbers you're going to need? Just make `primes` a list of all prime numbers, and then which ones actually get generated depends on how you use them in the rest of your code. By contrast, writing code in a strict language that constructs a data structure in response to demand usually will require first-class functions and/or a lot of manual hoop-jumping to make it all behave itself.


### Examples of non strict helping in writing composable code

any :: (a -> Bool) -> [a] -> Bool
any p = or . map p

## Stoping non-strictnes 

### seq 

### Strictness analysis 
foldl        :: (a -> b -> a) -> a -> [b] -> a
foldl f z0 xs0 = lgo z0 xs0
  where
    lgo z []     =  z
    lgo z (x:xs) = lgo (f z x) xs
lgo, instead of adding elements of the long list, creates a thunk for (f z x). z is stored within that thunk, and z is a thunk also, created during the previous call to lgo. The program creates the long chain of thunks. Stack is bloated when evaluating that chain.

With "-O" flag GHC performs strictness analysis, than it knows that lgo is strict in z argument, therefore thunks are not needed and are not created. 

### Explicit strictness 

####  Evaluating expressions strictly with $! 

A good example is the monadic return. If you find yourself writing

do …
   …
   return (fn x)
then consider instead writing

do …
   …
   return $! fn x
it is very rare to actually need laziness in the argument of return here.

    
   
--
https://wiki.haskell.org/Thunk
https://wiki.haskell.org/Tail_recursion
https://wiki.haskell.org/Seq
http://stackoverflow.com/questions/7140978/haskell-how-does-non-strict-and-lazy-differ

http://lambda-the-ultimate.org/node/2273
https://existentialtype.wordpress.com/2011/04/24/the-real-point-of-laziness/

