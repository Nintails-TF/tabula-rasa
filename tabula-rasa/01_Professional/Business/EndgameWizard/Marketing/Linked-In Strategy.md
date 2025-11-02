---
date created: Sunday, October 12th 2025, 3:09:37 pm
date modified: Sunday, October 12th 2025, 3:18:28 pm
---

# LinkedIn Content Delivery Guide: EndgameWizard Build Journey

## Overview

**Goal:** Build professional presence and demonstrate technical + product skills through documenting your 8-week MVP build journey.

**Target Audience:** Recruiters, hiring managers, founders, fellow developers, tech companies.

**Posting Cadence:** 1 substantial post per week (Sundays work well for visibility) + 3-5 thoughtful comments throughout the week.

**Duration:** 8 weeks of primary content + ongoing career-building content.

---

## Pre-Launch: Profile Optimization

Add your live EndgameWizard link when deployed
Consider adding a PDF case study later

---

## 8-Week Content Calendar

### Week 1: Launch Post - "Why I'm Building This"

**Posting Day:** Sunday (Week 1)

**Post Structure:**

```
Hook (attention grabber)
↓
Problem identification
↓
Your insight/solution
↓
What you're building
↓
Call to action
```

**Example Post:**

```
I've lost count of how many won chess games I've thrown away in the endgame. Turns out, I'm not alone.

After talking to players at my local chess club in Dumfries, people know they should practice endgames, but they don't because it's boring. As the masters have said:

"To improve at chess you should in the first instance study the endgame." - J.R Capablanca

The problem isn't information - there are countless books and videos. The problem is motivation and putting the fun in learning.

So I'm building EndgameWizard: a gamified daily training app that makes endgame practice actually fun. Think Duolingo for chess endgames.

🎯 Goal: MVP in 8 weeks
📚 Tech stack: React, Node.js, PostgreSQL
👥 Beta group: Local chess club (10-20 players)

I'll be documenting the entire journey here - the wins, the bugs, the lessons learned, and everything in between. 

This weeks deliverable: Deployment and a functional chessboard with move validation.

If you've built an MVP before, what's one thing you wish you'd known before starting?

#webdev #mvp #react #nodejs
```

**Why This Works:**
- Personal story (relatable)
- Clear problem statement
- Concrete goals and metrics
- Invites engagement with a question
- Sets expectations for future posts

---

### Week 2: "Technical Decisions & Trade-offs"

**Posting Day:** Sunday (Week 2)

**Focus:** Show your technical decision-making process

**Example Post:**

```
Week 2 of building EndgameWizard: Why I chose boring tech over the latest trends.

I had a choice: build this with the newest, shiniest frameworks or stick with proven, stable tools.

I went boring. Here's why:

React instead of Svelte
→ Massive ecosystem, easier to find solutions when stuck
→ More relevant for job applications
→ I need to ship in 8 weeks, not learn new syntax

Node/Express instead of Go/Rust
→ JavaScript across the stack = faster context switching
→ Rich libraries for chess logic (chess.js)
→ Every deployment platform supports it

PostgreSQL instead of MongoDB
→ Chess data is inherently relational (users, games, positions)
→ Easy to query for analytics later
→ ACID compliance for score/streak tracking

Vercel/Railway instead of AWS
→ Zero config deployment
→ Free tier is generous
→ I want to build product, not manage infrastructure

The lesson: At MVP stage, familiarity > novelty. Ship first, optimize later.

Current progress: ✅ Auth working, ⏳ Building chess board component this week

What's your "boring" tech stack that just works?

[Include screenshot of your tech stack diagram]

#webdevelopment #mvp #techstack #react #nodejs
```

---

### Week 3: "First User Feedback"

**Posting Day:** Sunday (Week 3)

**Focus:** User research and iteration

**Example Post:**

```
I showed my chess app to 3 real users yesterday. It went... differently than expected.

What I thought they'd want: Adaptive difficulty, AI opponents, detailed analytics.

What they actually wanted: "Just make it fast and simple."

Key feedback that's changing my approach:

1️⃣ "Don't make me create an account on day 1"
→ Adding guest mode - accounts only when they want to save progress

2️⃣ "The timer is stressful on hard positions"
→ Making timed positions optional, adding practice mode

3️⃣ "I want to know WHY I got it wrong"
→ Adding solution explanations (not just win/loss)

4️⃣ "This is just like Chess.com puzzles"
→ Emphasizing the daily gauntlet structure and streak system more clearly

The biggest surprise: One player said "I'd come back every day just to keep my streak alive." That's the behaviour I'm trying to create.

This is why you talk to users early. What I think is important ≠ what users actually care about.

Next: Implementing guest mode and improving the feedback system.

What's the most unexpected feedback you've gotten that changed your product?

[Include photo from user testing session or screenshot of feedback notes]

#productdevelopment #userfeedback #mvp #buildinpublic
```

---

### Week 4: "Solving a Specific Technical Challenge"

**Posting Day:** Sunday (Week 4)

**Focus:** Technical problem-solving and learning

**Example Post:**

````
Spent 6 hours debugging why chess positions weren't saving. The solution was embarrassingly simple.

The problem:
Users complete positions, see "Correct!" message, but when they come back the next day, their progress is gone.

What I tried:
✅ Checked database logs - writes were succeeding
✅ Verified JWT tokens - auth was working
✅ Tested API endpoints - all returning 200
❌ Still broken

The breakthrough:
I console.logged the actual database query. The date comparison was off by one day due to timezone handling.

My code:
```javascript
// ❌ This was wrong
const today = new Date().toISOString().split('T')[0]
// Returns date in UTC, but user is in GMT

// ✅ The fix
const today = new Date().toLocaleDateString('en-CA') // 'en-CA' gives YYYY-MM-DD
````

The lesson: When something seems impossible, log EVERYTHING. The bug is usually in something you assumed was working.

Secondary lesson: Timezones are harder than you think. Always think about timezone handling upfront.

Progress update: Core gameplay loop is working! Users can now complete the daily gauntlet and their streaks are saved correctly.

What's your "I can't believe that was the bug" story?

[Include before/after screenshots or code snippet]

#coding #debugging #webdev #javascript #learnprogramming

```

---

### Week 5: "Metrics & Early Traction"

**Posting Day:** Sunday (Week 5)

**Focus:** Product metrics and learnings

**Example Post:**

```

Week 5 Update: 12 beta users. Here's what the data is showing.

After launching to my local chess club, I'm tracking 3 metrics:

- Day-1 retention (did they come back?)
- Day-3 retention (is it habit-forming?)
- Session length (are they engaged?)

The numbers so far:

📊 Day-1 retention: 75% (9/12 users came back) 📊 Day-3 retention: 50% (6/12 users - target is 40%+) 📊 Avg session: 8.5 minutes (target: 8-12 min) 📊 Streak leader: 11 days (this person is hooked!)

What's working: ✅ The "easy → hard" progression keeps users engaged ✅ Daily streaks are driving habit formation ✅ Quick sessions respect busy schedules

What's not working: ❌ 3 users stopped after day 2 - exit survey says "too difficult" ❌ Some confusion about timed vs untimed positions ❌ Mobile experience needs work (60% use mobile)

Next steps:

1. Add difficulty selection (beginner/intermediate/advanced)
2. Better onboarding explaining the position types
3. Mobile UI improvements

The insight: 50% day-3 retention at this stage isn't bad, but I need 20 users to see clear patterns. Focusing on getting more beta testers this week.

If you've launched a beta, what early metrics surprised you?

[Include chart/graph of retention data]

#productmetrics #startup #mvp #buildinpublic #analytics

```

---

### Week 6: "Learning from Failure"

**Posting Day:** Sunday (Week 6)

**Focus:** Honest reflection on what's not working

**Example Post:**

```

I built a feature nobody wanted. Here's what I learned.

Last week I added a "leaderboard" showing who solved the most positions. Spent 12 hours on it.

Usage after 7 days: 2 people clicked it. Once. Total.

Why it flopped:

1️⃣ Wrong motivation → Chess players want to improve, not compete with strangers → I assumed gamification = leaderboards → Streaks matter (personal progress), rankings don't

2️⃣ Built without asking → I thought "this would be cool" instead of "users need this" → No validation before building → Classic founder mistake

3️⃣ Solving the wrong problem → Users were asking for better mobile experience → I built what was fun for me to code, not what they needed

The fix: Removing global leaderboard. Adding friend-only streak comparison (opt-in). Spending those 12 hours on mobile improvements instead.

The lesson: "What would be cool?" is the wrong question. "What problem does this solve?" is the right one.

Paul Graham says: "Make something people want." Not "Make something and hope people want it."

Still learning. Still shipping.

What's a feature you built that nobody used?

#productdevelopment #startup #failforward #buildinpublic #learning

```

---

### Week 7: "Deployment & Going Live"

**Posting Day:** Sunday (Week 7)

**Focus:** Technical achievement + what's next

**Example Post:**

```

EndgameWizard is live. Here's what it took to get from localhost to production.

🔗 endgamewizard.com (link in comments)

8 weeks ago this was just an idea. Today it's a working web app with 18 active users maintaining daily streaks.

The deployment stack:

- Frontend: Vercel (automatic deploys from GitHub)
- Backend: Railway (Node.js + PostgreSQL)
- Domain: Namecheap
- SSL: Auto-provisioned
- Total cost: £10 for the domain

Biggest deployment challenges:

1️⃣ Environment variables → Development vs production configs → Solution: .env files + Railway dashboard

2️⃣ Database migrations → Local data structure ≠ production → Solution: Prisma migrations + careful testing

3️⃣ CORS issues → Frontend couldn't talk to backend initially → Solution: Proper origin whitelisting

4️⃣ Mobile responsiveness → Looked great on laptop, broken on phones → Solution: Tailwind breakpoints + real device testing

Current stats: ✅ 18 active users ✅ 45% day-7 retention ✅ 94% uptime (one outage when I broke the DB) ✅ Average session: 9.2 minutes

What's next:

- Gathering feedback for 2 more weeks
- Deciding if this becomes my final year project
- Potentially expanding to more chess clubs

For those who've deployed their first full-stack app: what caught you off guard?

[Include screenshot of the live app + deployment dashboard]

#deployment #webdev #mvp #fullstack #buildinpublic

```

---

### Week 8: "8-Week Retrospective"

**Posting Day:** Sunday (Week 8)

**Focus:** Complete journey, lessons learned, what's next

**Example Post:**

```

8 weeks. One app. Here's everything I learned building EndgameWizard from scratch.

The Goal: Build a chess training app that makes endgame practice fun The Result: 22 daily active users, 45% day-7 retention, deployed and running

What went right: ✅ Talked to users before writing code ✅ Kept scope ruthlessly minimal ✅ Shipped rough and iterated fast ✅ Tracked metrics from day 1 ✅ Documented the journey publicly

What went wrong: ❌ Wasted time on features users didn't want ❌ Underestimated mobile usage (60% of traffic) ❌ Ignored edge cases that broke in production ❌ Should have deployed earlier (waited until week 7)

The biggest lessons:

1️⃣ Shipping beats perfecting → Week 4 version was "embarrassing" but taught me more than weeks of planning

2️⃣ Users don't care about your tech stack → They care if it works and solves their problem → React vs Svelte? Irrelevant. Fast vs slow? Critical.

3️⃣ Metrics tell the real story → "Users love it!" means nothing → "45% come back after 7 days" means everything

4️⃣ The best feedback comes from watching, not asking → User interviews: "This is great!" → Usage data: 3 features never clicked

5️⃣ Building in public = accountability → Knowing I'd post weekly kept me shipping → Comments here solved 2 technical problems

What's next:

- Finalizing decision on final year project
- Expanding beta to online chess communities
- Open to junior developer roles - learning from this build confirmed I want to work in product development

The complete tech stack, GitHub repo, and live app are linked in the comments.

To everyone who followed along, commented, and shared advice: thank you. This community made this possible.

What's one lesson you learned from your first real project?

[Include before/after comparison: Week 1 notes vs Week 8 live app]

#buildinpublic #mvp #webdevelopment #retrospective #learning #softwaredevelopment

```

---

## Post-8-Weeks: Ongoing Content Strategy

### Monthly Content (Months 3-6)

**Post Type 1: Product Updates (Monthly)**

Track and share meaningful metrics updates:
- User growth
- Retention improvements
- Feature launches based on feedback
- Revenue (if you monetize)

**Post Type 2: Technical Deep Dives (Bi-weekly)**

Share specific technical solutions:
- "How I implemented adaptive difficulty in EndgameWizard"
- "Optimizing PostgreSQL queries for chess position lookup"
- "Building a streak system that users actually care about"

**Post Type 3: Career Updates (As Needed)**

- Final year project announcement
- Job search journey
- Interviews and lessons learned
- First job celebration

**Post Type 4: Reflection Posts (Monthly)**

- "3 months of daily active users: what I learned"
- "The unexpected ways users are using EndgameWizard"
- "Why I'm [continuing/pausing/pivoting] this project"

---

## Engagement Strategy

### How to Get More Eyes on Your Posts

**1. Post Timing**
- Sundays 9am-12pm GMT (professionals browsing weekend LinkedIn)
- Avoid Monday mornings (inbox overwhelm)
- Avoid Friday afternoons (weekend mode)

**2. Hashtag Strategy**
Use 3-5 relevant hashtags:
- **Industry tags:** #webdevelopment #fullstack #softwaredevelopment
- **Community tags:** #buildinpublic #indiehacker #mvp
- **Tech tags:** #react #nodejs #javascript

**3. Engage Before Posting**
Spend 15 minutes before posting:
- Comment on 3-5 posts in your feed
- Like content from target companies
- Respond to comments on your previous posts

**4. Respond to Every Comment**
- Reply within first hour if possible
- Ask follow-up questions
- Tag people when relevant
- Turn comments into conversations

**5. Tag Strategically**
- Tag relevant people/companies (sparingly)
- Tag when you reference their content/advice
- Don't spam tags

**6. Cross-Promote**
- Share to relevant LinkedIn groups
- Post shorter version on Twitter/X
- Add to your GitHub README
- Include in email signature

---

## Post Formatting Best Practices

### Visual Hierarchy

```

Hook (1-2 lines, bold or standalone)

Context paragraph (2-4 lines)

Main content:

- Use line breaks
- Use emojis sparingly (✅❌📊🚀)
- Use numbered lists (1️⃣2️⃣3️⃣)
- Use bullet points for scannability

Conclusion (1-2 lines)

Question to drive engagement

#hashtags

```

### Length Guidelines
- **Optimal length:** 150-250 words (1200-1500 characters)
- **Shorter posts (50-150 words):** Quick wins, daily updates
- **Longer posts (250-400 words):** Deep dives, retrospectives

### Visual Content
- Include image/screenshot in EVERY post
- Carousel posts (PDFs) get 2x engagement
- Video gets high engagement but harder to produce
- Code snippets as images (use carbon.now.sh)

---

## What NOT to Do

**❌ Avoid:**
- Posting only when you have good news (authenticity matters)
- Copy-pasting identical posts from other platforms
- Using too many hashtags (3-5 max)
- Making every post promotional
- Writing only about yourself (share learnings)
- Inconsistent posting (pick a schedule and stick to it)
- Ignoring comments on your posts
- Buying followers/engagement
- Posting LinkedIn clichés ("Agree?" "Thoughts?" "Let's connect!")

**❌ Red Flags for Recruiters:**
- No profile picture
- Generic headline ("Student at X University")
- Empty about section
- No posts or activity
- Only promotional content
- Controversial political/religious content

---

## Success Metrics to Track

### LinkedIn Profile Growth
- Connection growth rate (aim for 50-100/month)
- Profile views (track weekly)
- Search appearances (how often you show up)
- Follower count (less important than engagement)

### Post Performance
- **Impressions:** How many people saw it
- **Engagement rate:** (Likes + comments + shares) / impressions
- **Good engagement rate:** 5-10%
- **Great engagement rate:** 10%+

### Career Impact
- Recruiter InMails (quality over quantity)
- Interview requests
- Networking conversations
- Job offers/opportunities

---

## Tools & Resources

### Content Creation
- **Canva:** Image creation for posts
- **Carbon:** Code snippet images (carbon.now.sh)
- **Notion:** Content calendar and idea bank
- **Grammarly:** Proofreading

### Scheduling (Optional)
- **LinkedIn Native Scheduling:** Free, built-in
- **Buffer:** Schedule posts in advance
- **Taplio:** LinkedIn-specific analytics

### Analytics
- **LinkedIn Analytics:** Native dashboard
- **Google Sheets:** Track your own metrics
- **Shield Analytics:** Advanced LinkedIn insights (paid)

---

## Sample Content Calendar Template

| Week | Post Type | Topic | Status | Engagement Goal |
|------|-----------|-------|--------|-----------------|
| 1 | Launch | Why I'm building this | ✅ Posted | 50+ reactions |
| 2 | Technical | Tech stack decisions | ✅ Posted | 30+ reactions |
| 3 | Product | First user feedback | ⏳ Drafting | 40+ reactions |
| 4 | Technical | Debugging story | 📝 Planned | 35+ reactions |
| 5 | Metrics | Beta traction | 📝 Planned | 45+ reactions |
| 6 | Reflection | Feature that failed | 📝 Planned | 50+ reactions |
| 7 | Milestone | Going live | 📝 Planned | 75+ reactions |
| 8 | Retrospective | 8-week journey | 📝 Planned | 100+ reactions |

---

## The Long Game

### Month 3-6: Scale Content
- Continue weekly posts (shift to bi-weekly if needed)
- Start engaging in comments on bigger accounts
- Share more technical deep dives
- Document final year project journey

### Month 6-12: Career Push
- Update profile with EndgameWizard as featured project
- Start applying to roles
- Use posts as conversation starters in interviews
- Network with developers at target companies

### Month 12+: Establish Authority
- Become known for building in public
- Help others starting their journey
- Consider writing longer articles
- Speak at university events/meetups

---

## Final Checklist

**Before Your First Post:**
- [ ] Optimize LinkedIn profile
- [ ] Connect with 50-100 relevant people
- [ ] Engage with content for 1 week
- [ ] Draft first 3 posts
- [ ] Set reminder for posting schedule

**Each Week:**
- [ ] Write post by Wednesday
- [ ] Review and edit Thursday
- [ ] Schedule for Sunday morning
- [ ] Respond to all comments within 24h
- [ ] Engage with others' content 3x/week

**Monthly Review:**
- [ ] Check analytics and engagement
- [ ] Update content calendar
- [ ] Reflect on what's working
- [ ] Adjust strategy as needed

---

## Remember

**The goal isn't to go viral. The goal is to demonstrate:**
1. You can ship products from scratch
2. You make thoughtful technical decisions
3. You learn from feedback and iterate
4. You communicate clearly about your work
5. You're someone worth hiring

Consistency > Perfection. Ship the post, learn, improve.

Good luck! 🚀
```