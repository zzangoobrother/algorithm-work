# 친구인가 (Union&Find)

N명의 학생이 주어지고 M개의 관계가 주어질 때,
마지막 줄에 두 학생이 친구인지 확인하고 출력

```java
import java.util.*;

public class algorithm {
  static int[] arr;
  
  public static void main(String[] args) {
    Scanner in=new Scanner(System.in);
    int input1 = in.nextInt();
    int input2 = in.nextInt();
    
    String result = "NO";
    
    arr = new int[input1+1];
    for (int i = 1; i <= input1; i++)
    	arr[i] = i;
    
    for (int i = 1; i <= input2; i++) {
    	int a = in.nextInt();
    	int b = in.nextInt();
    	union(a, b);
    }
    
    int a = in.nextInt();
    int b = in.nextInt();
    int fa = find(a);
    int fb = find(b);
    if (fa == fb)
    	result = "YES";
    
    System.out.println(result);
  }
  
  static void union(int a, int b) {
  	int fa = find(a);
  	int fb = find(b);
  	if (fa != fb)
  		arr[fa] = fb;
  }
	
  static int find(int v) {
  	if (v == arr[v])
  		return v;
  	else 
  		return arr[v] = find(arr[v]);
  }
}
```
