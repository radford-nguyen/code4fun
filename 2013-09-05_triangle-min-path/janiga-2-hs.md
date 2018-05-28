Cleaned up
 
```haskell
minPath :: [[(Int)]] -> Int
minPath [[]] = 0
minPath xs = head( foldr1 (minP) xs )
 
minP xs ys = zipWith (+) xs (zipWith (min) (tail ys) (init ys))
 
hithere> 3 == minPath [[1],[2,3]]
True
hithere> 20 == minPath [[3],[2,4],[1,9,3],[9,9,2,4],[4,6,6,7,8],[5,7,3,5,1,2]]
True
hithere> 7 == minPath [[1],[2,4],[5,1,4],[2,3,4,5]]
True
hithere> 3 == minPath [[3]]
True
hithere> 4 == minPath [[3],[1,2]]
True
```


## Submitted by

Matthew Janiga (manager writing haskell!)
2013-09-07
