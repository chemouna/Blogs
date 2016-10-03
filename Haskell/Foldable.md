
# Foldable 

- A Foldable type is also a container. The class does not require Functor superclass 

- But many interesting Foldables are also Functors.
A foldable container is a container with the added property that its items can be 'folded' to a summary value.
In other words, it is a type which supports "foldr". Once you support foldr, of course, it can be turned into a list, by using toList = foldr (:) []. This means that all Foldables have a representation as a list, but the order of the items may or may not have any particular significance. 

- A particular kind of fold well-used by Haskell programmers is mapM_, which is a kind of fold over (>>), and Foldable provides this along with the related sequence_.

## foldmap

### examples of usage 

## Special folds

## Instances 
instance Foldable Maybe where
    foldr _ z Nothing = z
    foldr f z (Just x) = f x z

    foldl _ z Nothing = z
    foldl f z (Just x) = f z x -- notice diff here with foldr 
    
instance Foldable (Either a) where
    foldMap _ (Left _) = mempty
    foldMap f (Right y) = f y

    foldr _ z (Left _) = z
    foldr f z (Right y) = f y z

    length (Left _)  = 0
    length (Right _) = 1

    null             = isLeft
-- notice that for folding operations it skips left values 

    
## Qs 
- sometimes foldable instances implement foldMap & sometimes they dont -> is it just an optimision ? (see instances [] and Either)
