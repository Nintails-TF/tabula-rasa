---
date created: Sunday, February 22nd 2026, 2:12:27 pm
date modified: Thursday, February 26th 2026, 4:49:42 pm
Time Budget: 5/20
---

# Description


## Question 1 — Conceptual Model (25 marks)

**What's actually needed:**

- **(a)** Table of candidate classes from the NSC scenario — keep/reject with reasons. Then a final list. (5 marks)
- **(b)** 200-word critical evaluation of the class identification guidance — did it work well, did you need to adapt it? (5 marks)
- **(c)** Class diagram (conceptual model) — classes + associations, no attributes/multiplicities yet. Upload to ShareSpace. (7 marks)
- **(d)** Comment on 2 peers' diagrams (~150 words each). (4 marks)
- **(e)** Update your model based on peer feedback, explain changes (~150 words). (4 marks)

**Time estimate:** ~4–5 hours. The candidate class table is methodical work. The diagram itself isn't huge — it's the NSC domain you already know from TMA 01. The peer review is time-dependent (you need to wait for feedback), so upload ASAP even if it's not 2 weeks early.

---

## Question 2 — Analysis Model (20 marks)

**What's actually needed:**

- **(a)** Take your Q1 diagram, add **attributes and multiplicities**. (10 marks)
- **(b)** Extend the model for the new "citizen science seed trials" scenario — new classes, attributes, associations with multiplicities. (6 marks)
- **(c)** Describe 2 OCL-style constraints (one for the main scenario, one for the extension) and justify them. (4 marks)

**Time estimate:** ~3–4 hours. Part (a) builds directly on Q1. Part (b) is a small extension — read it carefully, it gives you GPS coordinates, planting records, weekly observations, and a "max 10 plantings" constraint. Part (c) is short written work.

---

## Question 3 — Behaviour Model / Sequence Diagrams (18 marks)

**What's actually needed:**

- **(a)(i)** Write OCL-style pre/postconditions for `orderSeed` operation. (5 marks)
- **(a)(ii)** Draw **two** sequence diagrams — one fork pattern, one cascade pattern — for the same postcondition. (6 marks)
- **(a)(iii)** Evaluate both against the **Law of Demeter** — which violates it and why. (3 marks)
- **(b)** Describe 2 kinds of changes a sequence diagram might suggest for the class model. (4 marks)

**Time estimate:** ~3–4 hours. The operation specification is the tricky part — get the pre/postconditions precise. The two sequence diagrams are fairly mechanical once you understand fork vs cascade. The Law of Demeter question is a short theoretical answer (fork typically violates it).

---

## Question 4 — Design Strategies (17 marks)

**What's actually needed:**

- **(a)** Apply 3 strategies (central class, actor classes, use-case-as-class) to the `orderSeed` use case. For each: extra class needed? What operation and where? First message and target object? (10 marks)
- **(b)(i)** Explain why passing object references is better than passing data like names. (4 marks)
- **(b)(ii)** Identify when passing data is the only option. (3 marks)

**Time estimate:** ~2–3 hours. This is mostly written explanation with small diagrams. The 3 strategies are covered in Unit 7 — apply them systematically to the NSC case.

---

## Question 5 — State Machine (20 marks)

**What's actually needed:**

- **(a)** List all states from Box 1's plant life cycle. (4 marks)
- **(b)** Draw a state machine diagram with transitions, guards, and timing. (12 marks)
- **(c)** Suggest 2 forms of change the state machine might reveal for the class diagram. (4 marks)

**Time estimate:** ~2–3 hours. Read Box 1 carefully — the states are: Seed → Seedling → Adult → Flowering → Fruiting/Seed → Dead, plus termination conditions (failed germination, frost, pest attack). The diagram needs `after()` timing events and guard conditions.

---

## Total Time Estimate

|Question|Estimated Time|
|---|---|
|Q1 (conceptual model + peer review)|4–5 hrs|
|Q2 (analysis model + extension)|3–4 hrs|
|Q3 (operation spec + sequence diagrams)|3–4 hrs|
|Q4 (design strategies)|2–3 hrs|
|Q5 (state machine)|2–3 hrs|
|**Total**|**~14–19 hours**|

Realistically, budget **around 16–20 hours** including formatting, screenshots, and revisions. Given it's due the 25th and you need peer interaction for Q1, I'd prioritise getting Q1(c) uploaded today or tomorrow, then work through Q2–Q5 while waiting for feedback, and circle back to Q1(d)/(e) last.

Want me to help you start on any specific question?