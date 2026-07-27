# PainPal

Team alpha — spec §3.2 hackathon build.

**One-liner:** A personalized physiotherapy platform for people with chronic pain

**Problem:** People with chronic pain face limited access to respectful, tailored physiotherapy services and environments that adapt to their conditions

**Solution:** An online platform offering virtual physiotherapy sessions, personalized exercise plans, and a community forum for people with chronic pain to connect and share their experiences

**Build scope:** **PainPal – Day 4‑5 Architecture (≈185 words)**  

**Tech‑stack**  
- **Front‑end:** React 18 + TypeScript, UI library (MUI) for accessible components; hosted on Vercel (edge CDN).  
- **Back‑end/API:** Node.js (Express) + TypeScript, containerised with Docker; hosted on AWS Fargate for auto‑scaling.  
- **Data layer:** PostgreSQL (RDS) for user/subscription data; Redis (Elasticache) for session & rate‑limiting.  
- **Video‑therapy:** Twilio Programmable Video (HIPAA‑compatible) embedded in React client.  
- **Payments:** Stripe Checkout (PCI‑DSS).  
- **Community:** Discourse (self‑hosted) integrated via SSO; fallback to a lightweight forum built with Node + SQLite if Discourse stalls.  

**Three core components**  
1. **Auth & Subscription Service** – JWT‑based login, role‑based access, Stripe webhook handling, subscription status sync.  
2. **Exercise Library & Planner** – CRUD API for 20 vetted physiotherapy videos, algorithmic plan generator (simple rule‑based matching to user‑reported pain zones).  
3. **Live Therapy Hub** – Secure video rooms, calendar scheduling, therapist‑user matching queue, session recording toggle for later review.  

**Top 2 risks**  
- **Regulatory/compliance risk:** Health‑data handling (HIPAA, GDPR). Mitigation: end‑to‑end encryption, minimal PHI storage, regular compliance audit.  
- **Engagement risk:** Low therapist availability causing poor session fill‑rates. Mitigation: pool of on‑demand freelance PTs, fallback to pre‑recorded “guided” sessions.  

**Fallback scope (if timeline/risks bite)**  
- Replace Twilio video with embedded YouTube‑private streams (access‑controlled).  
- Swap Discourse for a simple React‑based forum backed by PostgreSQL.  
- Launch with “self‑guided” exercise plans only; defer live sessions to a later sprint.  

Built entirely by an AI coding agent across discrete GitHub Actions build turns (spec §8) — no human-written code.
