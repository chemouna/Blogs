
# Hashable 

### class Hashable a 
The class of types that can be converted to a hash value.
There are two ways to create new instances: by deriving instances automatically 
using GHC's generic programming support or by writing instances manually. 

```haskell
{-# LANGUAGE DeriveGeneric #-}

import GHC.Generics (Generic)
import Data.Hashable

data Foo a = Foo a String
             deriving (Eq, Generic)

instance Hashable a => Hashable (Foo a)

data Colour = Red | Green | Blue
              deriving Generic

instance Hashable Colour
```` 
 
### Data.HashSet 

#### member :: (Eq a, Hashable a) => a -> HashSet a -> Bool Source #
O(min(n,W)) Return True if the given value is present in this set, False otherwise.

#### fromList :: (Eq a, Hashable a) => [a] -> HashSet a Source #
O(n*min(W, n)) Construct a set from a list of elements.



