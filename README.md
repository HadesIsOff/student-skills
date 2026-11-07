# StudentSkills

A high-performance suite of modular agent skills for Claude, Claude Code, Cursor, and Antigravity, engineered specifically for students, competitive programmers, and exam-takers.

Built to eliminate AI slop, optimize context windows, and enforce rigorous active recall.

---

## The Skills

### 1. `exam-code` (v1.1.0)
*Brevity, anti-slop, and comment-free code protocol for tests, exams, and coding assessments.*

- **Zero-Comment Default**: Completely bans inline comment clutter (`// initialize counter`, `# loop through`). Output is pure, minimal code ready for test portals.
- **Viva Armor Protocol**: On-demand oral examination defense script. Details the top trap questions examiners ask, complexity proofs, and the exact verbal responses students should recite.
- **Anti-AI Fingerprint Enforcement**: Eliminates robotic LLM tells (overly defensive null checks, weird naming, generic helper functions) to produce authentic, human student code.
- **Multilingual Support**: Tailored exam idioms for **Python, C++, Java, C, JavaScript/TypeScript, and SQL**.
- **Modes**: `code` (default raw output), `explain` (line-by-line breakdown), `viva` (oral defense script), `complexity` (time/space mathematical proofs).
- **References**:
  - [`reference/viva-armor.md`](skills/exam-code/reference/viva-armor.md) - Oral exam and viva voce defense templates.
  - [`reference/anti-ai-fingerprint.md`](skills/exam-code/reference/anti-ai-fingerprint.md) - Rules for human student code authenticity.
  - [`reference/multilingual-idioms.md`](skills/exam-code/reference/multilingual-idioms.md) - Fast I/O and standard-library templates.

### 2. `syllabus-master` (v1.1.0)
*Adaptive active-recall and syllabus mastery engine for dense PDFs and exam outlines.*

- **100 Evidence-Based Cognitive Techniques**: Houses an encyclopedic reference of 100 learning protocols with researcher citations (Dunlosky, Ebbinghaus, Feynman, Sweller, Leitner, Bjork, Ausubel, Paivio).
- **Domain-Aware Routing**: Automatically detects whether a syllabus is STEM, Medical/Bio, Law/Humanities, or Language/Vocab, and pairs it with the optimal cognitive protocol.
- **Context-Compressor**: Strips bureaucratic filler from large syllabi and textbook outlines, generating an indexed topic matrix that saves up to 80% of prompt tokens while retaining 100% of testable knowledge.
- **The 4-Tier Exam Ladder**: Drills topics through 4 rigorous difficulty tiers:
  - *Tier 1*: Foundation (Direct Concept & MCQ)
  - *Tier 2*: Intermediate (Applied Scenarios & Problems)
  - *Tier 3*: Advanced (Common Exam Traps & Edge Cases)
  - *Tier 4*: University Exam Synthesis (Multi-concept long questions)
- **Live Mastery Ledger**: Maintains a persistent ASCII checklist (`[X] Mastered`, `[>] In-Progress`, `[ ] Pending`) until the entire syllabus is cleared.
- **References**:
  - [`reference/100-cognitive-techniques.md`](skills/syllabus-master/reference/100-cognitive-techniques.md) - Complete catalog of 100 learning techniques.
  - [`reference/techniques.md`](skills/syllabus-master/reference/techniques.md) - Detailed execution rules for core protocols.

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
> /exam viva

**Response:**
```text
============================================================
VIVA ARMOR: DEFENSE PLAYBOOK
============================================================
1. Examiner: "Why use a hash map instead of checking all subarrays?"
   Your Answer: "Checking all subarrays requires O(N^2) time with two loops. 
   Using a prefix sum hash map achieves O(N) linear time with a single pass."

2. Examiner: "Why is seen[0] initialized to -1?"
   Your Answer: "To handle the boundary condition where a valid subarray 
   starts at index 0. Without -1, any prefix sum exactly matching k from 
   the start would calculate index - 0 = index instead of index + 1."
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
COGNITIVE DIAGNOSTIC (Domain: STEM / Systems)
============================================================
Recommended Protocol: #43 Faded Worked Examples + #31 Inversion Testing.

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
│   │   ├── SKILL.md                          # Core exam code & viva playbook
│   │   └── reference/
│   │       ├── clean-idioms.md               # Clean language snippets
│   │       ├── viva-armor.md                 # Oral exam defense scripts
│   │       ├── anti-ai-fingerprint.md        # Authentic student style guide
│   │       └── multilingual-idioms.md        # Python, C++, Java, C, JS, SQL
│   └── syllabus-master/
│       ├── SKILL.md                          # Active recall & syllabus engine
│       └── reference/
│           ├── 100-cognitive-techniques.md   # Comprehensive 100-technique library
│           └── techniques.md                 # Core protocol guidelines
├── LICENSE                                   # MIT License
└── README.md                                 # Documentation
```

---

## License

MIT License. Free to use, modify, and distribute.
