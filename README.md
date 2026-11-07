# StudentSkills

A high-performance suite of modular agent skills for Claude, Claude Code, Cursor, and Antigravity, engineered specifically for students, competitive programmers, and exam-takers.

Built to eliminate AI slop, optimize context windows, and enforce rigorous active recall.

---

## The Skills

### 1. `exam-code`
*Brevity, anti-slop, and comment-free code protocol for tests, exams, and coding assessments.*

- **Zero-Comment Enforcement**: Completely bans AI comment clutter (`// initialize x`, `/* helper */`). Clean, minimal, readable code only.
- **Shortest Working Form**: Standard library only. No bloated enterprise patterns, no factory classes, no unnecessary imports.
- **On-Demand Breakdown (`explain`)**: Dissects code line-by-line in plain English on command, detailing why each line exists and the exact questions examiners ask in vivas or interviews.
- **Modes**: `code` (default raw output), `explain` (line-by-line viva breakdown), `complexity` (time/space mathematical proofs).

### 2. `syllabus-master`
*Adaptive active-recall and syllabus mastery engine for dense PDFs and exam outlines.*

- **Context-Compressor**: Strips bureaucratic filler from large syllabi and textbook outlines, generating an indexed topic matrix that saves up to 80% of prompt tokens while retaining 100% of testable knowledge.
- **Technique Diagnostics**: Evaluates the student across 4 proven cognitive learning protocols (Feynman Technique, Active Recall, Pomodoro Drills, Analogy Anchoring) and locks in the technique yielding the highest retention.
- **The 4-Tier Exam Ladder**: Drills topics through 4 rigorous difficulty tiers:
  - *Tier 1*: Foundation (Direct Concept & MCQ)
  - *Tier 2*: Intermediate (Applied Scenarios & Problems)
  - *Tier 3*: Advanced (Common Exam Traps & Edge Cases)
  - *Tier 4*: University Exam Synthesis (Multi-concept long questions)
- **Persistent Coverage Ledger**: Tracks mastery across every subtopic until 100% of the syllabus is cleared.

---

## Installation

### Method 1: Claude Code CLI (`.agents/skills`)

Clone or copy the skills directly into your global or project `.agents` directory:

```bash
# In your project root
git clone https://github.com/HadesIsOff/student-skills.git .agents/student-skills
```

Or copy individual skills:
```bash
mkdir -p .agents/skills
cp -r student-skills/skills/* .agents/skills/
```

Claude Code will automatically discover and load the skills whenever your request matches their trigger descriptions.

---

### Method 2: Claude Web App & Desktop

1. Open **Claude** (`claude.ai` or desktop app).
2. Go to **Settings** -> **Capabilities** -> Ensure **Code Execution** is enabled.
3. Open **Customize** -> **Skills**.
4. Click **Add Skill**, name it (e.g. `exam-code`), and paste the full contents of `skills/exam-code/SKILL.md`.
5. Repeat for `syllabus-master`.

---

### Method 3: Antigravity / Cursor / Windsurf

Drop the skill directories into your workspace skills directory:
```bash
.gemini/skills/
├── exam-code/
│   └── SKILL.md
└── syllabus-master/
    └── SKILL.md
```

---

## Usage Examples

### Using `exam-code`

**Prompt:**
> Write a function in Python that finds the length of the longest subarray with sum equal to k. /exam

**Response:**
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
```text
Complexity: O(N) time | O(N) space
Constraints Handled: Negative numbers, zero sum, empty match.
```

**Follow-up Prompt:**
> explain

**Response:**
```text
Line 2: seen = {0: -1}
- What it does: Initializes a hash map storing prefix sums mapped to their earliest index.
- Why it is there: Needed so subarrays starting from index 0 can be measured accurately.
- Examiner Tip: Expect to be asked why the initial value is -1 instead of 0.
...
```

---

### Using `syllabus-master`

**Prompt:**
> Here is my Operating Systems syllabus: [paste syllabus or PDF text]. Help me study for midterms.

**Response:**
```text
============================================================
SYLLABUS COMPRESSION COMPLETE
============================================================
MODULE 1: Processes & Threads (Topics 1.1 - 1.4)
MODULE 2: CPU Scheduling & Synchronization (Topics 2.1 - 2.5)
MODULE 3: Deadlocks & Memory Management (Topics 3.1 - 3.4)

============================================================
COGNITIVE DIAGNOSTIC
============================================================
Before we drill, let us identify your highest-retention learning technique:
1. Feynman Technique (Teach-back & gap discovery)
2. Active Recall (Closed-book rapid retrieval)
3. Pomodoro Drill Cycles (20m sprint + 5m quiz)
4. Analogy Anchoring (Physical world mappings)

To calibrate your baseline, solve this 1-minute question on Topic 1.1:
What is the fundamental difference between a Process Control Block (PCB) 
and a Thread Control Block (TCB) in terms of memory sharing?
```

---

## Repository Structure

```text
student-skills/
├── skills/
│   ├── exam-code/
│   │   ├── SKILL.md                 # Core exam code playbook
│   │   └── reference/
│   │       └── clean-idioms.md      # Language-specific exam snippets
│   └── syllabus-master/
│       ├── SKILL.md                 # Active recall & syllabus engine
│       └── reference/
│           └── techniques.md        # Cognitive protocol guidelines
├── LICENSE                          # MIT License
└── README.md                        # Documentation
```

---

## License

MIT License. Free to use, modify, and distribute.
