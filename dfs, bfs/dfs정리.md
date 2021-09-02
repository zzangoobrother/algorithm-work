# dfs
이진트리 순회
```java
public class algorithm {
  static Node root;
  public static void main(String[] args) {
    root = new Node(1);
    root.left = new Node(2);
    root.right = new Node(3);
    root.left.left = new Node(4);
    root.left.right = new Node(5);
    root.right.left = new Node(6);
    root.right.right = new Node(7);
    dfs(root);
  }
  
  public static void dfs(Node root) {
     if (root == null)
     	return;
     
     // 전위순회 : 1 2 4 5 3 6 7
     System.out.println(root.data + " ");
     
     dfs(root.left);
     
     // 중위순회 : 4 2 5 1 6 3 7
     System.out.println(root.data + " ");
     
     dfs(root.right);
     
     // 후위순회 : 4 5 2 6 7 3 1
     System.out.println(root.data + " ");
	}
  }

class Node {
  int data;
  Node left, right;
  public Node(int data) {
     this.data = data;
     left = right = null;
  }
}
```
