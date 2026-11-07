# Leetcode_Day98
# Day 98 — Path Sum

**LeetCode 112 | Easy | Java**

## Problem

Given the root of a binary tree and an integer `targetSum`, determine whether the tree has a root-to-leaf path where the sum of all node values equals `targetSum`.

A leaf is a node that has no children.

### Example

Input:
```text
root = [5,4,8,11,null,13,4,7,2,null,null,null,1]
targetSum = 22
```

Output:
```text
true
```

Explanation:

One valid root-to-leaf path is:

`5 → 4 → 11 → 2`

Sum = `5 + 4 + 11 + 2 = 22`

---

## Approach: Recursion (DFS)

I used Depth First Search (DFS) with recursion to explore the possible root-to-leaf paths.

Instead of calculating the complete sum at every step, I subtract the current node's value from the target sum.

### Steps

1. If the root is `null`, return `false`.
2. Check whether the current node is a leaf.
3. If it is a leaf, compare its value with the remaining target sum.
4. Otherwise, subtract the current node's value from `targetSum`.
5. Recursively check both the left and right subtrees.
6. If either subtree contains a valid path, return `true`.

### Java Code

```java
class Solution {
    public boolean hasPathSum(TreeNode root, int targetSum) {

        if(root == null) {
            return false;
        }

        if(root.left == null && root.right == null) {
            return targetSum == root.val;
        }

        int remaining = targetSum - root.val;

        return hasPathSum(root.left, remaining) ||
               hasPathSum(root.right, remaining);
    }
}
```

---

## Complexity Analysis

**Time Complexity: O(n)**

In the worst case, every node is visited once.

**Space Complexity: O(h)**

The recursive call stack depends on the height of the tree.

- Balanced tree: O(log n)
- Skewed tree: O(n)

---

## What I Learned

- How to use DFS to explore root-to-leaf paths.
- How recursion simplifies tree traversal.
- How subtracting node values helps track the remaining target sum.
- Why checking the leaf condition is important.
- How the OR operator helps explore both possible branches.

## Key Takeaway

Sometimes solving a problem becomes easier when we stop carrying the entire problem forward and simply track what is still remaining.
