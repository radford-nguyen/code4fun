Morning Y’all!

Haskell:

```haskell
minP xs ys = zipWith (+) xs (zipWith (min) (tail ys) (init ys))
 
hithere> let t1 = [[1],[2,3]]
hithere> let t2 = [[3],[2,4],[1,9,3],[9,9,2,4],[4,6,6,7,8],[5,7,3,5,1,2]]
hithere> let t3 = [[1],[2,4],[5,1,4],[2,3,4,5]]
hithere> let t4 = [[3]]
hithere> let t5 = [[3],[1,2]]
hithere> let t6 = [[]]
hithere> foldr1 (minP) t1
[3]
hithere> foldr1 (minP) t2
[20]
hithere> foldr1 (minP) t3
[7]
hithere> foldr1 (minP) t4
[3]
hithere> foldr1 (minP) t5
[4]
hithere> foldr1 (minP) t6
[]
```


## Submitted by

Matthew Janiga (manager writing haskell!)
2013-09-07
