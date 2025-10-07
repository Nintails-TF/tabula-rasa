---
date created: Tuesday, October 7th 2025, 11:34:00 am
date modified: Tuesday, October 7th 2025, 11:48:32 am
---

# EndgameWizard: Technical Roadmap

**Goal:** Ship a working MVP in 8 weeks (~60 hours total)  
**Builder:** Solo developer (3rd year comp sci student)  
**Launch target:** 10-20 beta users from local chess club

---

## Tech Stack

### Frontend

- **Framework:** React 18+ with Vite (faster than Create React App)
- **Styling:** Tailwind CSS (rapid development, no CSS file management)
- **Chess UI:** react-chessboard (drag-and-drop, mobile-friendly)
- **Chess Logic:** chess.js (move validation, checkmate detection)
- **Routing:** React Router v6
- **State Management:** React Context (useState/useReducer - keep it simple)
- **HTTP Client:** Axios or fetch API

### Backend

- **Runtime:** Node.js 18+ with Express
- **Database:** PostgreSQL (structured data, good for analytics later)
- **ORM:** Prisma (type-safe, great DX)
- **Authentication:** JWT tokens (simple, stateless)
- **Chess Engine:** Stockfish.js (client-side) or Lichess API (server-side)

### Deployment & Infrastructure

- **Frontend Hosting:** Vercel (free tier, automatic deploys from GitHub)
- **Backend Hosting:** Railway or Render (free tier with database)
- **Database:** Included with Railway/Render free tier
- **Domain:** endgamewizard.com (Namecheap, £10/year)
- **Version Control:** GitHub
- **CI/CD:** GitHub Actions (optional, Vercel handles frontend automatically)

### Development Tools

- **Code Editor:** VS Code
- **API Testing:** Postman or Thunder Client
- **Database Client:** TablePlus or pgAdmin
- **Design/Mockups:** Figma (free tier) or pen and paper

---

## MVP Feature Scope

### Must Have (Core Loop)

✅ User authentication (email + password)  
✅ Daily gauntlet with 5 positions  
✅ Mix of timed (blitz) and untimed positions  
✅ Chess board with move validation  
✅ Win/loss detection  
✅ Instant feedback ("Correct!" / "Here's the solution")  
✅ Streak counter  
✅ Basic progress tracking  
✅ Mobile responsive

### Explicitly NOT Building (Yet)

❌ Multiple gauntlet types  
❌ Adaptive difficulty  
❌ Leaderboards  
❌ Social features  
❌ Payment system  
❌ Email notifications  
❌ Password reset flow (admin can reset manually)  
❌ Detailed analytics dashboard  
❌ Custom position creator  
❌ Video explanations  
❌ OAuth (Google/Facebook login)

---

## 8-Week Development Plan

### Week 1: Project Setup & Chess Basics (6-8 hours)

**Day 1-2: Environment Setup (2 hours)**

- [ ] Purchase endgamewizard.com domain
- [ ] Set up GitHub repository
- [ ] Initialize React app with Vite: `npm create vite@latest endgame-wizard -- --template react`
- [ ] Install dependencies: `npm install react-chessboard chess.js tailwindcss`
- [ ] Configure Tailwind CSS
- [ ] Set up ESLint and Prettier
- [ ] Create basic folder structure

**Day 3-4: Basic Chess Board (2-3 hours)**

- [ ] Create ChessBoard component with react-chessboard
- [ ] Integrate chess.js for move validation
- [ ] Implement basic move making (click piece → click square)
- [ ] Display whose turn it is
- [ ] Test: Can make legal moves, illegal moves rejected

**Day 5-6: Position Loading (2-3 hours)**

- [ ] Create Position component
- [ ] Load position from FEN string
- [ ] Implement "Reset Position" button
- [ ] Create 5 sample endgame positions (hardcoded)
- [ ] Test: Can load different positions correctly

**Deliverable:** Working chess board that loads positions and validates moves

---

### Week 2: Timer & Win Detection (8-10 hours)

**Day 1-2: Timer Component (3-4 hours)**

- [ ] Create Timer component with countdown
- [ ] Start/pause/reset functionality
- [ ] Timer expires → show "Time's up!" modal
- [ ] Connect timer to specific positions
- [ ] Test: Timer counts down correctly, expires as expected

**Day 3-4: Win/Loss Detection (3-4 hours)**

- [ ] Detect checkmate using chess.js
- [ ] Detect stalemate and draw conditions
- [ ] Create simple modal for "You won!" / "You lost!" / "Draw!"
- [ ] Show correct solution (series of moves) on loss
- [ ] Test: Correctly identifies win/loss/draw

**Day 5-6: Position Flow (2 hours)**

- [ ] Create "Next Position" button
- [ ] Track current position index (1 of 5)
- [ ] Show progress indicator
- [ ] Test: Can complete all 5 positions in sequence

**Deliverable:** Can play through 5 positions with timers and win detection

---

### Week 3: Backend Setup (8-10 hours)

**Day 1-2: Backend Initialization (3 hours)**

- [ ] Initialize Node.js project: `npm init -y`
- [ ] Install Express, Prisma, JWT, bcrypt, cors, dotenv
- [ ] Set up Express server with basic routes
- [ ] Configure CORS for frontend
- [ ] Create .env file for secrets
- [ ] Test: Server runs on localhost:3000

**Day 3-4: Database Schema (3-4 hours)**

- [ ] Initialize Prisma: `npx prisma init`
- [ ] Design database schema:
    - Users table (id, email, password_hash, created_at)
    - Progress table (id, user_id, date, positions_completed, streak, created_at)
    - Gauntlets table (id, date, positions_json, difficulty_levels)
- [ ] Run migrations: `npx prisma migrate dev`
- [ ] Test: Can create tables, seed with dummy data

**Day 5-6: Authentication Endpoints (2-3 hours)**

- [ ] POST /api/auth/register (create user, hash password)
- [ ] POST /api/auth/login (verify password, return JWT)
- [ ] Middleware: verifyToken (protect routes)
- [ ] Test with Postman: Can register, login, receive token

**Deliverable:** Backend with database and working auth endpoints

---

### Week 4: User System Integration (8-10 hours)

**Day 1-2: Frontend Auth (3-4 hours)**

- [ ] Create Login page component
- [ ] Create Register page component
- [ ] Store JWT in localStorage
- [ ] Create AuthContext for global auth state
- [ ] Protected routes (redirect to login if not authed)
- [ ] Test: Can register, login, logout

**Day 3-4: Connect Frontend to Backend (3-4 hours)**

- [ ] Axios interceptor for adding JWT to requests
- [ ] Create API service layer (apiClient.js)
- [ ] Test connection: frontend → backend
- [ ] Handle token expiration gracefully
- [ ] Test: Auth persists on page reload

**Day 5-6: Basic User Profile (2 hours)**

- [ ] Display logged-in user's email
- [ ] Show account creation date
- [ ] Logout button
- [ ] Test: Profile displays correctly

**Deliverable:** Full authentication flow working

---

### Week 5: Gauntlet System (10-12 hours)

**Day 1-2: Gauntlet Data Structure (3 hours)**

- [ ] Create gauntlet service (generateDailyGauntlet)
- [ ] Hardcode 7 days of gauntlet data (5 positions each)
- [ ] Each position: FEN, isTimedm timeLimit, difficulty, solution
- [ ] API: GET /api/gauntlet/daily (returns today's gauntlet)
- [ ] Test: Can fetch daily gauntlet

**Day 3-4: Gauntlet UI (4-5 hours)**

- [ ] Create Gauntlet component
- [ ] Fetch daily gauntlet on load
- [ ] Display position N of 5
- [ ] Show/hide timer based on position config
- [ ] Handle position completion
- [ ] Test: Can play through entire gauntlet

**Day 5-6: Progress Tracking (3-4 hours)**

- [ ] API: POST /api/progress (save completed position)
- [ ] Calculate streak (consecutive days with completed gauntlet)
- [ ] Display streak on home page
- [ ] Store completion time and accuracy
- [ ] Test: Progress saves correctly, streak calculates

**Deliverable:** Daily gauntlet system with progress tracking

---

### Week 6: Feedback & Polish (8-10 hours)

**Day 1-2: Feedback Screens (3-4 hours)**

- [ ] Success modal: "Correct! Next position"
- [ ] Failure modal: "Not quite. Here's the winning line:" (show moves)
- [ ] Gauntlet complete screen: "4/5 completed! Streak: 3 days"
- [ ] Add confetti animation on gauntlet complete
- [ ] Test: Feedback feels good

**Day 3-4: Show Solution (3-4 hours)**

- [ ] Animate solution moves on the board
- [ ] "Replay" button to see solution again
- [ ] Display notation (e.g., "1. Rxe7 Kf8 2. Re8#")
- [ ] Test: Solution displays clearly

**Day 5-6: UI Polish (2-3 hours)**

- [ ] Add wizard theming (subtle - icons, colors)
- [ ] Improve mobile responsiveness
- [ ] Loading states (spinners)
- [ ] Error handling (show user-friendly messages)
- [ ] Test: UI feels smooth

**Deliverable:** Polished core experience

---

### Week 7: Deployment & Testing (6-8 hours)

**Day 1-2: Backend Deployment (2-3 hours)**

- [ ] Create Railway/Render account
- [ ] Connect GitHub repository
- [ ] Add environment variables (DATABASE_URL, JWT_SECRET)
- [ ] Deploy backend
- [ ] Verify database connection
- [ ] Test: Backend accessible at <https://api.endgamewizard.com>

**Day 3-4: Frontend Deployment (2-3 hours)**

- [ ] Create Vercel account
- [ ] Connect GitHub repository
- [ ] Configure environment variables (VITE_API_URL)
- [ ] Deploy frontend
- [ ] Connect domain: endgamewizard.com
- [ ] Test: Site loads at endgamewizard.com

**Day 5-6: End-to-End Testing (2 hours)**

- [ ] Test full user journey: register → login → play gauntlet → logout
- [ ] Test on mobile device
- [ ] Fix any deployment issues
- [ ] Invite 2-3 friends to test

**Deliverable:** Deployed app accessible at endgamewizard.com

---

### Week 8: Beta Launch Prep (6-8 hours)

**Day 1-2: Landing Page (2-3 hours)**

- [ ] Create simple landing page (/landing route)
- [ ] Headline: "The fun way to stop losing won endgames"
- [ ] Email signup form (save to database)
- [ ] Screenshot/demo of daily gauntlet
- [ ] Test: Landing page converts interest

**Day 3-4: Content Creation (2-3 hours)**

- [ ] Create 30 days of gauntlet content (150 positions)
- [ ] Mix of K+P, K+Q, basic Rook endgames
- [ ] Vary difficulty and time controls
- [ ] Test: Sufficient variety for 1 month

**Day 5-6: Beta Invites (2 hours)**

- [ ] Share with 10 chess club members
- [ ] Create feedback form (Google Forms)
- [ ] Set up basic analytics (Plausible or Simple Analytics)
- [ ] Monitor: Daily active users, retention, bug reports

**Deliverable:** Live beta with 10-20 users

---

## Folder Structure

```
endgame-wizard/
├── client/                    # React frontend
│   ├── src/
│   │   ├── components/
│   │   │   ├── ChessBoard.jsx
│   │   │   ├── Timer.jsx
│   │   │   ├── Position.jsx
│   │   │   ├── Gauntlet.jsx
│   │   │   └── Modal.jsx
│   │   ├── pages/
│   │   │   ├── Login.jsx
│   │   │   ├── Register.jsx
│   │   │   ├── Home.jsx
│   │   │   └── Profile.jsx
│   │   ├── context/
│   │   │   └── AuthContext.jsx
│   │   ├── services/
│   │   │   └── apiClient.js
│   │   ├── utils/
│   │   │   └── chessUtils.js
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── public/
│   └── package.json
│
├── server/                    # Node.js backend
│   ├── src/
│   │   ├── routes/
│   │   │   ├── auth.js
│   │   │   ├── gauntlet.js
│   │   │   └── progress.js
│   │   ├── middleware/
│   │   │   └── verifyToken.js
│   │   ├── services/
│   │   │   ├── gauntletService.js
│   │   │   └── userService.js
│   │   ├── prisma/
│   │   │   └── schema.prisma
│   │   └── server.js
│   ├── .env
│   └── package.json
│
└── README.md
```

---

## Database Schema (Prisma)

```prisma
// schema.prisma

generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model User {
  id            String     @id @default(uuid())
  email         String     @unique
  passwordHash  String
  createdAt     DateTime   @default(now())
  progress      Progress[]
}

model Progress {
  id                 String   @id @default(uuid())
  userId             String
  date               DateTime @default(now())
  positionsCompleted Int      @default(0)
  positionsAttempted Int      @default(0)
  currentStreak      Int      @default(0)
  longestStreak      Int      @default(0)
  completionTime     Int?     // seconds
  user               User     @relation(fields: [userId], references: [id])
  
  @@unique([userId, date])
}

model Gauntlet {
  id            String   @id @default(uuid())
  date          DateTime @unique
  positionsJson String   // JSON array of positions
  createdAt     DateTime @default(now())
}
```

---

## Key Technical Decisions

### Why These Choices?

**React + Vite:** Faster than CRA, modern, well-documented  
**Tailwind CSS:** Rapid styling without CSS files  
**chess.js:** Battle-tested, handles all chess logic  
**PostgreSQL:** Structured data, easy to query for analytics later  
**Prisma:** Type-safe ORM, great developer experience  
**Vercel + Railway:** Free tiers, zero-config deployment  
**JWT:** Stateless auth, scales easily

### What We're Avoiding (For Now)

**No Redux:** Context API sufficient for this scale  
**No microservices:** Single backend is fine for MVP  
**No Docker:** Complicates deployment, not needed yet  
**No native mobile apps:** Progressive Web App is enough  
**No automated testing:** Manual testing sufficient at this stage (add later)

---

## Cost Breakdown

|Item|Cost|Notes|
|---|---|---|
|Domain (endgamewizard.com)|£10/year|Namecheap|
|Frontend hosting (Vercel)|£0|Free tier|
|Backend hosting (Railway)|£0|Free tier (500hr/month)|
|Database (Railway)|£0|Included in free tier|
|SSL Certificate|£0|Auto-provisioned|
|**Total (Year 1)**|**£10**||

**When costs increase:**

- Railway free tier limits: 500 hours/month (~16hrs/day)
- If you get 1000+ daily users, upgrade to Railway hobby plan (~$5/month)
- PostgreSQL storage limits (1GB free, upgrade as needed)

---

## Critical Path & Risk Management

### What Could Go Wrong

**Risk: Position generation is harder than expected**

- **Mitigation:** Hardcode 30 days of positions (150 total) - that's plenty for MVP
- **Fallback:** Use Lichess puzzle database API for position inspiration

**Risk: Stockfish/tablebase integration is complex**

- **Mitigation:** Don't use tablebases for MVP - just use chess.js to detect wins
- **Fallback:** Use Lichess API for position evaluation (free, no setup)

**Risk: Authentication bugs**

- **Mitigation:** Use well-tested libraries (bcrypt, jsonwebtoken)
- **Fallback:** Implement simple "access code" system (no registration) for initial beta

**Risk: Deployment issues**

- **Mitigation:** Deploy early (Week 7) to catch issues with time to fix
- **Fallback:** Use Netlify for frontend, Heroku for backend if Vercel/Railway problematic

**Risk: Running out of time (exams, coursework)**

- **Mitigation:** Can pause development - no ongoing costs
- **Mitigation:** MVP scope is ruthlessly minimal (60 hours achievable)
- **Fallback:** Ship "super MVP" with just 3 positions per gauntlet if needed

---

## Success Metrics (Technical)

**Week 4:** Backend deployed and accessible  
**Week 6:** Can complete full gauntlet from login to completion  
**Week 7:** App deployed and accessible at endgamewizard.com  
**Week 8:** 10 beta users can use the app without critical bugs

**Performance Targets:**

- Page load < 2 seconds
- Move validation < 100ms
- Zero database downtime
- Mobile responsive (works on phone without issues)

---

## Post-MVP: What's Next?

**If beta shows promise (30%+ day-7 retention):**

**Month 3:**

- Add more gauntlet variety (Sprint Days, Theme Days)
- Improve position quality based on feedback
- Basic leaderboard (top streaks)

**Month 4-6:**

- Adaptive difficulty (positions match player rating)
- Progress dashboard (charts, insights)
- Email notifications (streak reminders)

**Month 6-12:**

- Freemium model implementation
- Payment integration (Stripe)
- Mobile app (React Native or PWA enhancement)
- Advanced analytics

**Don't build these until core retention is proven.**

---

## Getting Started Checklist

**Tonight (30 minutes):**

- [ ] Purchase endgamewizard.com
- [ ] Create GitHub repository
- [ ] Set up React project locally
- [ ] Make first commit

**This Weekend (3-4 hours):**

- [ ] Build basic chess board with react-chessboard
- [ ] Make a few moves work
- [ ] Deploy to Vercel (even if just "Hello World")
- [ ] You now have something live!

**This Week:**

- [ ] Show working board to 1-2 club members
- [ ] Get feedback on position difficulty
- [ ] Begin Week 1 tasks

**Remember:** Perfect is the enemy of done. Ship something rough in 8 weeks, then iterate based on real usage.

---

## Resources

**Libraries:**

- react-chessboard: <https://github.com/Clariity/react-chessboard>
- chess.js: <https://github.com/jhlywa/chess.js>
- Tailwind CSS: <https://tailwindcss.com/docs>
- Prisma: <https://www.prisma.io/docs>

**APIs:**

- Lichess API: <https://lichess.org/api>
- Stockfish.js: <https://github.com/nmrugg/stockfish.js>

**Deployment:**

- Vercel Docs: <https://vercel.com/docs>
- Railway Docs: <https://docs.railway.app>

**Positions:**

- Lichess Puzzle Database: <https://database.lichess.org>
- Syzygy Tablebase Online: <https://syzygy-tables.info>

**Student Resources:**

- GitHub Student Developer Pack: <https://education.github.com/pack>
- AWS Educate: Free cloud credits for students

---

## Final Notes

**This roadmap is aggressive but achievable.** You have the skills, the test audience, and the domain knowledge. The key is staying focused on the MVP scope and not getting distracted by "nice to have" features.

**Track your hours.** If you hit Week 4 and you've already spent 40 hours, you're behind pace. Cut scope if needed.

**Ship something imperfect.** A working app with 5 hardcoded positions is infinitely more valuable than a perfect app that never launches.

**The goal:** By Week 8, your chess club friends can open endgamewizard.com, play today's gauntlet, and come back tomorrow. Everything else is secondary.

Good luck! 🧙‍♂️