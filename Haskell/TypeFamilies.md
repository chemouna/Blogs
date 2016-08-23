
# Type Families 


## Haskell language extensions 

## Typelevel programming

## Examples 
type family Fst (p :: (k,l)) :: k where
  Fst '(a,b) = a
  

--
https://wiki.haskell.org/GHC/Type_families
http://research.microsoft.com/en-us/um/people/simonpj/papers/assoc-types/fun-with-type-funs/typefun.pdf
https://wiki.haskell.org/Simonpj/Talk:FunWithTypeFuns
http://www.cse.unsw.edu.au/~chak/papers/SCPD07.html
