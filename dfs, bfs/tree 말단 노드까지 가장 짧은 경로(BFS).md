# tree 말단 노드까지 가장 짧은 경로(DFS)

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
  	System.out.println(bfs(root));
  }
  
  public static int bfs(Node root) {
  	Queue<Node> queue = new LinkedList<>();
  	queue.offer(root);
  	int level = 0;
  	while(!queue.isEmpty()) {
  	    int len = queue.size();
  	    for (int i = 0; i < len; i++) {
  	    	Node cur = queue.poll();
  	    	if (cur.left == null && cur.right == null)
  	    		return level;  
  	    	if (cur.left != null)
  	    		queue.offer(cur.left);
  	    	
  	    	if (cur.right != null)
  	    		queue.offer(cur.right);
  	    }
  	    level++;
  	}
  	
  	return level;
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
