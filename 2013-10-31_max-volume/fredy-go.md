```golang
package main

import (
    "fmt"
)
func maxVolume(a []int) int {
    left := 0
    right := len(a) - 1
    volume := 0
    total := 0
    for left != right {
        if a[left] <= a[right] {
            for i := left + 1; i < len(a); i++ {
                if a[left] > a[i] {
                    volume += a[left] - a[i]
                } else {
                    left = i
                    total += volume
                    volume = 0
                    break
                }
            }
        } else {
            for i := right - 1; i >= left; i-- {
                if a[right] > a[i] {
                    volume += a[right] - a[i]
                } else {
                    right = i
                    total += volume
                    volume = 0
                    break
                }
            }
        }
    }
    return total
}
func main() {
    fmt.Println(maxVolume([]int{2, 5, 1, 2, 3, 4, 7, 7, 6}) == 10)
    fmt.Println(maxVolume([]int{2, 5, 1, 3, 1, 2, 1, 7, 7, 6}) == 17)
    fmt.Println(maxVolume([]int{2, 3, 1, 2, 3, 1, 3}) == 5)
    fmt.Println(maxVolume([]int{1, 2, 3, 4, 5, 6, 7, 8, 9}) == 0)
    fmt.Println(maxVolume([]int{9, 8, 7, 6, 5, 4, 3, 2, 1}) == 0)
    fmt.Println(maxVolume([]int{1, 1, 1, 1, 1}) == 0)
    fmt.Println(maxVolume([]int{1, 0, 1}) == 1)
    fmt.Println(maxVolume([]int{5, 0, 5}) == 5)
    fmt.Println(maxVolume([]int{5, 0, 4}) == 4)
    fmt.Println(maxVolume([]int{4, 0, 5}) == 4)
    fmt.Println(maxVolume([]int{4, 0, 5, 0, 2}) == 6)
    fmt.Println(maxVolume([]int{0, 1, 0, 1, 0}) == 1)
    fmt.Println(maxVolume([]int{0, 1, 0, 0, 1, 0}) == 2)
    fmt.Println(maxVolume([]int{4, 2, 2, 1, 1, 1, 3}) == 8)
    fmt.Println(maxVolume([]int{0, 3, 2, 1, 4}) == 3)
    fmt.Println(maxVolume([]int{1, 0, 1, 0}) == 1)
    fmt.Println(maxVolume([]int{1, 0, 1, 2, 0, 2}) == 3)
    fmt.Println(maxVolume([]int{2, 5, 1, 2, 3, 4, 7, 7, 6}) == 10)
    fmt.Println(maxVolume([]int{5, 1, 0, 1}) == 1)
    fmt.Println(maxVolume([]int{2, 5, 1, 2, 3, 4, 7, 7, 6, 3, 5}) == 12)
    fmt.Println(maxVolume([]int{3, 0, 1, 0, 2}) == 5)
}
```


## Submitted by

Fredy Wijaya
2013/11/01
