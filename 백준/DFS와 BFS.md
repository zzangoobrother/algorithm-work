## DFS와 BFS

문제 : https://www.acmicpc.net/problem/1260

```java
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class Main {
  public static int[][] arr;
  public static boolean[] visited;

  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);

    int num = sc.nextInt();
    int count = sc.nextInt();
    int start = sc.nextInt();

    arr = new int[num + 1][num + 1];

    for (int i = 0; i < count; i++) {
      int a = sc.nextInt();
      int b = sc.nextInt();

      arr[a][b] = 1;
      arr[b][a] = 1;
    }

    visited = new boolean[num + 1];
    dfs(start);

    System.out.println();

    visited = new boolean[num + 1];
    bfs(start);
  }

  public static void dfs(int start) {
    visited[start] = true;
    System.out.print(start + " ");

    if (start == arr.length) {
      return;
    }

    for (int i = 1; i < arr.length; i++) {
      if (arr[start][i] == 1 && visited[i] == false) {
        dfs(i);
      }
    }
  }

  public static void bfs(int start) {
    Queue<Integer> queue = new LinkedList<>();

    queue.add(start);
    visited[start] = true;
    System.out.print(start + " ");

    while (!queue.isEmpty()) {
      int temp = queue.poll();
      for (int i = 1; i < arr.length; i++) {
        if (arr[temp][i] == 1 && visited[i] == false) {
          queue.offer(i);
          visited[i] = true;
          System.out.print(i + " ");
        }
      }
    }
  }
}
```
