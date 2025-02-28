# Python Syntax Notes for DSA

## 1. Input & Output

```python
x = int(input())  # Input
print(x)  # Output
```

## 2. Data Types & Variable Declaration

```python
a = 10  # int
b = 10.5  # float
c = 20.99  # float
d = 'A'  # char (string in Python)
e = True  # bool
f = 10000000000  # int (long in C++)
```

## 3. Control Structures

### If-Else
```python
if x > 0:
    print("Positive")
elif x < 0:
    print("Negative")
else:
    print("Zero")
```

### Loops
#### For Loop
```python
for i in range(5):
    print(i, end=' ')
```

#### While Loop
```python
i = 0
while i < 5:
    print(i, end=' ')
    i += 1
```

## 4. Functions

```python
def add(a, b):
    return a + b
```

## 5. Lists (Dynamic Arrays)

```python
arr = [1, 2, 3, 4, 5]
```

## 6. Tuples (Immutable Lists)

```python
tup = (1, 2, 3)
```

## 7. Strings

```python
s = "Hello"
s += " World"
print(s)  # Output: Hello World
```

## 8. Dictionaries (Maps)

```python
d = {1: "One", 2: "Two"}
```

## 9. Sets

```python
s = {1, 2, 3}
```

## 10. Stacks & Queues

### Stack
```python
stack = []
stack.append(1)
stack.append(2)
stack.pop()
```

### Queue
```python
from collections import deque
queue = deque()
queue.append(1)
queue.append(2)
queue.popleft()
```

## 11. Priority Queue (Heap)

```python
import heapq
pq = []
heapq.heappush(pq, 10)
heapq.heappush(pq, 20)
heapq.heappop(pq)
```

## 12. Linked List (Singly)

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
```

## 13. Recursion

```python
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n - 1)
```

## 14. Sorting (Built-in)

```python
arr.sort()
```

## 15. Binary Search

```python
import bisect
exists = bisect.bisect_left(arr, 3) < len(arr) and arr[bisect.bisect_left(arr, 3)] == 3
```

## 16. Graph Representation

### Adjacency List
```python
adj = [[] for _ in range(100)]
adj[1].append(2)
adj[2].append(1)
```

### Adjacency Matrix
```python
adj = [[0] * 100 for _ in range(100)]
adj[1][2] = 1
adj[2][1] = 1
```

## 17. BFS & DFS

### BFS
```python
from collections import deque
def bfs(start):
    q = deque([start])
    while q:
        node = q.popleft()
        # Process node
```

### DFS
```python
def dfs(node, visited=set()):
    if node in visited:
        return
    visited.add(node)
    for neighbor in adj[node]:
        dfs(neighbor, visited)
```

