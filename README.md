# ✦ LifeOS — AI Personal Operating System

> **Run your life intelligently.** LifeOS is a production-ready, open-source AI-powered personal operating system for students and ambitious people.

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/YOUR_USERNAME/lifeos)
![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
![Next.js](https://img.shields.io/badge/Next.js-14-black)
![TypeScript](https://img.shields.io/badge/TypeScript-5-blue)
![Tailwind CSS](https://img.shields.io/badge/Tailwind-3-38bdf8)

---

## 🚀 What is LifeOS?

LifeOS is your AI-powered personal chief of staff. It combines task management, habit tracking, goal planning, AI chat, and life analytics into one elegant, unified interface — powered by Claude (Anthropic) and built with Next.js 14.

### ✨ Features

| Feature | Description |
|---|---|
| 🧠 **AI Daily Briefing** | Every morning, Claude reads your tasks and habits and generates a personalized briefing |
| 📅 **AI Planner** | Input your goals → AI generates your optimal daily schedule |
| ✅ **Tasks & Goals** | Kanban, list, and calendar views with priorities and deadlines |
| 💬 **AI Chat** | Ask anything about productivity, planning, studying, or life |
| 📝 **Notes + AI Summarizer** | Write notes → AI extracts key points and action items |
| 🔥 **Habit Tracker** | Track sleep, workouts, study, mood with streaks and 7-day view |
| 📊 **Analytics** | Productivity trends, peak hours, missed tasks, weekly insights |
| 🔭 **Future Simulator** | "If I code 2h daily for 6 months?" → AI predicts outcomes with charts |
| ⚙️ **Settings** | Theme toggle, AI provider selection, notification preferences |

---

## 🖼️ Screenshots

> Dashboard · AI Planner · Habit Tracker · Analytics · Future Simulator

*(Add screenshots after first deploy)*

---

## 🛠️ Tech Stack

```
Frontend     → Next.js 14 (App Router) + TypeScript + Tailwind CSS + Framer Motion
AI           → Anthropic Claude API (claude-opus-4-5) + OpenAI GPT-4 (modular)
Auth         → Clerk (social login, email/password, magic link)
Database     → PostgreSQL + Prisma ORM
Deployment   → Vercel (frontend + API) + Neon/Supabase (free Postgres)
Styling      → Liquid Glass UI · Dark/Light mode · Sora font
```

---

## ⚡ Quick Start (Local Development)

### Prerequisites

- Node.js 18+
- PostgreSQL database (or use [Neon](https://neon.tech) — free tier)
- [Clerk](https://clerk.com) account (free)
- [Anthropic](https://console.anthropic.com) API key

### 1. Clone the repo

```bash
git clone https://github.com/YOUR_USERNAME/lifeos.git
cd lifeos
```

### 2. Install dependencies

```bash
npm install
# or
yarn install
# or
pnpm install
```

### 3. Set up environment variables

```bash
cp .env.example .env.local
```

Then fill in your `.env.local`:

```env
# ── Clerk Auth ─────────────────────────────────────────────────────────────
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_test_...
CLERK_SECRET_KEY=sk_test_...
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL=/dashboard
NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL=/dashboard

# ── Database ───────────────────────────────────────────────────────────────
DATABASE_URL=postgresql://user:password@localhost:5432/lifeos

# ── AI ─────────────────────────────────────────────────────────────────────
ANTHROPIC_API_KEY=sk-ant-...
OPENAI_API_KEY=sk-...         # optional fallback

# ── App ────────────────────────────────────────────────────────────────────
NEXT_PUBLIC_APP_URL=http://localhost:3000
```

### 4. Set up the database

```bash
# Generate Prisma client
npm run db:generate

# Push schema to your database (creates all tables)
npm run db:push

# Optional: seed with demo data
# First set SEED_CLERK_ID=your_clerk_user_id in .env.local
npm run db:seed
```

### 5. Run the dev server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) — you're live! 🎉

---

## 🌐 Deploy to Vercel (Free)

LifeOS is designed to run 100% free on Vercel + Neon Postgres.

### Step 1 — Set up free Postgres with Neon

1. Go to [neon.tech](https://neon.tech) → Create free account
2. Create a new project → Copy the **connection string**
3. It looks like: `postgresql://user:pass@ep-xxx.us-east-1.aws.neon.tech/neondb?sslmode=require`

### Step 2 — Set up Clerk

1. Go to [clerk.com](https://clerk.com) → Create free account
2. Create a new application
3. Go to **API Keys** → Copy `Publishable Key` and `Secret Key`
4. In Clerk Dashboard → **Paths** → set:
   - Sign-in URL: `/sign-in`
   - Sign-up URL: `/sign-up`
   - After sign-in: `/dashboard`
   - After sign-up: `/dashboard`

### Step 3 — Get Anthropic API Key

1. Go to [console.anthropic.com](https://console.anthropic.com)
2. Create account → **API Keys** → Create new key
3. You get $5 free credits to start

### Step 4 — Deploy to Vercel

**Option A: One-click deploy**

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/YOUR_USERNAME/lifeos)

**Option B: CLI deploy**

```bash
npm install -g vercel
vercel login
vercel --prod
```

### Step 5 — Add environment variables in Vercel

Go to your Vercel project → **Settings** → **Environment Variables** → add:

```
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY   → your clerk publishable key
CLERK_SECRET_KEY                    → your clerk secret key
NEXT_PUBLIC_CLERK_SIGN_IN_URL       → /sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL       → /sign-up
NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL → /dashboard
NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL → /dashboard
DATABASE_URL                        → your neon connection string
ANTHROPIC_API_KEY                   → your anthropic key
NEXT_PUBLIC_APP_URL                 → https://your-app.vercel.app
```

### Step 6 — Initialize database on Vercel

After first deploy, run in Vercel CLI:

```bash
vercel env pull .env.local
npm run db:push
```

Or add `prisma db push` to your build command in `vercel.json` (already configured).

**That's it — your LifeOS is live! 🚀**

---

## 📁 Project Structure

```
lifeos-web/
├── index.html
├── css/
│   └── style.css
├── js/
│   └── app.js
├── assets/
│   ├── icons/
│   └── images/
└── README.mds
```

---

## 🗄️ Database Schema

LifeOS uses PostgreSQL with Prisma ORM. Key models:

```
User          → Linked to Clerk auth
Task          → Title, status, priority, due date, goal link
Goal          → Title, progress %, target date, milestones
Habit         → Name, icon, color, streak tracking
HabitLog      → Daily habit completion records
Note          → Content, AI summary, action items
ChatMessage   → Full conversation history
PlannerSession→ Saved AI-generated schedules
AnalyticsEvent→ Productivity event tracking
```

---

## 🤖 AI System Prompts

All AI prompts are in `lib/ai.ts`:

- **`assistant`** — Personal chief of staff, knows user context
- **`planner`** — Generates daily schedules in structured JSON
- **`simulator`** — Predicts future outcomes with growth charts
- **`summarize`** — Extracts key points and action items from notes
- **`dailyBriefing`** — Sharp, personalized morning briefing

---

## 🎨 Design System

LifeOS uses a **Liquid Glass** design language:

```css
.glass-card          → Frosted glass cards (backdrop-blur + transparency)
.glass-card-hover    → Glass cards with smooth hover lift
.sidebar-glass       → Blurred translucent sidebar
.nav-glass           → Floating nav with blur
.gradient-text       → Indigo→Purple gradient text
.btn-primary         → Gradient CTA button with shadow
.input-glass         → Frosted input fields
.shimmer             → Loading skeleton animation
.mesh-bg             → Subtle radial gradient background
```

Colors: Indigo `#6366f1` · Purple `#8b5cf6` · Cyan `#06b6d4` · Emerald `#10b981`

---

## 🆓 Free Hosting Guide

| Service | Free Tier | What it's used for |
|---|---|---|
| **Vercel** | Unlimited deploys, 100GB bandwidth | Frontend + API routes |
| **Neon** | 0.5GB storage, 1 branch | PostgreSQL database |
| **Clerk** | 10,000 MAU | Authentication |
| **Anthropic** | $5 free credits | AI features |

**Total monthly cost: $0** (within free tier limits)

---

## 🔧 Configuration Reference

### `next.config.js`
- Image domains for Clerk avatars
- Server actions configuration

### `vercel.json`
- Streaming API timeout: 60 seconds (for AI routes)
- Build command includes `prisma db push`

### `tailwind.config.ts`
- Custom CSS variables for glass design
- Sora + system font stack
- Custom animations: float, shimmer, fade-in

### `middleware.ts`
- Public routes: `/`, `/sign-in`, `/sign-up`
- All other routes require Clerk authentication

---

## 🛣️ Roadmap

- [ ] Calendar view with drag-and-drop scheduling
- [ ] Mobile app (React Native)
- [ ] Document upload (PDF → AI summary)
- [ ] Team/accountability partner features
- [ ] Webhook for Notion/Google Calendar sync
- [ ] Voice input for quick task capture
- [ ] AI-powered journaling
- [ ] Weekly email digest

---

## 🤝 Contributing

1. Fork the repo
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit changes: `git commit -m 'Add amazing feature'`
4. Push: `git push origin feature/amazing-feature`
5. Open a Pull Request

Please follow the existing code style and add TypeScript types for all new code.

---

## 📄 License

MIT © 2025 LifeOS Team

---

## 🙏 Built With

- [Next.js](https://nextjs.org) — React framework
- [Anthropic Claude](https://anthropic.com) — AI backbone
- [Clerk](https://clerk.com) — Authentication
- [Prisma](https://prisma.io) — Database ORM
- [Framer Motion](https://framer.com/motion) — Animations
- [Tailwind CSS](https://tailwindcss.com) — Styling
- [Recharts](https://recharts.org) — Charts
- [Lucide](https://lucide.dev) — Icons
- [Neon](https://neon.tech) — Serverless Postgres

---

<p align="center">
  <strong>LifeOS — Run your life intelligently ✦</strong><br/>
  <a href="https://lifeos.app">Website</a> · 
  <a href="https://github.com/YOUR_USERNAME/lifeos/issues">Issues</a> · 
  <a href="https://twitter.com/lifeos_app">Twitter</a>
</p>
