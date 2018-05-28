Rust (1.2):
 
```rust
fn combinations(list: &[i32]) -> Vec<Vec<i32>> {
 
  fn recur(curr_set: Vec<i32>, results: &mut Vec<Vec<i32>>, list: &[i32]) {
    match list.first() {
      None        => results.push(curr_set.clone()),
      Some(&head) => {
                       let mut plus_next = curr_set.clone();
                       plus_next.push(head);
                       recur(plus_next, results, &list[1..]);
                       recur(curr_set, results, &list[1..]);
                     }
    }
  }
 
  let mut results: Vec<Vec<i32>> = vec![];
  recur(vec![], &mut results, list,1);
  results
}
 
fn main() {
  let case1 = [1,2,3,4];
  let case2 = &mut [0,4,1];
  case2.sort();
 
  for c in combinations(&case1) {
    println!("{:?}", c);
  }
  println!("---");
  for c in combinations(case2) {
    println!("{:?}", c);
  }
}
```

## Submitted by

Radford Nguyen
2015/08/09
