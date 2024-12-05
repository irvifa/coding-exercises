# Cord Tree

```
// "static void main" must be defined in a public class.
import java.util.*;

/**
A cord tree is a binary tree of strings. A node in this tree can be a leaf node or an internal node.
An internal node has two children, a left child and a right child. It also has a length of all the children under it
A leaf nodes have a value and a length

      InternalNode, 26
      /              \   
     /                \                         
    /                  \
 Leaf(5, ABCDE)      InternalNode, 21
                       /           \
                      /             \
                     /               \
                    /                 \
         Leaf(10, FGHIJKLMNO)     Leaf(11, PQRSTUVWXYZ)  

Define a Data Structure that represents a Cord tree.
Define a function that takes in a tree and an index and returns the character at that index.
*/


public class Main {
      static class Node{
    private int length;

    public Node(int length) {
      this.length = length;
    }
  }

  static class LeafNode extends Node{
    private String value;

    public LeafNode(int length, String value) {
      super(length);
      this.value = value;
    }

    public String getValue() {
      return value;
    }
  }

  static class InternalNode extends Node{
    private Node leftChild;
    private Node rightChild;

    public InternalNode(int length, Node leftChild, Node rightChild) {
      super(length);
      this.leftChild = leftChild;
      this.rightChild = rightChild;
    }
  }

  static class Tree {
    private Node root;

    public Tree(Node root) {
      this.root = root;
    }

    public Character findCordAtIndex(int index) {
      return findCordAtIndex(index, root);
    }

    public Character findCordAtIndex(int index, Node root) {
        int length = root.length;
        while (index <= root.length) {
            if(root instanceof LeafNode) {
          // if a leaf node, base case
              String s = ((LeafNode) root).value;
              return s.charAt(index-1);
            } else {
              // if a internal node
              // check left right
              InternalNode internalNode = (InternalNode) root;
              Node left = internalNode.leftChild;
              Node right = internalNode.rightChild;
              if(index <= left.length) {
                // go to left side
                root = left;
                // return findCordAtIndex(index, left);
              } else {
                // got to right side
                  index = index - left.length;
                  root = right;
              }
            }
        }
      return null;
    }
  }
    public static void main(String[] args) {
    // Build tree
    Node root = new InternalNode(26, new LeafNode(5, "ABCDE"), new InternalNode(21,
        new LeafNode(10, "FGHIJKLMNO"), new LeafNode(11, "PQRSTUVWXYZ")));
    
    Tree cordTree = new Tree(root);
        
    Map<Integer, Character> testCases = new HashMap<>();
        testCases.put(10, 'J');
        testCases.put(3, 'C');
        testCases.put(16, 'P');
    testCases.keySet().forEach(k -> {
        assert cordTree.findCordAtIndex(k).equals(testCases.get(k));
        System.out.println(cordTree.findCordAtIndex(k));
    });
  }
}
```
