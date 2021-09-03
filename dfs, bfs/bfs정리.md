# BFS 정리

```java
import java.util.*

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
    bfs(root);
  }
  
  public static void bfs(Node root) {
	Queue<Node> queue = new LinkedList<>();
	queue.offer(root);
	int level = 0;
	while (!queue.isEmpty()) {
		int len = queue.size();
		for (int i = 0; i < len; i++) {
			Node cur = queue.poll();
			System.out.print(cur.data + " ");
			if (cur.left != null) 
				queue.offer(cur.left);
		
			if (cur.right != null)
				queue.offer(cur.right);
		}
		level++;
	}
    }
}

class Node {
    int data;
    Node left, right;
    public Node(int val) {
    	data=val;
    	left = right = null;
    }
}
```
