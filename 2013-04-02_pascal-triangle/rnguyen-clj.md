This one took me a while, but it was fun to do.  Again, in Clojure:
 

```clojure
(defn get-row [prev-row]
   (concat [1] (map + prev-row (rest prev-row)) [1]))
 
(def lazy-pascal (iterate get-row [1]))
 
(defn print-pascal [nrows]
   (doseq [row (take nrows lazy-pascal)]
      (apply println row)))
 
(print-pascal 5)
```
 
```
Output:

[rnguyen@t14ubsoff04 wk2]$ clj –i solution.clj
Clojure 1.5.1
1
1 1
1 2 1
1 3 3 1
1 4 6 4 1
```
 
`lazy-pascal` is kind of like a generator expression in python.  It uses
`clojure.core/iterate` to produce a lazy sequence of
`(x, (f x), (f (f x)), ...)`.  All I have to do is start it with my
function `get-row` and the first row of the triangle.


## Submitted by

Radford Nguyen
2013/04/02
