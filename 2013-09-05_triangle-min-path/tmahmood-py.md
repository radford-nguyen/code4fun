Solution in python

```python
def f(triangle,pos):
    if pos[0] > len(triangle) - 1: return 0
    sol = []
    left = (pos[0] + 1, pos[1])
    right = (pos[0] + 1,pos[1] + 1) 
    sol.append(triangle[pos[0]][pos[1]] +f(triangle,left))
    sol.append(triangle[pos[0]][pos[1]] +f(triangle,right))
    return min(sol)

assert f([[3],[2,4],[1,9,3],[9,9,2,4],[4,6,6,7,8],[5,7,3,5,1,4]],(0,0)) == 20
assert f([[1],[2,4],[5,1,4],[2,3,4,5]],(0,0)) == 7
assert f([[3]],(0,0)) == 3
assert f([[3],[1,2]],(0,0)) == 4     
assert f([],(0,0)) == 0 
```

It is not possible to determine the path using my solution but the question did
not ask for that :)


## Submitted by

Tabiul Mahmood
2013-09-06
