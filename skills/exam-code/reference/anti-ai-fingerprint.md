# Anti-AI Fingerprint Guide // Writing Authentic Human Student Code

Automated academic plagiarism checkers (MOSS, Copyleaks, Turnitin) and human evaluators scan for telltale signatures produced by standard LLMs. This guide enforces rules to ensure all generated code looks like authentic, high-performing human student code.

---

## 1. Telltale AI Signatures (What Gets Caught)

| AI Tell | Why It Flags Evaluators | The Human Student Rule |
| :--- | :--- | :--- |
| **Comments on Every Line** | Real students never write `// initialize counter variable` or `# return the maximum value`. | **ZERO comments by default.** Let clean variable names and logic speak. |
| **Enterprise Variable Names** | `accumulatedTotalSumCount`, `temporaryIndexPointer`, `resultMapData`. | **Idiomatic brevity:** `n`, `arr`, `ans`, `res`, `dp`, `cur`, `seen`. |
| **Defensive Over-Engineering** | 15 lines of null-checks, `if (!arr) return;`, custom exceptions on trusted input. | **Trust constraints:** If $1 \le N \le 10^5$, don't check for $N = -50$. |
| **Unused Parameter Boilerplate** | Adding `args`, `kwargs`, unused context parameters, or generic docstrings. | **Surgical focus:** Accept only what the problem statement specifies. |
| **Robotic Helper Extraction** | Creating 4 tiny single-line helper functions (`isEven()`, `calculateValue()`). | **Inline the logic:** Direct expressions inside the loop. |
| **Polite Introductory Fluff** | *"Sure! Here is the C++ implementation of the problem:"* | **Zero chatter:** Start immediately with `#include` or `def`. |

---

## 2. Structural Authenticity Checklist

- [ ] **No Academic Docstrings**: Never include `@param`, `@return`, `@author`, or Sphinx docstrings in exam solutions unless explicitly demanded.
- [ ] **Idiomatic Language Shortcuts**:
  - Python: Use list comprehensions (`[x for x in nums if x > 0]`), tuple unpacking (`a, b = b, a`), and `dict.get()`.
  - C++: Use `auto`, range-based for loops (`for (int x : nums)`), and `emplace_back()`.
  - Java: Use standard `for (int i = 0; i < n; i++)`, `Arrays.sort()`, and primitive arrays where possible.
- [ ] **Realistic Spacing**: Standard 2 or 4-space indentation without weird multi-line wrapping of simple conditions.
- [ ] **Single-File Execution**: All code must fit in a single self-contained script or class that compiles immediately without external file dependencies.
