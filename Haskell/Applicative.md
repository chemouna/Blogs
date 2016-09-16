
# Applicative

- Applicative is a super class of Monad 

## newtype ZipList a
Lists, but with an Applicative functor based on zipping, so that
f <$> ZipList xs1 <*> ... <*> ZipList xsn = ZipList (zipWithn f xs1 ... xsn)

### Examples 

## TODO:
- in doc: applicative admits more sharing than the monadic interface -> why is that ? 

 
