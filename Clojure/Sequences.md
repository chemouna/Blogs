
# Sequences 

- Seqs differ from iterators in that they are persistent and immutable, not stateful cursors into a collection. 
- Seqs useful for much more than foreach - functions can consume and produce seqs, they are thread safe, they can share structure etc. 

- Rich Hickey says, "A seq is like a logical cursor," and that, unlike iterators, they are immutable. 

### Seq 
- Copies of immutable objects are free. That's right, free. Because you don't need to copy at all. The same allocated object in memory can simply be reused wholesale, because it's guaranteed to always be the same as when it was "copied."
So a function like seq never has to actually copy anything. It just operates on whatever is passed, directly, and returns a (possibly lazy) sequence that provides an abstract interface to whatever you called seq on.
And so, seq is always O(1).

- what's so powerful about Clojure is that all the core data-types implement the same sequence abstraction: clojure.lang.ISeq.
This means that functions like "first", "concat", "cons", "map", "rest", etc work generically on all of those data-types

- 
