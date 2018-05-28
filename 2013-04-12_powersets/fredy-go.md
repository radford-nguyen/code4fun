My ugly and verbose solution in Go.

 

```golang
package main
 
import (
    "fmt"
    "sort"
    "strings"
)
 
func powerset(set []int) [][]int {
    m := map[string][]int{}
    m = recursePowerset(set, m)
    result := [][]int{set}
    for _, v := range m {
        result = append(result, v)
    }
    return result
}
 
func join(s []int) string {
    result := []string{}
    for _, v := range s {
        result = append(result, string(v))
    }
    return strings.Join(result, ",")
}
 
func recursePowerset(set []int, accumulator map[string][]int) map[string][]int {
    if len(set) == 0 {
        return accumulator
    }
    for i, _ := range set {
        subset := make([]int, len(set[:i]))
        copy(subset, set[:i])
        subset = append(subset, set[i+1:len(set)]...)
        sort.Ints(subset)
        key := join(subset)
        accumulator[key] = subset
        accumulator = recursePowerset(subset, accumulator)
    }
    return accumulator
}
 
func main() {
    set := []int{1, 2, 3, 4}
    powset := powerset(set)
    // pretty print the output
    for i := 0; i <= len(set); i++ {
        for _, v := range powset {
            if len(v) == i {
                fmt.Println(v)
            }
        }
    }
}


## Submitted by

Fredy Wijaya
2013-04-12
