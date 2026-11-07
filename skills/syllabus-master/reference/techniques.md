# Cognitive Learning Protocols Reference

Detailed breakdown of the 4 learning techniques implemented in `syllabus-master`.

---

## 1. The Feynman Protocol

- **Step 1: The Simplified Teach-Back**
  The student explains the target concept in plain, simple English without using any technical buzzwords or jargon.
- **Step 2: Gap Identification**
  The coach identifies where the student uses hand-waving, vague metaphors, or circular definitions.
- **Step 3: Surgical Refinement**
  The student revisits the core principle to eliminate the discovered gap until the explanation is crystal clear to a beginner.

---

## 2. Active Retrieval Practice

- **Step 1: Stimulus Prompt**
  Present a question requiring direct recall of a formula, definition, or algorithmic step without multiple-choice crutches.
- **Step 2: Effortful Retrieval**
  The student produces the response entirely from memory.
- **Step 3: Immediate Calibration**
  Compare response against the exact canonical rubric. If incorrect, schedule the question for re-testing after 2 intervening concepts.

---

## 3. Pomodoro Drill Cycles

- **Structure**: 20 minutes focused acquisition $\to$ 5 minutes active recall test $\to$ 5 minutes rest.
- **Execution**:
  - Minutes 0-20: Rapid traversal of 2 interconnected subtopics.
  - Minutes 20-25: 4-question speed test (Tiers 1 & 2).
  - Minutes 25-30: Rest interval / mental reset.

---

## 4. Analogy Anchoring

- **Structure**: Abstract mathematical/logical system $\to$ Concrete mechanical analogy $\to$ Formalization.
- **Example**:
  - Abstract: Mutual Exclusion (Mutex) vs Semaphore.
  - Analogy: Bathroom key (Mutex = 1 key, single occupant) vs Restaurant table buzzers (Semaphore = counting permits for $N$ diners).
  - Formalization: Invariant proofs, code implementation, deadlocks.
