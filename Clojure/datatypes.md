
# Datatypes

## defrecord
(defrecord Employee [name room])

- You can construct an instance of the datatype by adding a dot to the end of its name.
user> (def emp (Employee. "John Smith" 304))

- Datatype instances behave like Clojure maps. You can retrieve the fields of a datatyped object by
using keywords as accessor functions:
```Clojure
user> (:name emp)
"John Smith"
```

- You can even assoc additional fields that were not part of the original datatype, without changing the
object's type.
```Clojure
user=> (assoc x :field "physics")
#:user.Scientist{:name "Albert Einstein", :iq 190, :field "physics"}
```

However, if you dissoc one of the original datatype keys, you get an ordinary map as the result.
```Clojure
user=> (dissoc x :iq)
{:name "Albert Einstein"}
```

- Datatypes can also implement methods from Java interfaces. For example, you could implement the
java.lang.Comparable interface, allowing your new datatype to support the Clojure compare function:
```Clojure 
user> (defrecord Pair [x y]
        java.lang.Comparable
            (compareTo [this other]
                ....
```

`
