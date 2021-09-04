# 동전교환(DFS)
N개의 동전이 주어지고, 동전의 금액들이 주어진다.
이때 거슬러줄 금액에서 최소의 갯수 출력

```java
import java.util.*

public class algorithm {
  static Integer[] arr;
	static int input1, input2;
	static int result = 501;
  
  public static void main(String[] args) {
    Scanner in=new Scanner(System.in);
		input1 = in.nextInt();
				
		arr = new Integer[input1];
		for (int i = 0; i < input1; i++) {
			arr[i] = in.nextInt();
		}
		Arrays.sort(arr, Collections.reverseOrder());
		input2 = in.nextInt();
		
		dfs(0, 0);
				
		System.out.println(result);
  }
  
  public static void dfs(int v, int sum) {
		if (sum > input2)
			return;
		if (v >= result)
			return;
		
		if (sum == input2) {
			result = Math.min(result, v);
		} else {
			for (int i = 0; i < input1; i++) {
				dfs(v+1, sum + arr[i]);
			}
		}	
	}
}
```
