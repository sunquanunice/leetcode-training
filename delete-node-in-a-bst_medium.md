https://leetcode.com/problems/delete-node-in-a-bst/
```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public TreeNode deleteNode(TreeNode root, int key) {
        TreeNode result = root;
        TreeNode parent = null;
        TreeNode currentNode = root;
        TreeNode nodeToDelete = null;
        while(currentNode != null) {
            if (currentNode.val == key) {
                nodeToDelete = currentNode;
                break;
            } else if (currentNode.val > key) {
                parent = currentNode;
                currentNode = currentNode.left;
            } else {
                parent = currentNode;
                currentNode = currentNode.right;
            }
        }
        
        if (nodeToDelete != null) {
           TreeNode candidateNode = findCandidateNode(nodeToDelete);
            if (candidateNode != null) {
               //candidateNode.left = nodeToDelete.left;
               //candidateNode.right = nodeToDelete.right;
               if (parent == null) {
                   //result = candidateNode;
                   if (root.left != candidateNode) {
                   candidateNode.left = root.left;
                   }
                   z
                   if (root.right != candidateNode) {
                   candidateNode.right = root.right;
                   }
               } else {
                   /*
                   if (parent.val < nodeToDelete.val) {
                       parent.right = candidateNode;
                   } else {
                       parent.left = candidateNode;
                   }*/
               }
            }
            
            if (parent == null) {
                   result = candidateNode;
               } else {
                   if (parent.val < nodeToDelete.val) {
                       parent.right = candidateNode;
                   } else {
                       parent.left = candidateNode;
                   }
               }
        }

        return result;
    }
    
    private TreeNode findCandidateNode(TreeNode nodeToDelete) {
        if (nodeToDelete.left == null && nodeToDelete.right == null) {
               return null;         
        } else if (nodeToDelete.left == null) {
            return nodeToDelete.right;
        } else if (nodeToDelete.right == null) {
            return nodeToDelete.left;
        } else {
            TreeNode parent = nodeToDelete;
            TreeNode currentNode = nodeToDelete.left;
            while(currentNode.right != null) {
                parent = currentNode;
                currentNode = currentNode.right;
            }
            
            if (parent.left != currentNode) {
                parent.right = currentNode.left;
            } else {
                currentNode.right = parent.right; 
            }
            return currentNode;
        }
    }
}
```
