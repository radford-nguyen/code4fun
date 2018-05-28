Hell yeah, Tabiul, that’s a kick-ass solution.  It’s just like this one
(not mine) in Clojure:

```clojure
(fn f [[[a] & b]]
   (+ a (if b (min (f (map rest b))
                   (f (map butlast b))) 0)))
```

## Submitted by

Radford Nguyen
2013-09-06
