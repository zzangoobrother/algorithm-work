## ATM

문제 : https://www.acmicpc.net/problem/11399

작은 시간 오름차순으로 풀이를 하면 답을 구할 수 있다.

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;
import java.util.Scanner;

public class Main {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);

    int count = sc.nextInt();
    List<Atm> atms = new ArrayList<>();
    for (int i = 1; i <= count; i++) {
      atms.add(new Atm(i, sc.nextInt()));
    }

    Collections.sort(atms, new Comparator<Atm>() {
      @Override
      public int compare(Atm o1, Atm o2) {
        if (o1.time > o2. time) {
          return 1;
        } else if (o1.time < o2.time) {
          return -1;
        }

        return 0;
      }
    });

    int answer = 0;
    int temp = 0;
    for (Atm atm : atms) {
      temp += atm.time;
      answer += temp + atm.time;
    }

    System.out.println(answer - temp);
  }

  static class Atm {
    private int order;
    private int time;

    public Atm(int order, int time) {
      this.order = order;
      this.time = time;
    }
  }
}
```
