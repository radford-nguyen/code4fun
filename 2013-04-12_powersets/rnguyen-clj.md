Clojure ftw.  Also adding Janiga, who says that he’s been feeling left out.


```clojure
(defn powerset [s]
  (reduce 
    (fn [res x] 
      (set (concat res (map #(conj % x) res) [#{x}])))
    #{#{}} s))
```

## Submitted by

Radford Nguyen
2013-04-12
