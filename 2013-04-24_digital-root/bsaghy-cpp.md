Yeah, perhaps I shouldn’t have scrolled down, either.

Recursion seems like the way to go here if you’re not going to use mod. I think
even with very large integers it shouldn’t be a very deep call. 

Also, your function name doesn’t have the same gardening connotations that mine
does.  :-P

Since mod is so easy to translate to other languages:

```cpp
#include<stdio.h>

int main( int argc, char *argv[] ){
    if (argc !=2){
        printf( "usage: %s <n>");
        return 1;
    } else {
        int n = atoi(argv[1]);
        int root = 1+((n-1)%9);
        printf( "The digital root of %i is %i", n, root);
    }
    return 0;
}
```


## Submitted by

Brian Saghy
2013-04-24
