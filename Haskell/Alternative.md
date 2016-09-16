
# Alternative

## class Applicative f => Alternative f 
A monoid on applicative functors. 

## (<|>) :: f a -> f a -> f a (infixl 3)
An associative binary operation

## some :: f a -> f [a]
One or more.

## many :: f a -> f [a]
Zero or more.

## Example instances
instance Alternative Perhaps where
  (<|>) = mplus
  empty = mzero

## instance Alternative [] where
    empty = []
    (<|>) = (++)
 
 
