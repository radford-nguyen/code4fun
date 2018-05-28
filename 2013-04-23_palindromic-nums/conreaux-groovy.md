My answer in Groovy:

 

```groovy
def isPal(int n) { s = n.abs().toString(); s == s.reverse() }

assert isPal(3) == true
assert isPal(99) == true
assert isPal(141) == true
assert isPal(14341) == true

assert isPal(-3) == true
assert isPal(-99) == true
assert isPal(-141) == true
assert isPal(-14341) == true

assert isPal(21) == false
assert isPal(314) == false
assert isPal(2013) == false
assert isPal(1234) == false
```


## Submitted by

Patrick Conreaux
2013-04-24
