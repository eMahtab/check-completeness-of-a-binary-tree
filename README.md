# Check Completeness of a Binary tree
## https://leetcode.com/problems/check-completeness-of-a-binary-tree

Given a binary tree, determine if it is a complete binary tree.

Definition of a complete binary tree from Wikipedia:
In a complete binary tree every level, except possibly the last, is completely filled, and all nodes in the last level are as far left as possible. It can have between 1 and 2h nodes inclusive at the last level h.

**Note: The tree will have between 1 and 100 nodes.**

## Implementation :

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public boolean isCompleteTree(TreeNode root) {
        if(root == null)
            return true;
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);
        boolean nullSeen = false;
        while(!queue.isEmpty()){
            TreeNode current = queue.poll();
            if(current == null){
              nullSeen = true;  
            } else {
                // If we already saw a null node and then If we see a non null node, that means its not a complete binary tree 
                if(nullSeen)
                    return false;
                queue.offer(current.left);
                queue.offer(current.right);
            }
        }
        return true;
    }
}
```

# References :
https://www.youtube.com/watch?v=j16cwbLEf9w
