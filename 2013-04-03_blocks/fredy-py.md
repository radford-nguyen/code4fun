My solution in Python. It needs Python 2.7 and above.
 
```python
#!/usr/bin/env python
 
from collections import OrderedDict
 
def create_levels(path):
    stack = []
    level = 0
    # make sure to use ordred dict
    # since we need to know which child belongs
    # to which parent
    levels = OrderedDict()
    for line in open(path):
        stripped_line = line.strip()
        if stripped_line.startswith("{"):
            level += 1
        elif stripped_line.startswith("}"):
           # parse it
            key = stripped_line.split(" ")[1]
            levels[key] = level
            level -= 1
    return levels
 
class Node:
    def __init__(self, value):
        self.value = value
        self.children = []
 
    def __str__(self):
        return self.value
 
def build_tree(levels):
    d = {} # key is the level, value is list of nodes
    for (k, v) in levels.items():
        if not v in d:
            d[v] = []
        node = Node(k)
        d[v].append(node)
        # there are children
        if (v + 1) in d:
            for child in d[v + 1]:
                node.children.append(child)
            # don't forget to delete the key
            del d[v + 1]
    # at the end, there should only be one node (the root)
    # that has the lowest level, which is 1 in this case
    return d[1][0]
 
def subblocks(tree):
    result = []
    if tree == None: return result
    children = [x for x in tree.children]
    while len(children) > 0:
        child = children.pop(0)
        result.append(child.value)
        for x in child.children:
            children.append(x)
    return result
 
def search_node(tree, value):
    if tree.value == value: return tree
    children = [x for x in tree.children]
    while len(children) > 0:
        child = children.pop(0)
        if child.value == value:
            return child 
        for x in child.children:
            children.append(x)
    return None
 
if __name__ == "__main__":
    levels = create_levels("block.txt")
    tree = build_tree(levels)
    assert ["A"] ==  subblocks(search_node(tree, "B"))
    assert [] == subblocks(search_node(tree, "C"))
    assert ["D", "E"] == subblocks(search_node(tree, "F"))
    assert [] == subblocks(search_node(tree, "D"))
    assert ["B", "C", "F", "A", "D", "E"] == subblocks(search_node(tree, "G"))
```


## Submitted by

Fredy Wijaya
2013/04/04
