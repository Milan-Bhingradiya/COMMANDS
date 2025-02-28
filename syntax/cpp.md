# C++ Syntax Notes for DSA

## 1. Input & Output

```cpp
#include <iostream>
using namespace std;

int main() {
    int x;
    cin >> x;  // Input
    cout << x << endl;  // Output
    return 0;
}
```

## 2. Data Types & Variable Declaration

```cpp
int a = 10;
float b = 10.5;
double c = 20.99;
char d = 'A';
bool e = true;
long long f = 10000000000;
```

## 3. Control Structures

### If-Else
```cpp
if (x > 0) {
    cout << "Positive";
} else if (x < 0) {
    cout << "Negative";
} else {
    cout << "Zero";
}
```

### Loops
#### For Loop
```cpp
for (int i = 0; i < 5; i++) {
    cout << i << " ";
}
```

#### While Loop
```cpp
int i = 0;
while (i < 5) {
    cout << i << " ";
    i++;
}
```

#### Do-While Loop
```cpp
int i = 0;
do {
    cout << i << " ";
    i++;
} while (i < 5);
```

## 4. Functions

```cpp
int add(int a, int b) {
    return a + b;
}
```

## 5. Arrays

```cpp
int arr[5] = {1, 2, 3, 4, 5};
```

## 6. Vectors (Dynamic Array)

```cpp
#include <vector>
vector<int> v = {1, 2, 3};
v.push_back(4);
v.pop_back();
```

## 7. Strings

```cpp
#include <string>
string s = "Hello";
s += " World";
cout << s;  // Output: Hello World
```

## 8. Pairs

```cpp
#include <utility>
pair<int, string> p = {1, "abc"};
cout << p.first << " " << p.second;
```

## 9. Maps

```cpp
#include <map>
map<int, string> m;
m[1] = "One";
m[2] = "Two";
```

## 10. Sets

```cpp
#include <set>
set<int> s;
s.insert(1);
s.insert(2);
```

## 11. Stacks & Queues

### Stack
```cpp
#include <stack>
stack<int> st;
st.push(1);
st.push(2);
st.pop();
```

### Queue
```cpp
#include <queue>
queue<int> q;
q.push(1);
q.push(2);
q.pop();
```

## 12. Priority Queue (Heap)

```cpp
priority_queue<int> pq;  // Max-Heap\pq.push(10);
pq.push(20);
pq.pop();
```

## 13. Linked List (Singly)

```cpp
struct Node {
    int data;
    Node* next;
};
```

## 14. Recursion

```cpp
int factorial(int n) {
    if (n == 0) return 1;
    return n * factorial(n - 1);
}
```

## 15. Sorting (STL)

```cpp
#include <algorithm>
vector<int> v = {3, 1, 4, 1, 5};
sort(v.begin(), v.end());
```

## 16. Binary Search (STL)

```cpp
bool exists = binary_search(v.begin(), v.end(), 3);
```

## 17. Graph Representation

### Adjacency List
```cpp
vector<int> adj[100];
adj[1].push_back(2);
adj[2].push_back(1);
```

### Adjacency Matrix
```cpp
int adj[100][100];
adj[1][2] = 1;
adj[2][1] = 1;
```

## 18. BFS & DFS

### BFS
```cpp
#include <queue>
void bfs(int start) {
    queue<int> q;
    q.push(start);
    while (!q.empty()) {
        int node = q.front();
        q.pop();
        // Process node
    }
}
```

### DFS
```cpp
void dfs(int node) {
    // Process node
    for (int neighbor : adj[node]) {
        dfs(neighbor);
    }
}
```

