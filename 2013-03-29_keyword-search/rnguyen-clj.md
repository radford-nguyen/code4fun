In inefficient and unreadable clojure:

```clojure
(defn words-from [sentence]
   (re-seq #"+" sentence))
 
(defn blorp [sentence]
   (letfn [(f [word] (hash-map word #{sentence}))]
      (into {} (map f (words-from sentence)))))
 
(defn index [seed]
   (apply merge-with into (map blorp seed)))
 
(defn show [c] (doseq [x c] (println x)))
 
(defn main []
   (let [seed (list "java is cool"
                    "cool java library"
                    "c++ is a cool language"
                    "both java and c++ are cool")
         idx  (index seed)]
 
      (show (map idx (words-from "java cool")))
      (println)
      (show (map idx (words-from "c++ cool")))
      (println)
      (show (map idx (words-from "whatever")))))
 
(main)
```

## Submitted by

Radford Nguyen
2013-04-02
