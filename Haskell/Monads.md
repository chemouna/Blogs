
# Monads

-  a pure function can always be fmap’d into a monadic result  

## class Monad m => MonadIO m where
Monads in which IO computations may be embedded. Any monad built by applying a sequence of 
monad transformers to the IO monad will be an instance of this class.
Instances should satisfy the following laws, which state that liftIO is a transformer of monads:
liftIO . return = return
liftIO (m >>= f) = liftIO m >>= (liftIO . f) 

## liftIO :: IO a -> m a
Lift a computation from the IO monad.

## data IO a :: * -> * -- in System.IO
A value of type IO a is a computation which, when performed, does some I/O before returning a value of type a. 

## Reader
Computations which read values from a shared environment.
The Reader monad (also called the Environment monad). Represents a computation, which can read values from a shared environment,
pass values from function to function, and execute sub-computations in a modified environment. Using Reader monad for such 
computations is often clearer and easier than using the State monad.

### ask :: m (EnvType m) 
Retrieves the monad environment.

## fail :: String -> m a
Fail with a message. This operation is not part of the mathematical definition of a monad, but is invoked on pattern-match failure in a do expression. 

## Monadic Naming convention 
- A postfix 'M' always stands for a function in the Kleisli category: The monad type constructor m is added to function results (modulo currying) and nowhere else. So, for example,
 filter  ::              (a ->   Bool) -> [a] ->   [a]
 filterM :: (Monad m) => (a -> m Bool) -> [a] -> m [a]

- A postfix '_' changes the result type from (m a) to (m ()). Thus, for example:
 sequence  :: Monad m => [m a] -> m [a]
 sequence_ :: Monad m => [m a] -> m ()

- A prefix 'm' generalizes an existing function to a monadic form. Thus, for example:
 sum  :: Num a       => [a]   -> a
 msum :: MonadPlus m => [m a] -> m a

## join 
### Examples of it's usefulness 

## MonadPlus

### class (Alternative m, Monad m) => MonadPlus m where
Monads that also support choice and failure.

## newtype WrappedArrow a b c 

### Examples usage 

## Identiy Monad
a monad that does not embody any computational strategy. It simply applies the bound function to its input without any modification.
Computationally, there is no reason to use it instead of the much simpler act of simply applying functions to their arguments.
Any monad transformer applied to the Identity monad yields a non-transformer version of that monad. 




 
