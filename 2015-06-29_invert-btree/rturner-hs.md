Haskell:

```haskell
data Tree a =  Leaf
               | Branch (Tree a) a (Tree a)
   deriving (Show)
 
invert :: Tree a -> Tree a
invert Leaf = Leaf
invert (Branch l a r) = Branch (invert r) a (invert l)
 
 
-- test case:
 
testTree :: Tree Int
testTree = Branch (Branch (Branch Leaf 4 Leaf) 2 (Branch (Branch Leaf 6 Leaf) 5 Leaf)) 1 (Branch Leaf 3 Leaf)
 
main :: IO ()
main =
   do putStrLn . show $ invert testTree
```

## Submitted by

Roy Turner
2015/06/29
