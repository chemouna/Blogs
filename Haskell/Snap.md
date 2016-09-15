
# Snap

## with :: SnapletLens v v' -> m b v' a -> m b v a 
Runs a child snaplet action in the current snaplet's context. If you think about snaplet lenses using a filesystem path metaphor, 
the lens supplied to this snaplet must be a relative path. In other words, the lens's base state must be the same as the current snaplet. 

## type SnapletLens s a = ALens' s (Snaplet a)

## data Snaplet s 
Snaplet's type parameter s here is user-defined and can be any Haskell type. 
A value of type Snaplet s countains a couple of things:
    - a value of type s, called the "user state".
    - some bookkeeping data the framework uses to plug things together, like the snaplet's configuration, 
      the snaplet's root directory on the filesystem, the snaplet's root URL, and so on. 

## MonadSnap m 
MonadSnap is a type class, analogous to MonadIO for IO, that makes it easy to wrap Snap inside monad transformers.

## newtype Snap a 
Snap is the Monad that user web handlers run in.

