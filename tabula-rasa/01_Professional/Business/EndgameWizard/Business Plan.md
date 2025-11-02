---
date created: Tuesday, October 7th 2025, 10:52:12 am
date modified: Friday, October 10th 2025, 3:01:42 pm
Reminder: Update this as the project evolves.
---

# EndgameWizard Business Plan

## 1. Concept Overview

EndgameWizard is a gamified web app that makes chess endgame training actually fun. Using daily gauntlets with varied difficulty and time controls, the platform solves a simple problem: **players lose won endgames because endgame training is boring, so they don't practice it.**

The goal is to create an addictive daily habit around endgame improvement - something players _want_ to do, not something they know they _should_ do.

**Brand:** EndgameWizard  
**Tagline:** "The fun way to stop losing won endgames"  
**Domain:** endgamewizard.com (secured)

---

## 2. Problem & Opportunity

**The Core Problem:**
- Club players frequently lose won endgames due to poor technique
- Endgame training feels dry, theoretical, and boring
- Players avoid practicing endgames even though they know it's important
- Current platforms (Chess.com, Lichess) offer endgame puzzles but without focused, engaging structure

**Key Insight from User Research:**
- Chess club players prefer simple, accessible interfaces (like Lichess)
- Most players have little interest in "perfect" tablebase play or deep theory
- What they want: practical improvement through fun, bite-sized practice
- The pain point is behavioural, not educational

**The Opportunity:** Build a niche product focused entirely on making endgame practice addictive through gamification, variety, and smart session design.

---

## 3. Value Proposition

**Core Promise:** Master chess endgames in 10 minutes a day without it feeling like homework

**What Makes It Different:**

- **Variety-driven sessions:** Mix of blitz (timed/easy) and slower (untimed/hard) positions keeps it fresh
	- Give options for either blitz only or untimed only. But give bonus points to those who choose the multi-path.
		- Don't want to force players who prefer blitzing things out to play slow, don't want to force slow players to stress. But the uncertainty of the gauntlet should improve engagement.
- **Daily Gauntlet structure:** 5-10 curated positions with clear progression and instant feedback
	- See Noctie, look at what they do with their square highlighting.
- **Gamification that works:** Streaks, levels, wizard-themed progression (Apprentice → Master)
	- A streak for the daily gauntlet. Can have a leaderboard globally and with friends, see who got the most correct, who did it the quickest, etc.
- **Respects player time:** Sessions designed for 5-15 minutes, not hour-long study
- **Purpose-built:** Entire experience optimized for endgame training specifically, not tactics. 
	- Other websites do this already and do this better. (Chess.com / Lichess.org - Puzzle Rush, huge sets of tactics)

---

## 4. Core Feature: The Daily Gauntlet

The heart of EndgameWizard is the Daily Gauntlet - a curated set of 5-10 endgame positions designed for optimal engagement.

**Structure:**
1. **Warm-up (2-3 positions):** Timed, easy, build momentum
    - Example: "Win K+Q vs K in 45 seconds"
2. **Main Challenges (3-5 positions):** Medium difficulty, untimed
    - Example: "Convert this won pawn endgame"
3. **Boss Position (1 position):** Hard, optional, for mastery
    - Example: "Master challenge: Draw this tricky Rook endgame"

**Why This Works:**
- Starts easy to build confidence and momentum
- Variety prevents monotony (players don't know what's coming)
- Natural difficulty curve within each session
- Completable in one sitting (satisfying)
- Optional hard challenge for motivated players

**Variety Across Days:**
- Mixed days (default)
- Sprint days (all timed, pure speed)
- Precision days (all untimed, deep thinking)
- Theme days (e.g., "Rook Endgame Tuesday")

---

## 5. Target Users

**Primary:** Club players (1200-2000 rating) who:
- Know openings and tactics but struggle with endgame technique
- Want to improve but find traditional endgame study boring
- Play regularly online (Lichess, Chess.com)
- Value their time (looking for efficient practice)

**Secondary:**
- Serious improvers who want structured endgame training
- Chess coaches looking for tools to assign to students
- Tournament players wanting to shore up a weakness

**Initial Test Group:**
- Local chess club in Dumfries and Galloway
- Online chess communities (Reddit r/chess, Discord servers)

---

## 6. Business Model (Future)

**Phase 1 (First 6 months):** Free MVP

- Focus entirely on product-market fit
- Gather feedback and iterate rapidly
- Build waitlist and community

**Phase 2 (6-12 months):** Freemium Model

- Free tier: Daily gauntlet with basic positions
- Premium tier (£5-8/month):
    - Advanced gauntlets (more positions, adaptive difficulty - e.g. instead of participating in a global daily gauntlet, they get their own gauntlet that is customized for their strengths/weaknesses)
    - Progress analytics and insights
    - Custom training modes
    - Ad-free experience

**Alternative Revenue Streams (Future):**
- One-time endgame training packs (£10-20 per theme)
	- Rook endgames, Pawn endgames, Rook and minor endgames, etc.
- Coaching partnerships (white-label for chess schools)
- B2B licensing for chess platforms

**Key Principle:** Don't monetize until retention is proven. If players aren't coming back day 3-7, pricing doesn't matter.

---

## 7. Go-to-Market Strategy

**Phase 1: Local Validation (Weeks 1-8)**
- Beta test with Dumfries and Galloway chess club
	- Travel to local chess tournaments, talk to people about it, show them it and hand out cards or flyers.
- Gather face-to-face feedback and iterate
- Aim for 10-20 active daily users

**Phase 2: Online Communities (Months 2-4)**

- Share on Reddit r/chess (cautiously - community is sceptical of promotion)
- Post in chess Discord servers
- Reach out to chess streamers for feedback (not sponsorship yet)
- Create content: "Why you're losing won endgames (and how to fix it)"

**Phase 3: Influencer Validation (Months 4-6)**

- Offer free premium access to chess content creators for honest reviews
- Targets: Smaller streamers first (GothamChess, Anna Cramling tier is later)
- Focus on educational chess creators who value tools

**Phase 4: Organic Growth (Months 6+)**

- SEO: Target "endgame training," "chess endgame practice," etc.
- User referrals: "Challenge a friend" features
- Community-driven growth through club partnerships

**Marketing Principles:**

- Product quality over marketing spend
- Word of mouth from satisfied users
- Focus on retention metrics, not vanity metrics

---

## 8. Development & Technology

**Builder:** Solo developer (3rd year comp sci student)  
**Timeline:** 8 weeks to MVP (~60 hours)  
**Budget:** ~£50 (domain + potential API costs)

**Tech Stack:**

- Frontend: React + Tailwind CSS + react-chessboard
- Backend: Node.js/Express or Python/Flask
- Database: PostgreSQL
- Chess Logic: chess.js library
- Engine: Lichess API (free) or Stockfish
- Hosting: Vercel (frontend) + Railway/Render (backend)
- Domain: endgamewizard.com

**Development Approach:**

- Ship rough MVP in 8 weeks
- Iterate based on real user feedback
- Keep architecture simple (no premature optimization)
- Focus on core loop: can we make people come back daily?

**Potential Academic Angle:**

- Could become final year project
- Research component: "Gamification effectiveness in chess skill acquisition"
- Access to university resources (cloud credits, servers)

---

## 9. Success Metrics

**MVP Success (First 3 months):**

- 50+ beta signups
- 20+ daily active users
- 40%+ day-3 retention (users come back after trying it)
- 20%+ day-7 retention (users make it a habit)
- Average session length: 8-12 minutes

**Product-Market Fit Indicators:**

- Users asking "when can I pay for this?"
- Unprompted social media posts/reviews
- Users completing 7+ day streaks
- Organic word-of-mouth growth

**Vanity Metrics to Ignore (Initially):**

- Total signups (retention matters more)
- Social media followers
- Press coverage

---

## 10. Risks & Mitigation

**Risk: Players don't find it fun enough**
- Mitigation: Extensive playtesting with club before launch
- Mitigation: Rapid iteration based on retention data
- Early warning: If day-3 retention < 30%, core loop needs rework

**Risk: Too niche - not enough market**
- Mitigation: Start hyper-focused (endgame specialists), expand later
- Mitigation: If club players won't use it, pivot or kill quickly
- Validation: 50+ interested users before building too much

**Risk: Larger platforms copy the idea**
- Mitigation: Speed and focus are advantages
- Mitigation: Superior UX for this specific use case
- Reality: If Chess.com copies you, you validated demand

**Risk: Technical complexity (tablebases, position generation)**
- Mitigation: Start with handcrafted positions (100+ gets you months of content)
- Mitigation: Use Lichess API to avoid infrastructure costs
- Mitigation: Add sophisticated features only after retention proven

**Risk: Student time constraints (exams, coursework)**
- Mitigation: Scope kept minimal for MVP
- Mitigation: Low/no ongoing costs if development pauses
- Mitigation: Can resume development during breaks

---

## 11. Vision & Roadmap

**Short-term (0-6 months): Validate & Iterate**

- Build MVP with daily gauntlet feature
- Test with local club (10-20 users)
- Achieve 30%+ day-7 retention
- Expand to 100+ active users through online communities

**Medium-term (6-18 months): Scale & Monetize**

- Launch freemium model
- Add adaptive difficulty and progress analytics
- Build mobile-responsive version (web app, not native)
- Reach 1,000+ active users
- Generate first revenue

**Long-term (18+ months): Become the Endgame Standard**
- Position as "the Duolingo of chess endgames"
- Partner with chess coaches and clubs
- Expand feature set based on proven user demand
- Potential: White-label for larger platforms
- Potential: Acquisition target for Chess.com or Lichess

**Success Definition:** If EndgameWizard becomes the first app club players recommend when someone asks "how do I get better at endgames," we've won.

---

## 12. Why This Will Work

**The convergence:**

- Real problem that affects most improving players
- Solution that's genuinely differentiated (fun > perfection)
- Builder with domain expertise (chess player + developer)
- Low risk, low cost, high learning opportunity
- Built-in test audience (local chess club)
- Timing: Chess has seen massive growth post-pandemic

**The key insight:** Endgame training isn't an information problem (plenty of books/videos exist). It's a motivation problem. Make practice addictive, and players will improve themselves.

**The moat:** Session design and gamification are hard to copy. Chess.com could clone the features, but not easily replicate a purpose-built, well-designed experience for this specific use case.

---

## Next Steps (Week 1)

1. ✅ Secure endgamewizard.com domain
2. Create landing page with email signup
3. Set up development environment and GitHub repo
4. Build simplest possible proof of concept (one position with timer)
5. Show prototype to 3 club members for initial feedback
6. Begin 8-week development sprint

**The goal isn't perfection. The goal is to ship something players will use tomorrow.**