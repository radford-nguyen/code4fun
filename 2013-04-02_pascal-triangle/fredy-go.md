My solution in Go.
 

```golang
package main
 
import "fmt"
import "os"
import "strconv"
 
func pascal(n int) [][]int {
    result := make([][]int, n)
    // initial value
    idx := 0
    result[idx] = []int{1}
    return recursePascal(idx, n, result)
}
 
func recursePascal(idx int, length int, accumulator [][]int) [][]int {
    if (idx == length-1) {
        return accumulator
    }
    slice := []int{1}
    for i := 0; i < len(accumulator[idx])-1; i++ {
        slice = append(slice,
            accumulator[idx][i] + accumulator[idx][i+1])
    }
    slice = append(slice, 1)
    idx++
    accumulator[idx] = slice
    return recursePascal(idx, length, accumulator)
}
 
func main() {
    n, _ := strconv.Atoi(os.Args[1])
    for _, v := range pascal(n) {
        fmt.Println(v)
    }
}
```


## Submitted by

Fredy Wijaya
2013/04/02
