An iterative solution in Go.

```golang
package main
 
import (
    "fmt"
)
 
func min(m map[int][]int) int {
    r := m[0][0]
    for _, v := range m {
        for _, v1 := range v {
            if r > v1 {
                r = v1
            }
        }
    }
    return r
}
 
func triangleMinPath(input [][]int) int {
    result := map[int][]int{}
    result[0] = input[0]
    for i := 1; i < len(input); i++ {
        result = minPath(input[i], result)
    }
    return min(result)
}
 
func minPath(input []int, accu map[int][]int) map[int][]int {
    result := map[int][]int{}
    for i := 0; i < len(input); i++ {
        for j := 0; j < len(accu[i]); j++ {
            if _, ok := result[i]; !ok {
                result[i] = []int{}
            }
            result[i] = append(result[i], input[i]+accu[i][j])
            if _, ok := result[i+1]; !ok {
                result[i+1] = []int{}
            }
            result[i+1] = append(result[i+1], input[i+1]+accu[i][j])
        }
    }
    return result
}
 
func main() {
    fmt.Println(triangleMinPath([][]int{{1}, {2, 4}, {5, 1, 4}, {2, 3, 4, 5}}))
    fmt.Println(triangleMinPath([][]int{{3}, {2, 4}, {1, 9, 3}, {9, 9, 2, 4}, {4, 6, 6, 7, 8}, {5, 7, 3, 5, 1, 4}}))
    fmt.Println(triangleMinPath([][]int{{3}}))
    fmt.Println(triangleMinPath([][]int{{3}, {1, 2}}))
}
```

```
Output:
7
20
3
4
```


## Submitted by

Fredy Wijaya
2013-09-05
