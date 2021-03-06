# 그래프 최단거리 (BFS)
정점의 수 N과 간선의 수 M이 주어지고, 연결정보가 입력으로
주어질 때 1번 부터 각 정점으로 가는 최소 간선수 출력

- tree 레벨로 간선수 구하기
```java
import java.util.*

public class algorithm {
  static int[][] arr;
  static Map<Integer, Integer> result = new TreeMap<>();
  
  public static void main(String[] args) {
    Scanner in=new Scanner(System.in);
    int input1 = in.nextInt();
    int input2 = in.nextInt();
    
    arr = new int[input1+ 1][input1+ 1];
    for (int i = 0; i < input2; i++) {
    	int a = in.nextInt();
    	int b = in.nextInt();
    	arr[a][b] = 1;
    }
    
    bfs(1, input1);
		
    for (int x : result.keySet()) {
    	System.out.println(x + " : " + result.get(x));
    }
  }
  
  public static void bfs(int v, int input1) {
      Queue<Integer> queue = new LinkedList<>();
      queue.offer(v);
      int level = 0;
      while (!queue.isEmpty()) {
      	int len = queue.size();
      	for (int i = 0; i < len; i++) {
      	   int cur = queue.poll();
      	   for (int j = 1; j <= input1; j++) {
      	      if (arr[cur][j] == 1) {
      	      	if (!result.containsKey(j)) {
      	      		result.put(j, level+1);
      	      		queue.offer(j);
      	      	}
      	      	if (result.size() == (input1 - 1)) {
      	      		return;
      	      	}
      	      }
      	   }
      	}
      	level++;
      }
  }
}
```

- 인접리스트와 배열 이용하여 구하기
```java
import java.util.*

public class algorithm {
    static List<List<Integer>> graph;
    static int[] check, dis;
	
    public static void main(String[] args) {
    	Scanner in=new Scanner(System.in);
	int input1 = in.nextInt();
	int input2 = in.nextInt();
	
	graph = new ArrayList<>();
	for (int i = 0; i <= input1; i++) {
		graph.add(new ArrayList<>());
	}
		
	check = new int[input1+1];
	dis = new int[input1+1];
	for (int i = 0; i < input2; i++) {
		int a = in.nextInt();
		int b = in.nextInt();
		graph.get(a).add(b);
	}
		
	bfs(1);
	for (int i = 2; i <= input1; i++) {
		System.out.println(i + " : " + dis[i]);
	}
    }
    
    public static void bfs(int v) {
	Queue<Integer> queue = new LinkedList<>();
	check[v] = 1;
	dis[v] = 0;
	queue.offer(v);
	while (!queue.isEmpty()) {
		int cv = queue.poll();
		for (int x : graph.get(cv)) {
			if (check[x] == 0) {
				check[x] = 1;
				queue.offer(x);
				dis[x] = dis[cv]+1;
			}
		}
	}
    }
}
```
