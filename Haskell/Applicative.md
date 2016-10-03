
# Applicative

- Applicative is a super class of Monad 

- Applicative allows for “effectful function application”, with <*> standing in for whitespace-between-arguments, and <$> standing in for $. For instance, mod 7 4 can be performed on list singletons (since lists are Applicative) as mod <$> [7] <*> [4].
ghci> mod <$> [7] <*> [4]

- minimal definition : pure, (<*>) 

## newtype ZipList a
Lists, but with an Applicative functor based on zipping, so that
f <$> ZipList xs1 <*> ... <*> ZipList xsn = ZipList (zipWithn f xs1 ... xsn)

### Examples 

## LiftA 

## LiftA2


## TODO:
- in doc: applicative admits more sharing than the monadic interface -> why is that ? 

 
