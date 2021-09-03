# tree에서 말단 노드까지 가장 짧은 경로 (DFS)

```java
public class algorithm {
  static Node root;
  
  public static void main(String[] args) {
    root = new Node(1);
		root.left = new Node(2);
		root.right = new Node(3);
		root.left.left = new Node(4);
		root.left.right = new Node(5);
		System.out.println(dfs(0, root));
  }
  
  public static int dfs(int level, Node root) {
		if (root.left == null && root.right == null)
			return level;
		
		return Math.min(dfs(level+1, root.left), dfs(level+1, root.right));
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
