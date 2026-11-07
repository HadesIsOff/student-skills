# Viva Armor // The Oral Exam & Interview Defense Protocol

In lab practicals, university examinations, and technical interviews, writing the code is only 50% of the grade. The other 50% is surviving the **Viva Voce / Oral Grilling**, where examiners probe for genuine understanding and search for signs of cheating or AI copy-pasting.

This guide provides the defense playbook for defending minimal exam code under pressure.

---

## 1. The 5 Core Examiner Trap Questions

### Question 1: "Why did you use this data structure instead of [Alternative]?"
- **Example**: Using a Hash Map (`unordered_map` / `dict`) vs an Array.
- **The Armor**:
  - Never answer: *"Because it was easier."*
  - Answer with Time/Space trade-offs: *"I chose a hash table because lookups and insertions operate in $O(1)$ average time, giving us overall $O(N)$ runtime. An array would require $O(N)$ linear scans for each lookup, pushing total time complexity to $O(N^2)$."*

### Question 2: "What is the exact time and space complexity, and where is the bottleneck?"
- **The Armor**:
  - Break it down by loop iterations and memory allocations:
    - *"The outer loop runs $N$ times, and the inner two-pointer loop advances at most $N$ times across the entire function, so the time is strictly $O(N)$, not $O(N^2)$."*
    - *"Auxiliary space is $O(1)$ because we mutate pointers in-place without allocating dynamic arrays or recursion stack frames."*

### Question 3: "What happens if the input is [Edge Case]?"
- **Standard Edge Cases**:
  - Empty input / $N = 0$.
  - All identical elements (e.g., `[1, 1, 1, 1]`).
  - Negative values or zero.
  - Large values causing 32-bit integer overflow ($> 2 \times 10^9$).
- **The Armor**:
  - Point to the exact guard line in your code:
    - *"If $N = 0$, line 2 immediately evaluates to false and returns 0 without entering the loop, preventing an index out-of-bounds error."*
    - *"For large values, we declared the accumulator as `long long` (or `long` in Java), which handles up to $\approx 9 \times 10^{18}$ without overflow."*

### Question 4: "Can you optimize this further?"
- **The Armor**:
  - If already optimal: *"This problem has a theoretical lower bound of $\Omega(N)$ because any correct algorithm must inspect every element at least once. Since our algorithm runs in $O(N)$ time and $O(1)$ auxiliary space, it is asymptotically optimal."*
  - If a trade-off exists: *"We could reduce time from $O(N \log N)$ to $O(N)$ by using a counting sort or frequency hash map, but that would sacrifice space complexity from $O(1)$ to $O(K)$."*

### Question 5: "Walk me through this line of code with a trace table."
- **The Armor**:
  - Pick a tiny concrete sample (e.g., `arr = [3, 1, 4]`) and trace variables step-by-step:
    - Iteration 0: `i = 0, x = 3, cur = 3, ans = 3`
    - Iteration 1: `i = 1, x = 1, cur = 4, ans = 4`
    - Iteration 2: `i = 2, x = 4, cur = 8, ans = 8`

---

## 2. Line-by-Line Defense Breakdown Template

When the user requests `explain` or `viva`, output this exact structured defense card:

```text
============================================================
VIVA ARMOR: LINE-BY-LINE DEFENSE BREAKDOWN
============================================================
Line [X]: <code snippet>
  - Mechanism: Plain English explanation of the operation.
  - Justification: Why this exact primitive was chosen over alternatives.
  - Examiner Question: "Why didn't you use X here?"
  - Perfect Answer: Concise verbal defense citing complexity or edge cases.
```
