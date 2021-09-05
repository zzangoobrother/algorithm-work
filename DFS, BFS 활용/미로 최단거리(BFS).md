# 미로 최단거리 찾기 (BFS)
7*7 격자 미로에서 탈출하는 경로의 총 가지수 출력 출발점 (1, 1), 도착점 (7, 7), 1은 벽, 0은 통로이다.

```java
import java.util.*

public class algorithm {
  static int[][] arr;
	static int[] dx = {1, 0, -1, 0};
	static int[] dy = {0, -1, 0, 1};
	static int[][] dis = new int[8][8];
	static int input1, input2;
  
  public static void main(String[] args) {
    Scanner in=new Scanner(System.in);
		
		arr = new int[8][8];
		for (int i = 1; i <= 7; i++) {
			for (int j = 1; j <= 7; j++) {
				arr[i][j] = in.nextInt();
			}
		}
		
		bfs(1, 1);
		
		if (dis[7][7] == 0) {
			System.out.println(-1);
		} else {
			System.out.println(dis[7][7]);
		}
  }
  
  public static void bfs(int x, int y) {
		Queue<Point> queue = new LinkedList<>();
		queue.offer(new Point(x, y));
		arr[1][1] = 1;
		while (!queue.isEmpty()) {
			Point temp = queue.poll();
			for (int i = 0; i < 4; i++) {
				int nx = temp.x + dx[i];
				int ny = temp.y + dy[i];
				if (nx > 0 && nx < 8 && ny > 0 && ny < 8 && arr[nx][ny] == 0) {
					dis[nx][ny] = dis[temp.x][temp.y] + 1;
					arr[nx][ny] = 1;
					queue.offer(new Point(nx, ny));
				}
			}
		}
	}
}

class Point {
	int x;
	int y;

	Point(int x, int y) {
		this.x = x;
		this.y = y;
	}
}
```
