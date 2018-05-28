I'm lazy so it's not tail-recursive, but in Clojure:

```clojure
(def tree
  '(1 (2 (4) (5 nil (6))) (3)))
 
(defn invert [node]
  (letfn [
          (vl    [n] (first n))
          (lt    [n] (first (next n)))
          (rt    [n] (first (next (next n))))
          (leaf? [n] (not-any? identity [(lt n) (rt n)]))
          ]
    (if (leaf? node)
      node
      (list (vl node) (invert (rt node)) (invert (lt node))))))
```
 
```
Output:
 
rnguyen@D7-2UA94610GV ~/dev/clj/prog4fun (master)
$ clj -i  invert_bintree.clj -r
Clojure 1.5.1
user=> (println tree)
(1 (2 (4) (5 nil (6))) (3))

user=> (println (invert (tree))
(1 (3) (2 (5 (6) nil) (4)))

user=> (println tree)
(1 (2 (4) (5 nil (6))) (3))
```


## Submitted by

Radford Nguyen
2015/06/29
