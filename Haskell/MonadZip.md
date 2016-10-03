
# Monad Zip 
Monadic zipping (used for monad comprehensions)

- has two laws : Naturality and Information preservation 

## mzip :: m a -> m b -> m (a, b) 

## mzipWith :: (a -> b -> c) -> m a -> m b -> m c 

## munzip :: m (a, b) -> (m a, m b)

minimal definition needs mzip and mzipWith 

## Related functions

### liftM 

### const 

### liftM2 

### uncurry 

## Example 
### for Identity 
```haskell
instance MonadZip Identity where 
    mzipWith f (Identity x) (Identity y) = Identity (f x y)
    munzip Identity (a, b) = (Identity a, Identity b)
```

instance (MonadZip m) => MonadZip (ExceptT e m) where
    mzipWith f (ExceptT a) (ExceptT b) = ExceptT $ mzipWith (liftA2 f) a b

## TODO
 - Examples of monadic comprehensions 
