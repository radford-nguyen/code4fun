Description
===========

The problem: Find the maximum sum possible from picking a contiguous
subsequence of an array.

    [-1, 5, 6, -2, 20, -50, 4]

What is the largest sum of contiguous elements available in this list?

In the example above, the maximum sum would be 29:

    [-1, 5, 6, -2, 20, -50, 4]

because `(5 + 6 - 2 + 20 = 29)`. End one element later and you'll go
negative. Start one element earlier and you'll subtract one.

```java
assert(findMaximum(List(-1, 5, 6, -2, 20, -50, 4)) == 29)

assert(findMaximum(List(1, 2, -1, 5)) == 7)

assert(findMaximum(List(-1, 2, -1, 5, -2, 7, -1, 9)) == 19)

assert(findMaximum(List(1, 2, -1, 5, -2, 7, -1, 9)) == 20)

assert(findMaximum(List(1, -1, -1)) == 1)

assert(findMaximum(List(-1, -1, 1)) == 1)
```
 
 
## Submitted by

Tabiul Mahmood
2013/10/11
