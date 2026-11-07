# Clean Exam Idioms Reference

Reference patterns for writing minimal, comment-free exam code across major languages.

---

## 1. Two-Pointer & Sliding Window (Python)

```python
def maxSubArrayLen(nums, k):
    seen = {0: -1}
    cur, ans = 0, 0
    for i, x in enumerate(nums):
        cur += x
        if cur - k in seen:
            ans = max(ans, i - seen[cur - k])
        if cur not in seen:
            seen[cur] = i
    return ans
```

---

## 2. Fast I/O & Graph BFS (C++)

```cpp
#include <bits/stdc++.h>
using namespace std;

int shortestPath(int n, vector<vector<int>>& edges, int src, int dst) {
    vector<vector<int>> adj(n);
    for (auto& e : edges) adj[e[0]].push_back(e[1]);
    vector<int> dist(n, -1);
    queue<int> q;
    dist[src] = 0;
    q.push(src);
    while (!q.empty()) {
        int u = q.front(); q.pop();
        if (u == dst) return dist[u];
        for (int v : adj[u]) {
            if (dist[v] == -1) {
                dist[v] = dist[u] + 1;
                q.push(v);
            }
        }
    }
    return -1;
}
```

---

## 3. Dynamic Programming Table Compression (Java)

```java
import java.util.*;

public class Knapsack {
    public static int solve(int W, int[] wt, int[] val, int n) {
        int[] dp = new int[W + 1];
        for (int i = 0; i < n; i++) {
            for (int w = W; w >= wt[i]; w--) {
                dp[w] = Math.max(dp[w], dp[w - wt[i]] + val[i]);
            }
        }
        return dp[W];
    }
}
```
