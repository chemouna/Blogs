
# Monads Transformers 

## EitherT

### newtype EitherT e m a 
EitherT is a version of ErrorT that does not require a spurious Error instance for the Left case.
This is necessary for both theoretical and practical reasons. For instance an apomorphism is the generalized 
anamorphism for this Monad, but it cannot be written with ErrorT.

### eitherT :: Monad m => (a -> m c) -> (b -> m c) -> EitherT a m b -> m c 
Given a pair of actions, one to perform in case of failure, and one to perform in case of success, run an EitherT and get back a monadic result.

### bimapEitherT :: Functor m => (e -> f) -> (a -> b) -> EitherT e m a -> EitherT f m b 
Map over both failure and success.

## ErrorT

### newtype ErrorT e m a :: * -> (* -> *) -> * -> *
The error monad transformer. It can be used to add error handling to other monads.
The ErrorT Monad structure is parameterized over two things:
    e - The error type.
    m - The inner monad.
The return function yields a successful computation, while >>= sequences two subcomputations, failing on the first error.


## ReaderT 

### newtype ReaderT r m a :: * -> (* -> *) -> * -> *
The reader monad transformer, which adds a read-only environment to the given monad.
The return function ignores the environment, while >>= passes the inherited environment to both subcomputations.

## Transformer type classes (i.e MonadXXX)
- they get rid of (most of) the need for explicitly using lift, giving a type-directed way to automatically determine the right number of calls to lift. 
   (for example for MonadWriter Simply writing put will be automatically translated into lift . put, lift . lift . put )
- they give you more flexibility to switch between different concrete monad stacks. For example, if you are writing a state-based algorithm, don't write
```haskell
foo :: State Int Char
foo = modify (*2) >> return 'x'
```
but rather
```haskell
foo :: MonadState Int m => m Char
foo = modify (*2) >> return 'x'
```
Now, if somewhere down the line you realize you need to introduce the possibility of failure, you might switch from State Int to MaybeT (State Int). The type 
of the first version of foo would need to be modified to reflect this change, but the second version of foo can still be used as-is.


## ErrorT 
- ExceptT 





