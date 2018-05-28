I shouldn’t have given the Wikipedia link :) This is my solution using
non-mathematical way. 

```golang
package main
 
import (
    "fmt"
    "os"
    "strconv"
)
 
func digitalRoot(n int) int {
    if n < 10 {
        return n
    }
    sum := 0
    for n > 0 {
        sum += n % 10
        n /= 10
    }
    return digitalRoot(sum)
}
 
func main() {
    n, e := strconv.Atoi(os.Args[1])
    if e != nil {
        fmt.Println("Invalid number:", os.Args[1])
        os.Exit(1)
    }
    fmt.Println(digitalRoot(n))
}
```


## Submitted by

Fredy Wijaya
2013-04-24
