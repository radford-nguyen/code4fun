Brute-force solution in C++11.

If you plan to solve it in liner time, you need to read this book :)
One whole book is dedicated to solving that problem.

http://www.amazon.com/dp/363901376X/ref=cm_sw_su_dp?tag=a200-20

 

```cpp
#include <iostream>
#include <vector>
#include <cassert>
using namespace std;
 

int maxConsecutiveSum(const vector<int>& v) {
    auto max = 0;
    for (auto i = 0; i < v.size(); i++) {
        auto sum = 0;
        for (auto j = i; j < v.size(); j++) {
            sum += v[j];
            if (j == 0) {
                max = v[j];
            } else {
                if (max < sum) {
                    max = sum;
                }
            }
        }
    }
    return max;
}

int main() {
    assert(maxConsecutiveSum({-1, 5, 6, -2, 20, -50, 4}) == 29);
    assert(maxConsecutiveSum({1, 2, -1, 5}) == 7);
    assert(maxConsecutiveSum({-1, 2, -1, 5, -2, 7, -1, 9}) == 19);
    assert(maxConsecutiveSum({1, 2, -1, 5, -2, 7, -1, 9}) == 20);
    assert(maxConsecutiveSum({1, -1, -1}) == 1);
    assert(maxConsecutiveSum({-1, -1, 1}) == 1);
    return 0;
}
```
 

## Submitted by

Fredy wijaya  
2013/10/11
