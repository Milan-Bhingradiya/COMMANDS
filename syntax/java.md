# Java Syntax Notes for DSA

## 1. Input & Output

```java
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int x = sc.nextInt();  // Input
        System.out.println(x);  // Output
        sc.close();
    }
}
```

## 2. Data Types & Variable Declaration

```java
int a = 10;
float b = 10.5f;
double c = 20.99;
char d = 'A';
boolean e = true;
long f = 10000000000L;
```

## 3. Control Structures

### If-Else
```java
if (x > 0) {
    System.out.println("Positive");
} else if (x < 0) {
    System.out.println("Negative");
} else {
    System.out.println("Zero");
}
```

### Loops
#### For Loop
```java
for (int i = 0; i < 5; i++) {
    System.out.print(i + " ");
}
```

#### While Loop
```java
int i = 0;
while (i < 5) {
    System.out.print(i + " ");
    i++;
}
```

## 4. Functions (Methods)

```java
int add(int a, int b) {
    return a + b;
}
```

## 5. Arrays

```java
int[] arr = {1, 2, 3, 4, 5};
```

## 6. ArrayList (Dynamic Array)

```java
import java.util.*;
ArrayList<Integer> list = new ArrayList<>();
list.add(1);
list.add(2);
list.remove(0);
```

## 7. Strings

```java
String s = "Hello";
s += " World";
System.out.println(s);  // Output: Hello World
```

## 8. HashMap (Dictionary)

```java
import java.util.*;
HashMap<Integer, String> map = new HashMap<>();
map.put(1, "One");
map.put(2, "Two");
```

## 9. HashSet (Set)

```java
import java.util.*;
HashSet<Integer> set = new HashSet<>();
set.add(1);
set.add(2);
```

## 10. Stack & Queue

### Stack
```java
import java.util.*;
Stack<Integer> stack = new Stack<>();
stack.push(1);
stack.push(2);
stack.pop();
```

### Queue
```java
import java.util.*;
Queue<Integer> queue = new LinkedList<>();
queue.add(1);
queue.add(2);
queue.poll();
```

## 11. Priority Queue (Heap)

```java
import java.util.*;
PriorityQueue<Integer> pq = new PriorityQueue<>(); // Min-Heap
pq.add(10);
pq.add(20);
pq.poll();
```

## 12. Linked List (Singly)

```java
class Node {
    int data;
    Node next;
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}
```

## 13. Recursion

```java
int factorial(int n) {
    if (n == 0) return 1;
    return n * factorial(n - 1);
}
```

## 14. Sorting (Built-in)

```java
import java.util.*;
Arrays.sort(arr);
```

## 15. Binary Search

```java
import java.util.*;
int index = Arrays.binarySearch(arr, 3);
boolean exists = index >= 0;
```

## 16. Graph Representation

### Adjacency List
```java
import java.util.*;
ArrayList<Integer>[] adj = new ArrayList[100];
for (int i = 0; i < 100; i++) adj[i] = new ArrayList<>();
adj[1].add(2);
adj[2].add(1);
```

### Adjacency Matrix
```java
int[][] adj = new int[100][100];
adj[1][2] = 1;
adj[2][1] = 1;
```

## 17. BFS & DFS

### BFS
```java
import java.util.*;
void bfs(int start) {
    Queue<Integer> q = new LinkedList<>();
    q.add(start);
    while (!q.isEmpty()) {
        int node = q.poll();
        // Process node
    }
}
```

### DFS
```java
void dfs(int node, boolean[] visited) {
    if (visited[node]) return;
    visited[node] = true;
    for (int neighbor : adj[node]) {
        dfs(neighbor, visited);
    }
}
```

