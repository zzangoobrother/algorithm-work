# 피자 배달 거리(DFS)

```java
import java.util.*;

public class algorithm {
  static int input1, input2;
	static List<Position> pizza, home;
	static int[] combi;
	static int result = Integer.MAX_VALUE;
  
  public static void main(String[] args) {
    Scanner in=new Scanner(System.in);
		input1 = in.nextInt();
		input2 = in.nextInt();
    
    pizza = new ArrayList<>();
		home = new ArrayList<>();
    
    int[][] arr = new int[input1][input1];
		for (int i = 0; i < input1; i++) {
			for (int j = 0; j < input1; j++) {
				arr[i][j] = in.nextInt();
				if (arr[i][j] == 1)
					home.add(new Position(i, j));
				else if (arr[i][j] == 2)
					pizza.add(new Position(i, j));
			}
		}
    
    combi = new int[input2];
		dfs(0, 0);
		
		System.out.println(result);
  }
  
  public static void dfs(int n, int s) {
		if (n == input2) {
			int sum = 0;
			for (Position h : home) {
				int dis = Integer.MAX_VALUE;
				for (int i : combi) {
					dis = Math.min(dis, Math.abs(h.x - pizza.get(i).x) + Math.abs(h.y - pizza.get(i).y));
				}
				sum += dis;
			}
			result = Math.min(result, sum);
		} else {
			for (int i = s; i < pizza.size(); i++) {
				combi[n] = i;
				dfs(n+1, i+1);
			}
		}
	}
}

class Position {
	int x;
	int y;
	public Position(int x, int y) {
		this.x = x;
		this.y = y;
	}
}
```
