# @foxglove/avl

> _Adelson-Velsky-Landis (AVL) self-balancing binary trees in TypeScript_

## Introduction

[AVL trees](https://en.wikipedia.org/wiki/AVL_tree) are self-balancing binary trees that are commonly used to implement sorted sets. In addition to the common insertion, deletion, and retrieval operations, this implementation also supports range queries, greater than, and less than searches.

## Usage

```Typescript
import { AVLTree } from "@foxglove/avl";

const tree = new AVLTree<number, string>();
tree.set(0, "zero");
tree.set(1, "1");
tree.set(1, "one");
tree.set(3, "three");
tree.set(2, "two");
tree.delete(0);
console.log(tree.has(0)); // false
console.log(tree.get(1)); // "one"
console.log(tree.size); // 3
console.log(tree.minEntry()); // [1, "one"]
console.log(tree.maxEntry()); // [3, "three"]
console.log(tree.findLessThan(2)); // [1, "one"]
console.log(tree.findGreaterThanOrEqual(2)); // [2, "two"]
tree.forEach((value, key) => console.log(value)); // "one" "two" "three"
tree.range(2, 3, (value, key) => console.log(value)); // "two" "three"
console.log(tree.pop()); // [3, "three"]
console.log(tree.shift()); // [1, "one"]
tree.clear();

// Use a custom comparator for non-Number keys
const bigintTree = new AVLTree<bigint, string>((a, b) => Number(a - b));
bigintTree.set(1n, "one");
```

## Alternatives

[avl](https://github.com/w8r/avl) - Optional support for duplicate keys, but return values can mutate after delete() calls, missing range query optimization, no find\[Less/Greater\]Than\[OrEqual\] queries, no iterators, and naming conventions do not follow ES6 container patterns.

## License

@foxglove/avl is licensed under [MIT License](https://opensource.org/licenses/MIT).

## Releasing

1. Run `yarn version --[major|minor|patch]` to bump version
2. Run `git push && git push --tags` to push new tag
3. GitHub Actions will take care of the rest

## Stay in touch

Join our [Slack channel](https://foxglove.dev/join-slack) to ask questions, share feedback, and stay up to date on what our team is working on.
