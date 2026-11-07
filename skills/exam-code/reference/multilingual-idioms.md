# Multilingual Minimal Exam Idioms

High-performance, minimal-complexity implementation templates across primary exam and interview languages.

---

## 1. Python (3.x)

### Fast I/O & Template
```python
import sys

def solve():
    lines = sys.stdin.read().split()
    if not lines:
        return
    n = int(lines[0])
    arr = list(map(int, lines[1:n+1]))
    # Core logic
    ans = sum(arr)
    print(ans)

if __name__ == '__main__':
    solve()
```

### Essential Stdlib Shortcuts
- Frequency map: `from collections import Counter; cnt = Counter(arr)`
- Default values: `from collections import defaultdict; d = defaultdict(int)`
- Min-Heap: `import heapq; heapq.heapify(h); heapq.heappush(h, val); x = heapq.heappop(h)`
- Binary search: `import bisect; idx = bisect.bisect_left(arr, target)`

---

## 2. C++ (C++17 / C++20)

### Minimal Competitive & Lab Exam Template
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    cin.tie(NULL)->sync_with_stdio(false);
    int n;
    if (!(cin >> n)) return 0;
    vector<int> a(n);
    for (int &x : a) cin >> x;
    
    long long ans = 0;
    for (int x : a) ans += x;
    cout << ans << "\n";
    return 0;
}
```

### Invariants & Traps
- Always use `\n` instead of `endl` to prevent stream buffer flushing timeouts.
- Use `long long` for sums to prevent 32-bit overflow ($> 2 \times 10^9$).
- Use `vector<vector<int>>` for dynamic 2D tables to avoid raw pointer segmentation faults.

---

## 3. Java (17+)

### Single-File Exam Template
```java
import java.io.*;
import java.util.*;

public class Solution {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String line = br.readLine();
        if (line == null || line.trim().isEmpty()) return;
        
        int n = Integer.parseInt(line.trim());
        int[] arr = new int[n];
        StringTokenizer st = new StringTokenizer(br.readLine());
        for (int i = 0; i < n; i++) arr[i] = Integer.parseInt(st.nextToken());
        
        long ans = 0;
        for (int x : arr) ans += x;
        System.out.println(ans);
    }
}
```

### Invariants & Traps
- Use primitive `int[]` instead of `ArrayList<Integer>` when size is fixed to avoid boxing/unboxing overhead.
- Handle potential `NullPointerException` on `br.readLine()`.

---

## 4. C (C99 / C11)

### Minimal Exam / Lab Practical Template
```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    int n;
    if (scanf("%d", &n) != 1) return 0;
    
    int *arr = (int *)malloc(n * sizeof(int));
    if (!arr) return 1;
    
    long long sum = 0;
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
        sum += arr[i];
    }
    
    printf("%lld\n", sum);
    free(arr);
    return 0;
}
```

---

## 5. JavaScript / TypeScript

### Minimal LeetCode & Node Template
```javascript
function solve(arr) {
    if (!arr.length) return 0;
    const seen = new Map();
    let ans = 0;
    for (let i = 0; i < arr.length; i++) {
        ans = Math.max(ans, arr[i]);
    }
    return ans;
}
```

---

## 6. SQL (ANSI-Standard)

### Canonical Interview Patterns
```sql
-- Pattern: N-th Highest Salary / Deduplicated Window
WITH Ranked AS (
    SELECT id, salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS rnk
    FROM Employees
)
SELECT salary FROM Ranked WHERE rnk = 2;

-- Pattern: Self-Join / Consecutive Active Records
SELECT DISTINCT a.num AS ConsecutiveNums
FROM Logs a
JOIN Logs b ON a.id = b.id - 1 AND a.num = b.num
JOIN Logs c ON a.id = c.id - 2 AND a.num = c.num;
```
