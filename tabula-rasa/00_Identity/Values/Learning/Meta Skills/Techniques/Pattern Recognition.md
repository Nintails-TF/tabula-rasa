---
date created: Saturday, March 14th 2026, 2:36:06 pm
date modified: Saturday, March 14th 2026, 3:00:50 pm
Parent Link:
  - "[[../Index#Techniques/Pattern Recognition Pattern Recognition|Index - Pattern Recognition]]"
---

# Pattern Recognition

---
## Reasoning:

The ability to see structure, regularity, and recurring dynamics across situations — often before you can articulate why. This is what people mean when they say someone has "good instincts" or "intuition," but it isn't magic. It's the result of extensive exposure to a domain combined with the deliberate habit of noticing similarities, extracting principles, and building mental models. Pattern recognition is what lets an experienced analyst look at network logs and sense something is wrong before they've consciously identified the anomaly, or what lets a seasoned investor spot a familiar setup unfolding in a new market. It bridges the gap between raw knowledge and practical wisdom — the ability to see this situation as an instance of something you've encountered before, and act accordingly.

---

## Sources:

**Foundational Texts:**
- _Sources of Power: How People Make Decisions_ — Gary Klein. The definitive work on how experts actually make decisions under pressure, based on studies of firefighters, nurses, military commanders. The recognition-primed decision model is fundamentally about pattern recognition — experts don't analytically compare options, they recognise the situation and act. Essential reading.
- _Thinking, Fast and Slow_ — Kahneman. The counterweight to Klein. System 1 is the brain's pattern-matching engine — fast, automatic, usually right in familiar domains, dangerously wrong when patterns are superficial or the domain is unpredictable. Reading Klein and Kahneman together gives you the complete picture: when to trust pattern recognition and when to override it.
- _The Model Thinker_ — Scott Page. Introduces the idea of using multiple models rather than one — lattice thinking. Each model is a pattern-recognition lens, and real insight comes from seeing which models apply to a given situation and where they conflict.

**For understanding how expertise builds pattern recognition:**
- _Peak: Secrets from the New Science of Expertise_ — Anders Ericsson & Robert Pool. Deliberate practice builds mental representations — which are essentially refined pattern libraries. This book explains the mechanism by which experience becomes expertise rather than just repetition.
- _Streetlights and Shadows: Searching for the Keys to Adaptive Decision Making_ — Gary Klein. Follow-up to Sources of Power, more focused on how pattern recognition works in messy real-world environments versus controlled ones. Good on the limits and failure modes.
- _Range: Why Generalists Triumph in a Specialized World_ — David Epstein. The case for cross-domain pattern recognition. Breadth of experience creates the ability to see analogies between distant fields — "this network security problem has the same structure as that epidemiology problem." Specialists see deep patterns; generalists see wide ones. Both matter.

**For building mental models and frameworks:**
- _Poor Charlie's Almanack_ — Charlie Munger's collected talks. The "latticework of mental models" idea originates here. Munger's argument is that the most powerful thinking comes from having patterns from multiple disciplines — psychology, physics, economics, biology — and recognising where they apply.
- _The Great Mental Models_ series — Shane Parrish / Farnam Street. More accessible than Munger, organises mental models into volumes by type. Good reference for expanding your library of patterns to match against.
- _An Introduction to General Systems Thinking_ — Gerald Weinberg. Older but foundational. Teaches you to see systems-level patterns — feedback loops, leverage points, emergent behaviour — that recur across wildly different domains.

**Domain-specific pattern recognition:**
- Chess literature — de Groot's studies, Chase & Simon's chunking research. The original research showing that expert pattern recognition in chess is about recognising meaningful configurations, not calculating further ahead. Directly applicable to understanding how domain expertise works.
- _The Visual Display of Quantitative Information_ — Edward Tufte. Teaches you to see patterns in data through visualisation. Not just about making charts — about training your eye to detect signal in noise.
- MITRE ATT&CK framework documentation. In cybersecurity specifically, this is a codified pattern library — common adversary tactics, techniques, and procedures organised so you can recognise them when they appear. Studying it is literally building a pattern vocabulary.

---

## Techniques:

**Building your pattern library:**
- Expose yourself to large volumes of cases in your domain. There is no shortcut here. Pattern recognition requires a base of experience to match against. Read incident reports, case studies, post-mortems, historical analyses. Every case you study is a pattern deposited in memory that might fire in a future situation. The analysts who've read hundreds of breach reports see things the analyst who's read ten cannot.
- Study the same phenomenon across multiple instances. Don't just read one case of a supply chain attack — read twenty. The features that repeat are the pattern. The features that vary are the context. Your brain will start doing this sorting automatically, but only after sufficient exposure.
- Learn across domains deliberately. Many of the most powerful pattern recognitions are cross-domain — seeing that network propagation follows the same dynamics as epidemics, or that organisational failure modes mirror engineering failure modes. Read outside your field with the explicit intention of finding structural parallels.
- Build and maintain a personal library of mental models. Not by memorising a list but by encountering a model, understanding it deeply, and then actively looking for it in the world. Once you understand feedback loops, you start seeing them everywhere — in security incidents, in team dynamics, in market behaviour. Each model is a pattern template.

**Training the recognition itself:**
- Practice with deliberate variation. If you always see the same type of problem in the same format, you build brittle patterns that only fire in familiar contexts. Deliberately vary the surface features while keeping the deep structure. In security, this means studying the same TTP executed by different actors against different targets — the surface differs, the pattern holds.
- Do post-event analysis with a focus on what you recognised and what you missed. After any significant event — an incident, a project, a decision — ask: what patterns did I see in advance, what did I only see in retrospect, and what should I have seen but didn't. This is how you tune your recognition system.
- Use comparison and analogy actively. When you encounter a new situation, make a deliberate habit of asking "what does this remind me of?" and "where have I seen this structure before?" Don't wait for the analogy to appear — hunt for it. Even forced analogies that turn out to be wrong teach you something about the structure of the current situation.
- Play pattern-rich games and puzzles. Chess, Go, bridge, poker — these build domain-specific pattern recognition, but the meta-skill of pattern recognition itself transfers to some degree. The habit of looking for structure, evaluating positions, recognising configurations — these are trainable dispositions.

**Refining and pressure-testing your patterns:**
- Distinguish signal from noise deliberately. Not every regularity is a meaningful pattern. Some are coincidence, some are artefacts of how you're looking. The discipline is asking: "Is this pattern real or am I imposing it?" Especially watch for patterns you want to find — confirmation bias is the enemy of accurate pattern recognition.
- Track your pattern hits and misses. When you act on a recognised pattern, note whether the prediction held. Over time, this builds calibration — you learn which of your patterns are reliable and which are unreliable. Without tracking, you'll remember your hits and forget your misses, and your confidence will outrun your accuracy.
- Seek out the exceptions and anomalies. When something doesn't fit a pattern you expect, don't dismiss it — investigate it. Anomalies are either noise, which is fine, or they're evidence that your pattern is wrong or incomplete, which is invaluable. The best pattern recognisers are the ones who pay the most attention to what doesn't fit.
- Update your patterns continuously. A pattern that was valid five years ago may not be valid now. Threat actor behaviours evolve, markets shift, technologies change. Pattern recognition is not a static library — it requires active maintenance. Periodically revisit your assumptions about how things work and check them against current evidence.

**Using pattern recognition wisely:**
- Know the difference between pattern matching and analysis. Recognition is fast and powerful but it can be wrong, especially in novel situations or when the surface features are misleading. Use it as a starting hypothesis, not a conclusion. "This looks like X" should be followed by "let me check whether it actually is X."
- Be especially cautious with patterns across low-validity domains. In chess, firefighting, and well-structured technical problems, expert pattern recognition is remarkably accurate. In stock markets, long-range political prediction, and complex social dynamics, it's much less reliable. Know which kind of domain you're operating in.
- Combine pattern recognition with systematic analysis. The best performance in most fields comes from using intuitive pattern recognition to generate hypotheses quickly and then using analytical thinking to verify them. Neither alone is as powerful as both together.

---

## Application:

**Cybersecurity.** The entire field runs on pattern recognition at multiple levels. Recognising known attack signatures in logs, seeing the behavioural pattern of lateral movement across systems, identifying social engineering attempts that follow familiar scripts, spotting the indicators that a "minor" alert is actually the edge of something larger. The MITRE ATT&CK framework is explicitly a pattern taxonomy. Threat hunting is pattern recognition applied proactively — looking for known adversary patterns in environments where no alert has fired.

**Technical troubleshooting and debugging.** Experienced engineers don't trace every problem from first principles. They recognise the pattern — "this looks like a race condition," "this failure profile matches a memory leak," "this is the same thing that happened when we changed the DNS configuration last year." The pattern fires, they check it, and they solve in minutes what a less experienced person would spend hours on.

**Strategic thinking and planning.** Recognising recurring dynamics — market cycles, organisational growth patterns, competitive plays, geopolitical patterns — allows you to anticipate rather than merely react. The strategist who has studied enough cases to recognise "this is the classic pattern of overextension" or "this looks like the early phase of consolidation" can position ahead of events.

**Medical diagnosis.** Expert diagnosticians are pattern recognisers — they match symptom constellations against thousands of cases they've encountered or studied. The classic "spot diagnosis" where a physician recognises a rare condition at a glance is pattern recognition in its purest form. Diagnostic errors often trace to pattern-matching failures — the wrong pattern was triggered, or the right pattern wasn't in the library.

**Reading people and situations.** Social pattern recognition — noticing that someone's behaviour matches a familiar pattern of disengagement, that a negotiation is following a predictable trajectory, that a team dynamic is heading toward a known failure mode. This is what people mean by "emotional intelligence" in many cases — it's pattern recognition applied to human behaviour, built from experience and attention.

**Creative and innovative work.** Creativity often comes from recognising a pattern in one domain and applying it in another — seeing that a biological process could solve an engineering problem, or that a narrative structure from literature could organise a presentation. The broader your pattern library, the more combinatorial possibilities are available to you. Innovation is frequently recombination, and recombination requires recognition.

---