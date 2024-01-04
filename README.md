# Path-with-given-sequence
Given a binary tree and a number sequence, find if the sequence is a root-to-leaf path in the given tree.

                                                          1

                                                  0              1

                                            1            6               9


                                  The tree has path sequence: false
                                  The tree has path sequence: true

                                  

import java.util.*;

public class pathWithGivenSequence {
    public boolean find(TreeNode root, int[] sequence) {
        return findRec(root, sequence, 0);
    }

    private static boolean findRec(TreeNode currentNode, int[] sequence, int sequenceIndex) {
        if(currentNode == null) {
            return false;
        }

        if(sequenceIndex >= sequence.length || currentNode.val != sequence[sequenceIndex]) {
            return false;
        }

        if(currentNode.left == null && currentNode.right == null && sequenceIndex == sequence.length - 1) {
            return true;
        }
        return findRec(currentNode.left, sequence, sequenceIndex + 1) || findRec(currentNode.left, sequence, sequenceIndex + 1);
    }

    public static void main(String[] args) {
    pathWithGivenSequence sol = new pathWithGivenSequence();
    TreeNode root = new TreeNode(1);
    root.left = new TreeNode(0);
    root.right = new TreeNode(1);
    root.left.left = new TreeNode(1);
    root.right.left = new TreeNode(6);
    root.right.right = new TreeNode(5);

    System.out.println("Tree has path sequence: " + 
                        sol.find(root, new int[] { 1, 0, 7 }));
    System.out.println("Tree has path sequence: " + 
                        sol.find(root, new int[] { 1, 1, 6 }));
  }
}
