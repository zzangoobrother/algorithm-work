# K번째 큰수
1~100 사이 자연수가 적힌 N장의 카드, 같은 숫자의 카드가 여러장 있을 수 있습니다.
이 중 3장을 뽑아 적힌 수를 합한 값의 모든 경우의 수 중 K번째로 큰 수를 출력

- java
```java
import java.util.*

public class algorithm {
  public static void main(String[] args) {
    Scanner in=new Scanner(System.in);
    int input1 = in.nextInt();
    int input2 = in.nextInt();
    
    int[] arr = new int[input1];
    for (int i = 0; i < input1; i++) {
    	arr[i] = in.nextInt();
    }
    
    Set<Integer> tempSet = new TreeSet<>(Collections.reverseOrder());
    int sum;
    for (int i = 0; i < input1; i++) {
    	for (int j = i + 1; j < input1; j++) {
    		for (int k = j + 1; k < input1; k++) {
    			sum = arr[i] + arr[j] + arr[k];
    			tempSet.add(sum);
    		}
    	}
    }
    
    int cnt = 0;
    int result = -1;
    for (int x : tempSet) {
    	cnt++;
    	if (cnt == input2) {
    		result = x;
    		break;
    	}
    }
  }
}
```

- python
```python
input1 = input().strip().split(' ')
input2 = input().strip().split(' ')

total = int(input1[0])
partCount = int(input1[1])

tempSet = set()
for i in range(0, total):
    for j in range(i + 1, total):
        for k in range(j + 1, total):
            tempSet.add(int(input2[i]) + int(input2[j]) + int(input2[k]))

resultSet = sorted(tempSet, reverse=True)

cnt = 0
result = -1
for i in resultSet:
    cnt += 1

    if cnt == partCount:
        result = i
        break

print(result)
```
