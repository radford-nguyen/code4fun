This is probably non-optimal. I have to convert from integer to string first
and check for a palindrome. I remember I saw a question about palindrome in the
recent Google Code Jam. Is this question from Google Code Jam?

 

```golang
package main
 
import (
    "fmt"
    "strconv"
)
 
func isPalindrome(n int) bool {
    str := strconv.Itoa(n)
    j := len(str) - 1 
    for i := 0; i < len(str) / 2; i++ {
        if (str[i] != str[j]) {
            return false
        }   
        j-- 
    }   
    return true
}
 
func main() {
    fmt.Println(isPalindrome(141))
    fmt.Println(isPalindrome(3))
    fmt.Println(isPalindrome(99))
    fmt.Println(isPalindrome(14341))
    fmt.Println(isPalindrome(1234))
}
```

## Submitted by

Fredy Wijaya
2013-04-23
