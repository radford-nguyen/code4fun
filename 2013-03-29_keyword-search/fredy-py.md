My solution. I don’t think this is optimal, but I can’t think of a better
solution.

 
```python
#!/usr/bin/env python
 
def build_index(dictionary):
    d = {}
    for item in dictionary:
        words = item.split()
        for word in words:
            if not word in d:
                d[word] = set()
            d[word].add(item)
    return d
 
def get_matches(index, keyword):
    words = keyword.split()
    sets = []
    for word in words:
        if word in index:
            sets.append(set(index[word]))
        else:
            return sets
    
    result = sets[0]
    for i in xrange(0, len(sets)):
        result = result.intersection(sets[i])
    return result
    
 
if __name__ == "__main__":
    dictionary = ["java is cool",
                  "cool java library",
                  "c++ is a cool language",
                  "both java and c++ are cool"]
    index = build_index(dictionary)
    print get_matches(index, "java cool")
```
