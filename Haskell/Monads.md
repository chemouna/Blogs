
# Monads

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
