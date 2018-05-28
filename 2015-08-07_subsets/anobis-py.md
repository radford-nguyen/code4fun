Python:

```python
for dummy_i in range(2 ** len(input)):
    out = []
    rep = ("{:0%db}"%len(input)).format(dummy_i)
    for val in range(len(input)):
        if rep[val] == '1':
            out.append(input[val])
    out.sort()
    print(out)
```

## Submitted by

Austin Nobis
2015/08/07
