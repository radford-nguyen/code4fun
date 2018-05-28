My solution in Go.
 
```golang
package main

import (
   "fmt"
   "math"
   "strconv"
   "strings"
)

func numberToWords(num int) string {
   if num == 0 {
      return "Zero"
   }
   str := strconv.Itoa(num)
   chunks := []string{}
   for i := len(str) - 1; i >= 0; i -= 3 {
      if i-2 < 0 {
         s := str[0 : i+1]
         chunks = append(chunks, s)
         break
      }
      s := str[i-2 : i+1]
      chunks = append(chunks, s)
   }
   result := ""
   size := len(chunks) - 1
   for i := len(chunks) - 1; i >= 0; i-- {
      s := chunks[i]
      tmp := s
      remainder, _ := strconv.Atoi(tmp)
      for remainder > 0 {
         val, _ := strconv.Atoi(tmp)
         a := int(math.Pow(10, float64(len(tmp)-1)))
         if val <= 20 {
            result += getName(val) + " "
            break
         } else {
            b := val / a
            if val <= 99 {
               if b > 0 {
                  result += getName(b*a) + " "
               }
            } else {
               result += getName(b) + " " + getName(a) + " "
            }
         }
         remainder = val % a
         tmp = strconv.Itoa(remainder)
      }
      val, _ := strconv.Atoi(s)
      if val > 0 {
         if size > 0 {
            a := int(math.Pow(1000, float64(size)))
            result += getName(a) + " "
         }
      }
      size--
   }
   return strings.Trim(result, " ")
}

func getName(n int) string {
   if n == 1 {
      return "One"
   } else if n == 2 {
      return "Two"
   } else if n == 3 {
      return "Three"
   } else if n == 4 {
      return "Four"
   } else if n == 5 {
      return "Five"
   } else if n == 6 {
      return "Six"
   } else if n == 7 {
      return "Seven"
   } else if n == 8 {
      return "Eight"
   } else if n == 9 {
      return "Nine"
   } else if n == 10 {
      return "Ten"
   } else if n == 11 {
      return "Eleven"
   } else if n == 12 {
      return "Twelve"
   } else if n == 13 {
      return "Thirteen"
   } else if n == 14 {
      return "Fourteen"
   } else if n == 15 {
      return "Fifteen"
   } else if n == 16 {
      return "Sixteen"
   } else if n == 17 {
      return "Seventeen"
   } else if n == 18 {
      return "Eighteen"
   } else if n == 19 {
      return "Nineteen"
   } else if n == 20 {
      return "Twenty"
   } else if n == 30 {
      return "Thirty"
   } else if n == 40 {
      return "Forty"
   } else if n == 50 {
      return "Fifty"
   } else if n == 60 {
      return "Sixty"
   } else if n == 70 {
      return "Seventy"
   } else if n == 80 {
      return "Eighty"
   } else if n == 90 {
      return "Ninety"
   } else if n == 1000000000 {
      return "Billion"
   } else if n == 1000000 {
      return "Million"
   } else if n == 1000 {
      return "Thousand"
   } else if n == 100 {
      return "Hundred"
   }
   return ""
}
```

## Submitted by

Fredy Wijaya
2015/10/26
