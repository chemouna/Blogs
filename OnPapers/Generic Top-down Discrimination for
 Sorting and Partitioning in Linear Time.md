
# Generic Top-down Discrimination for Sorting and Partitioning in Linear Time


## Get results out of it 

### Read more to learn more about this kind of stuff 
    and maybe get an innovative idea 
- Paper Generalizing Generalized Tries 


### What i understand so far 
- it seems to be a generalisation of radix sort 
- its an example of an elegant use of GADTs 

- Henglein's core idea is that if you can start with some basic Groups on integers—we can write very fast Group Int32 implementations via radix sort—and then use combinators to extend them over all types then you will have generalized radix sort to algebraic data types. 


### TODO 
- implement some exples of eq relations like congruent, cong mod n, same abs value
- after reimplementing it in Idris, Try in clojure/java
- implement radix sort in haskell
- read on algo asymptotics 
- to get used to radix sort solve the problems here https://www.hackerearth.com/practice/algorithms/sorting/radix-sort/tutorial/ 
- read sections on radix sort in both knuth & intro to algo books 
- look at impl of radix sort in clj from clojure-algorithms sort.clj
- Read paper FP A pointless Derivation of radix sort 

### Later 
- burstsort and application to caching 


## Sources
- http://stackoverflow.com/questions/32059754/are-there-useful-applications-for-the-divisible-type-class 
- https://www.reddit.com/r/haskell/comments/3brce1/why_does_sort_in_datadiscrimination_claim_to_be_on/ 
