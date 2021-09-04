# 최대점수 구하기(DFS)
N개의 문제 갯수와 제한시간 M이 주어진다.
한 문제당 점수와 푸는 시간이 주어질 때, 최대점수 출력

```java
import java.util.*

public class algorithm {
  static int[][] arr;
  static int input1, input2;
  static int result = 0;
  
  public static void main(String[] args) {
    Scanner in=new Scanner(System.in);
    input1 = in.nextInt();
    input2 = in.nextInt();
    
    arr = new int[input1][2];
    for (int i = 0; i < input1; i++) {
    	for (int j = 0; j < 2; j++) {
    		arr[i][j] = in.nextInt();
    	}
    }
    
    dfs(0, 0, 0);
    
    System.out.println(result);
  }
  
  public static void dfs(int v, int sum, int time) {
    if (input2 < time)
    	return;
    
    if (v == input1) {
    	result = Math.max(result, sum);
    	return;
    } else {
    	dfs(v+1, sum + arr[v][0], time + arr[v][1]);
    	dfs(v+1, sum, time);
    }
  }
}
```
