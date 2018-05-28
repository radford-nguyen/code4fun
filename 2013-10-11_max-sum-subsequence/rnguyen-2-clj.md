Wikipedia showed me a linear-time solution, but it won’t work for an array with
all negative numbers without a tweak.

 
```clojure
(defn- fmax [[x & xs] m1 m2]
  (cond (nil? x) m1
   :else         (let [m2 (max 0 (+ m2 x))
                       m1 (max m1 m2)]
                   (recur xs m1 m2))))
 
(defn find-max' [& nums]
  (fmax nums 0 0))
 
(assert (= (find-max' -1 5 6 -2 20 -50 4) 29))
(assert (= (find-max' 1 2 -1 5) 7))
(assert (= (find-max' -1 2 -1 5 -2 7 -1 9) 19))
(assert (= (find-max' 1 2 -1 5 -2 7 -1 9) 20))
(assert (= (find-max' 1 -1 -1) 1))
(assert (= (find-max' -1 -1 1) 1))
(assert (= (find-max' -1 -5 -22) -1)) ;; FAIL
```

Tweaked:

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
2013/10/13
