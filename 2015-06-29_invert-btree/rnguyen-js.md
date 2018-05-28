The only way to do this is in a language with pattern matching, but Roy beat me
to it, so here's my solution in plain js.

```js
// invert (in place!) the binary tree
function invert(bintree) {
 
  var isLeaf = function(node) {
    return !node || !node.left && !node.right;
  };
 
  var swapLeaves = function(node) {
    var t = node.left;
    node.left = node.right;
    node.right = t;
  };
 
  if (isLeaf(bintree)) return;
 
  swapLeaves(bintree);
  invert(bintree.left);
  invert(bintree.right);
}

var tree = {
  value: 1,
  left:  { val: 2,
           left:  { val: 4 },
           right: { val: 5,
                   left: { val: 6 }  }},
  right: { val: 3 }
};
 
console.log(JSON.stringify(tree, null, 2));
invert(tree);
console.log(JSON.stringify(tree, null, 2));
```

```
{
  "value": 1,
  "left": {
    "val": 2,
    "left": {
      "val": 4
    },
    "right": {
      "val": 5,
      "left": {
        "val": 6
      }
    }
  },
  "right": {
    "val": 3
  }
}
{
  "value": 1,
  "left": {
    "val": 3
  },
  "right": {
    "val": 2,
    "left": {
      "val": 5,
      "right": {
        "val": 6
      }
    },
    "right": {
      "val": 4
    }
  }
}
```

## Submitted by

Radford Nguyen
2015/06/29
