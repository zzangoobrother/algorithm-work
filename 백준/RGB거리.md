## RGB거리

문제 : https://www.acmicpc.net/problem/1149

```java
import java.util.Scanner;

public class Main {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);

    int[][] dp = new int[1001][3];
    int[][] arr = new int[1001][3];

    int count = sc.nextInt();
    for (int i = 1; i <= count; i++) {
      arr[i][0] = sc.nextInt();
      arr[i][1] = sc.nextInt();
      arr[i][2] = sc.nextInt();
    }

    for (int i = 1; i <= count; i++) {
      dp[i][0] = Math.min(dp[i-1][1], dp[i-1][2]) + arr[i][0];
      dp[i][1] = Math.min(dp[i-1][0], dp[i-1][2]) + arr[i][1];
      dp[i][2] = Math.min(dp[i-1][0], dp[i-1][1]) + arr[i][2];
    }

    System.out.println(Math.min(dp[count][0], Math.min(dp[count][1], dp[count][2])));
  }
}
```
