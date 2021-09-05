# 미로탐색(DFS)
7*7 격자 미로에서 탈출하는 경로의 총 가지수 출력
출발점 (1, 1), 도착점 (7, 7), 1은 벽, 0은 통로이다.

```java
import java.util.*

public class algorithm {
  static int[][] arr;
	static int[] dx = {1, 0, -1, 0};
	static int[] dy = {0, -1, 0, 1};
	static int result;
	static int input1, input2;
  
  public static void main(String[] args) {
    Scanner in=new Scanner(System.in);
		
		arr = new int[8][8];
		for (int i = 1; i <= 7; i++) {
			for (int j = 1; j <= 7; j++) {
				arr[i][j] = in.nextInt();
			}
		}
		arr[1][1] = 1;
		
		dfs(1, 1);
		System.out.println(result);
  }
  
  public static void dfs(int x, int y) {
		if (x == 7 && y == 7) {
			result++;
		} else {
			for (int i = 0; i < 4; i++) {
				int nx = x + dx[i];
				int ny = y + dy[i];
				if (nx > 0 && nx < 8 && ny > 0 && ny < 8 && arr[nx][ny] == 0) {
					arr[nx][ny] = 1;
					dfs(nx, ny);
					arr[nx][ny] = 0;
				}
			}
		}
	}
}
```
