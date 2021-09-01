# LRU알고리즘
캐시 크기 N, K개 입력 일때, 최근 사용된 작업부터 차례대로 출력

- java 배열
```java
import java.util.Scanner;

public class algorithm {
  public static void main(String[] args) {
      Scanner in=new Scanner(System.in);
	    int input1 = in.nextInt();
	    int input2 = in.nextInt();
      
      int[] arr = new int[input2];
	    for (int i = 0; i < input2; i++) {
	    	arr[i] = in.nextInt();
	    }
    
      int[] result = new int[input1];
	    for (int x : arr) {
	    	int hit = -1;
	    	for (int i = 0; i < input1; i++) {
	    		if (x == result[i]) {
	    			hit = i;
	    			break;
	    		}
	    	}
	    	if (hit == -1) {
	    		for (int i = input1-1; i >= 1; i--) {
	    			result[i] = result[i-1];
	    		}
	    	} else {
	    		for (int i = hit; i >= 1; i--) {
	    			result[i] = result[i-1];
	    		}
	    	}
	    	result[0] = x;
	    }
  }
}
```

- List java 손코딩 테스트 연습을 위해 List 풀이는 자제
```java
import java.util.Scanner;

public class algorithm {
   public static void main(String[] args) {
      Scanner in=new Scanner(System.in);
	    int input1 = in.nextInt();
	    int input2 = in.nextInt();
     
      List<Integer> list = new ArrayList<>();
      for (int i = 0; i < input2; i++) {
         int temp = in.nextInt();
         if (list.contains(temp)) {
             list.remove(Integer.valueOf(temp));
             list.add(0, temp);
         } else {
             list.add(0, temp);
         }
         if (list.size() > input1) {
             list.remove(input1);
         }
      }
   }
}
```
