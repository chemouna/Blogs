
# Lists

## Coinductive 


### Difference list

## Comparing lists to sequences, vectors, arrays 
http://stackoverflow.com/questions/9611904/haskell-lists-arrays-vectors-sequences?rq=1

My feeling is that you should default to using Data.Sequence if a list is not appropriate. 
Use Data.Vector only if your usage pattern doesn't involve making many modifications,
or if you need extremely high performance within the ST/IO monads.

## Using lists in Haskell as control structures 
One insight I've heard is that lists are basically as much a control structure as a data structure in Haskell. 
And this makes sense: where you would use a C-style for loop in a different language, you would use a [1..] 
list in Haskell. Lists can also be used for fun things like backtracking. Thinking about them as control 
structures (sort of) really helped make sense of how they're used.


