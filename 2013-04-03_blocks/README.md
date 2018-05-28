Given a sample input file with the following content:

```
{
    {
        {
        } A
    } B
    {
    } C
    {
        {
        } D
        {
        } E
    } F
} G
```
 

Explanation:

```
{
} X
```

means block X

Each block will always appears in a new line.

Find all the sub-blocks that are within a given input block.
 
Input: block B
Output: block A

Input: block F
Output: block D, block E

Input: block G
Output: block B, block C, block F, block A, block D, block E

Note: the order of the output is not important.


## Submitted by

Fredy Wijaya
2013/04/03
