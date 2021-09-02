# 부분집합 구하기(DFS)
자연수 N이 입력되면 1부터 N까지 원소를 갖는 부분 집합 출력

```java
import java.util.Scanner;

public class algorithm {
  static int num;
	static int[] flag;
  public static void main(String[] args) {
    Scanner in=new Scanner(System.in);
		num = in.nextInt();
		flag = new int[num + 1];
		dfs(1);
  }
  
  public static void dfs(int in) {
		if (in == num + 1) {
			String result = "";
			for (int i = 1; i <= num; i++) {
				if (flag[i] == 1)
					result += i + " ";
			}
			
			if (result.length() > 0)
				System.out.println(result);
			
			return;
		}
		flag[in] = 1;
		dfs(in+1);

		flag[in] = 0;
		dfs(in+1);
	}
}
```
