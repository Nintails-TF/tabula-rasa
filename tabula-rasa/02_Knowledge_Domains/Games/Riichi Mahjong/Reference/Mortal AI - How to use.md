---
date created: Monday, January 26th 2026, 7:09:07 pm
date modified: Monday, January 26th 2026, 7:10:49 pm
---

# Mortal AI Analysis Interpretation Guide

A practical reference for understanding Mortal's review output when analysing your riichi mahjong games.

---

## The Core Metrics

### Q Value (Expected Ranking Points)

The Q value estimates how many **ranking points (pt)** you can expect to gain or lose from a given action. Mortal uses the Tenhou houou pt distribution [+90, +45, 0, -135] as its baseline.

|Q Value|Interpretation|
|---|---|
|Positive|Action expected to gain ranking points|
|Near zero|Roughly neutral expected value|
|Negative|Action expected to lose ranking points|

**Key insight:** Q values for non-optimal moves may be imprecise. Mortal is optimized for _playing_,not for providing exact EV calculations on every possible action.

---

### P Value (Policy Probability)

The P value shows Mortal's **confidence** that each action is correct, expressed as a percentage. All P values for a decision sum to 100%.

|P Value|Interpretation|
|---|---|
|> 90%|Mortal considers this the obvious/only choice|
|50–90%|Clear preference, but alternatives have some merit|
|20–50%|Close decision, multiple reasonable options|
|< 20%|Mortal considers this suboptimal|
|< 5%|Mortal considers this a clear mistake|

**Key insight:** When the top choice has very high P (>90%) and you picked something with <5%, Mortal saw something you missed—worth investigating.

---

## Evaluating Your Mistakes

### Q Difference Scale

Compare your move's Q value to Mortal's recommended move:

|Q Difference|Severity|What It Means|
|---|---|---|
|< 0.1 pt|Negligible|Essentially equivalent moves|
|0.1 – 0.3 pt|Minor|Small inaccuracy, don't stress|
|0.3 – 1.0 pt|Notable|Worth understanding why|
|1.0 – 3.0 pt|Significant|Clear error, study this spot|
|> 3.0 pt|Major|Game-impacting mistake|

### Context Matters

The same Q difference can mean different things:
- **Early hand, no pressure:** A 0.5 pt mistake is just tile efficiency error
- **All-last, close scores:** A 0.5 pt mistake might cost you a placement
- **Against riichi:** Defensive errors can have huge swings

---

## Combining Q and P for Analysis

|Your P|Q Difference|Interpretation|
|---|---|---|
|High (>30%)|Small (<0.3)|Reasonable alternative, close decision|
|High (>30%)|Large (>0.5)|Your move was defensible but costly|
|Low (<5%)|Small (<0.3)|Mortal disagrees but stakes were low|
|Low (<5%)|Large (>0.5)|Clear mistake—prioritize studying this|

---

## Red Flags to Watch For

### Patterns That Indicate Leaks
- **Consistently low P on your riichi timing:** You may be declaring too early/late
- **Defensive cuts with high Q loss:** Your danger tile reading needs work
- **Calling decisions with big Q swings:** Review your melding judgment
- **All-last mistakes:** Placement logic may need study
### When to Ignore Mortal
- **Q difference < 0.1:** Genuinely doesn't matter
- **Multiple moves at similar P (20-40% each):** Close decisions, trust your read
- **Mortal makes "inhuman" plays:** Sometimes optimal play looks weird

---

## Understanding the Limitations

### What Mortal Doesn't Know
- Your opponents' skill levels or tendencies
- Historical patterns from specific players
- Tournament/league-specific considerations
- Psychological factors

### Technical Limitations
- Mortal is model-free: it can't "search" like chess engines
- Q values for bad moves may be inaccurate (they're not the optimization target)
- Trained on Tenhou data—may not perfectly match Mahjong Soul or Riichi City meta

---

## Practical Review Workflow

1. **First pass:** Note any move where your P < 5% and Q difference > 0.3
2. **Categorize:** Is it tile efficiency? Defense? Calling? Push/fold?
3. **Understand:** Before accepting Mortal's answer, try to figure out _why_
4. **Pattern match:** Do you make this type of mistake often?
5. **Accept variance:** Some "mistakes" are table reads that didn't pan out

---

## Quick Reference Card

```
Q DIFFERENCE          P VALUE (YOUR MOVE)
< 0.1  → Ignore       > 30% → Reasonable
0.1-0.3 → Minor       5-30% → Questionable  
0.3-1.0 → Notable     < 5%  → Mistake
> 1.0  → Serious      < 1%  → Blunder

PRIORITY = High Q difference + Low P value
```

---

## Final Notes

Mortal is a training tool, not a judge. Its goal is to help you identify patterns in your play that cost you ranking points over time. A single "mistake" means little—what matters is whether you're making the same type of mistake repeatedly.

Don't chase 100% accuracy. Even pros don't match Mortal perfectly, and some human reads are valid even when Mortal disagrees. Use Mortal to find your _leaks_, not to become a bot.