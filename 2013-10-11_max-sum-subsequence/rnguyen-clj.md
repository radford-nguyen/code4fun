Nothing particularly exciting about my exponential-time solution.

```clojure
(defn- f [coll mx]
  (max mx (apply max (reductions + coll))))
 
(defn- g [coll mx]
  (if (empty? coll) mx
    (recur (rest coll) (f coll mx))))
 
(defn find-max [& nums]
  (g nums -10000))
```
 
```
$ clj -i solution.clj -r
Clojure 1.4.0
user=> (find-max -1 5 6 -2 20 -50 4)
29
user=> (find-max 1 2 -1 5)
7
user=> (find-max -1 2 -1 5 -2 7 -1 9)
19
user=> (find-max 1 2 -1 5 -2 7 -1 9)
20
user=> (find-max 1 -1 -1)
1
user=> (find-max -1 -1 1)
1
user=>
```


```clojure
(defn- fmax [[x & xs] m1 m2]
  (if (nil? x) m1
    (let [m2 (if (neg? m2) x (+ m2 x))
          m1 (max m1 m2)]
      (recur xs m1 m2))))
 
(defn find-max' [& [x & nums]]
  (fmax nums x x))
 
(assert (= (find-max' -1 5 6 -2 20 -50 4) 29))
(assert (= (find-max' 1 2 -1 5) 7))
(assert (= (find-max' -1 2 -1 5 -2 7 -1 9) 19))
(assert (= (find-max' 1 2 -1 5 -2 7 -1 9) 20))
(assert (= (find-max' 1 -1 -1) 1))
(assert (= (find-max' -1 -1 1) 1))
(assert (= (find-max' -1 -5 -22) -1))
```

## Submitted by

Radford Nguyen
2013/10/12
