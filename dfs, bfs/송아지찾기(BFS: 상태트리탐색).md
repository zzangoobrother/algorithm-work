# 송아지찾기 (BFS: 상태트리탐색)
주인의 위치와 송아지의 위치가 입력, 송아지는 움직이지 않고 제자리에 있고,
주인은 앞으로 1, 뒤로 1, 앞으로 5를 이동할 수 잇다.
송아지 위치까지 가는 최소 점프 횟수 출력

```java
import java.util.*

public class algorithm {
  static int[] check;
  static int[] dis = {1, -1, 5};
  
  public static void main(String[] args) {
    Scanner in=new Scanner(System.in);
    int input1 = in.nextInt();
    int input2 = in.nextInt();
    check = new int[10001];
    System.out.println(bfs(input1, input2));
  }
  
  public static int bfs(int input1, int input2) {
     Queue<Integer> queue = new LinkedList<>();
     check[input1] = 1;
     queue.offer(input1);
     int level = 0;
     while (!queue.isEmpty()) {
     	int len = queue.size();
     	for (int i = 0; i < len; i++) {
     		 int cur = queue.poll();
     		 for (int x : dis) {
     			 int num = cur + x;
     			 if (num == input2)
     				 return level+1;
     			 
     			 if (num >= 1 && num <= 10000 && check[num] == 0) {
     				 check[num] = 1;
     				 queue.offer(num);
     			 }
     		 }
     	}
     	level++;
     }
     
     return level;
  }
}
```
