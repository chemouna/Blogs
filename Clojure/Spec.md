
# Spec 

(defprotocol Spec
  (conform* [spec x])
  (unform* [spec y])
  (explain* [spec path via in x])
  (gen* [spec overrides path rmap])
  (with-gen* [spec gfn])
  (describe* [spec]))
 
 
 - explain-data 
  
## Spec gen 
 
### generators combinators 
- cat 
 

### Examples from ring spec 

- expl for generating uri params 
```Clojure
(defn- gen-query-string []
  (->> (gen/tuple (gen/not-empty (gen/string-alphanumeric)) (gen-string uri-chars))
       (gen/fmap (fn [[k v]] (str k "=" v)))
       (gen/vector)
       (gen/fmap #(str/join "&" %))))
```

### Comparing Spec.check  to Haskell QuickCheck 
