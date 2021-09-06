토마토 보관 상자가 있다. 보관상자에는 익은 토마토, 안익은 토마토를 넣을 수 있고,
이때 익은 토마토는 1 안익은 토마토는 0, 토마토가 없을때는 -1로 표시한다.
이때 익은 토마토 옆에 안익은 토마토가 있을 때 안익은 토마토가 하루 후 익는다고 했을 때
모든 토마토 익는 최소의 날짜 출력
토마토가 모두 익지 못하면 -1 출력

```java
import java.util.*;

public class algorithm {
  static int input1;
  static int input2;
  static int[] dx = {1, 0, -1, 0};
  static int[] dy = {0, -1, 0, 1};
  static int[][] dis;
  static Queue<Position> queue = new LinkedList<>();
  
  public static void main(String[] args) {
    Scanner in=new Scanner(System.in);
		
    input1 = in.nextInt();
    input2 = in.nextInt();
    
    dis = new int[input2][input1];
    int[][] arr = new int[input2][input1];
    for (int i = 0; i < input2; i++) {
    	for (int j = 0; j < input1; j++) {
    		arr[i][j] = in.nextInt();
    		if (arr[i][j] == 1)
    			queue.offer(new Position(i,j));
    	}
    }
    
    int temp = queue.size();
    bfs(arr);
    
    int result = 0;
    int cnt = 0;
    for (int i = 0; i < input2; i++) {
    	for (int j = 0; j < input1; j++) {
    		if (result < dis[i][j])
    			result = dis[i][j];
    		if (dis[i][j] == 0 && arr[i][j] != -1)
    			cnt++;
    	}
    }
    
    if (cnt != temp)
    	result = -1;
    
    System.out.println(result);
  }
  
  public static void bfs(int[][] arr) {
    while (!queue.isEmpty()) {
    	Position position = queue.poll();
    	for (int i = 0; i < 4; i++) {
    	  int nx = position.x + dx[i];
    	  int ny = position.y + dy[i];
    	  if (nx >= 0 && nx < input2 && ny >= 0 && ny < input1 && arr[nx][ny] == 0) {
    	  	arr[nx][ny] = 1;
    	  	queue.offer(new Position(nx, ny));
    	  	dis[nx][ny] = dis[position.x][position.y]+1;
    	  }
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
