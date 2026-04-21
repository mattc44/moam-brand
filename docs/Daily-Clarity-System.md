# Daily Clarity System — Design & Product Reference

> A premium interactive productivity web app for high-achieving Christian men. Lead magnet for Matt Chenard's Man on a Mission (MOAM) community.

---

## What It Is

The Daily Clarity System (DCS) is a full-stack web application that gives users a structured morning/evening productivity framework. It's built as a free tool to attract and convert men into the MOAM coaching community. The app feels like a real premium product — not a landing page, not a quiz funnel. It's meant to be used daily.

**Live at:** [manonmission.ca](https://www.manonmission.ca/)

**Tagline:** *"Clarity is the elimination of mental clutter. When you know exactly what matters, everything else falls away."*

---

## Design Concept — "The Ascent"

The visual design follows the **Ascent** concept: a vertical mountaineering journey. The page metaphor is climbing — you ascend through the system each day. The design is dark, bold, masculine, and purposeful. No fluff, no pastel gradients, no coaching-bro aesthetic.

**Design inspiration:** Editorial longform storytelling meets alpine expedition documentation (Arc'teryx, Black Diamond). Premium outdoor brand meets dark-mode SaaS.

**Core principles:**
- Every element serves a mission — zero decoration without function
- High information density with absolute clarity
- Dark-dominant with surgical sage green accents
- Content is the product — the UI is the frame

---

## Brand Colors (DCS-Specific)

| Name | Hex | Usage |
|------|-----|-------|
| Stealth Black | `#0A0A0A` | Primary background (all screens) |
| Off-White | `#F5F5F0` | All readable text, headings |
| Sage Green | `#7B9E8E` | Active states, completions, CTAs, progress |
| Maroon Red | `#800000` | Problem/pain states only (used sparingly) |
| Amber Gold | `#D4A843` | Dashboard stat icons, capture highlights |

> **Note:** These are DCS-specific tones. The master brand uses Mission Gold `#C9A84C` — use `#D4A843` for DCS in-app elements and `#C9A84C` for marketing materials.

---

## Typography

| Role | Font | Size Range | Style |
|------|------|-----------|-------|
| App title, section headers, stats | **Bebas Neue** | 36–96px | All caps, tracked wide |
| Body, interactive, labels | **Open Sans** | 14–18px | Regular / Semibold |
| Section numbers, dates | **Space Mono** | 12–14px | Monospace accent |

**Hierarchy rule:** Never more than 3 type sizes on screen at once. Bebas Neue for authority. Open Sans for usability.

---

## Logo & Emblem

**Compass Emblem (inverted/white):**
```
https://d2xsxph8kpxj0f.cloudfront.net/310519663280547267/9RdhS7AVQjVgnADdR9npSb/compass_emblem_a1f152d8.png
```
- Use `filter: invert(1)` on dark backgrounds
- On-screen size: 14×14px (sidebar), 56×56px (join screen hero), 32×32px (CTAs)

---

## App Structure — Tabs & Features

The app has 7 tabs accessed via a left sidebar on desktop / bottom nav on mobile.

### 1. Dashboard
**Purpose:** Command center. Morning orientation or evening reflection.

**Two modes:**
- **Morning Mode** (sun icon / amber accent) — prompts to set Big Three and capture brain dump
- **Evening Mode** (moon icon / indigo accent) — prompts to review Big Three, log a win, prep tomorrow

**Stats displayed (2×2 grid):**
| Stat | Color | Description |
|------|-------|-------------|
| In Capture | Amber `#D4A843` | Items in brain dump inbox |
| Big Three | Sage `#7B9E8E` | X/6 tasks completed (3 personal + 3 professional) |
| Active Projects | Purple `#8B5CF6` | Open project count |
| Win Streak | Orange `#EF8C44` | Consecutive days with a logged win |

**Quick view:** Today's Big Three (personal + professional) with progress bar

**Quote block:** Pulls a rotating daily quote from the DCS quote library. Left-bordered, italic, sage green accent.

---

### 2. Capture
**Purpose:** Brain dump / inbox. Get everything out of your head first, then prioritize.

**Workflow:**
1. User types anything on their mind — ideas, tasks, worries, to-dos
2. Items sit in the capture list
3. User processes them into Big Three, Projects, or discards

**Design feel:** Simple text input with a clean list. Items show timestamp. Nothing is categorized yet — it's raw.

---

### 3. Big Three
**Purpose:** Three personal priorities + three professional priorities for the day. The core of the system.

**Layout:**
- Two columns: Personal | Professional
- 3 slots each — text input + checkbox
- Completing all 6 shows a celebration state
- Items carry over to next day if incomplete (user decides)

**The philosophy:** Not a task list — it's the three highest-return actions for today. Quality over quantity. Tied to the MOAM Mission5 framework.

---

### 4. Projects
**Purpose:** Active project tracking. Kanban-lite with simple status management.

**Features:**
- Create projects with name, description, due date
- Mark complete
- Filter by active/completed
- Brief notes on each project

**Design:** Cards on dark background. Sage green for active status indicator. Clean, no calendar bloat.

---

### 5. Win Log
**Purpose:** Daily win documentation + streak tracking.

**Features:**
- Add one or more wins per day (text entries)
- Date-stamped automatically
- Streak calculation: consecutive days with at least one logged win
- Today's wins appear on Dashboard

**The philosophy:** Momentum is built by noticing progress. Most men skip this. The streak mechanic makes it sticky.

---

### 6. Deposits
**Purpose:** Habit/routine tracker tied to the MOAM Mission5 Framework life areas.

**Life areas tracked:**
- Faith
- Family
- Fitness
- Finance
- Focus (work/purpose)

**Features:**
- Create custom "deposits" (habits) in each life area
- Set frequency: daily, weekdays, specific days of week
- Check off for today
- Streak per deposit
- XP/Level system: accumulate points as deposits are completed
- Level titles (gamified)

**The philosophy:** Based on the "deposits" concept from MOAM — every small daily action is a deposit into the life you're building. Consistent deposits compound.

---

### 7. Join the Mission
**Purpose:** Community CTA page. Converts active DCS users into MOAM community members.

**Content:**
- MOAM compass emblem + "Join the Mission" headline
- Featured YouTube video embed (hardcoded: `iCo2xCb-6p0`)
- Latest YouTube video (auto-fetched via RSS, channel ID: `UCxKvfRHB1GBOmAMSEFCjPcA`)
- Two CTA cards:
  - **Join Man on a Mission** → `https://www.manonmission.ca/` (Sage Green, primary)
  - **Subscribe on YouTube** → `https://www.youtube.com/@mattchenard` (secondary)
- Three benefit blocks: Frameworks That Work / A Brotherhood That Sharpens / Accountability With Depth

---

## Sidebar (Navigation)

**Left sidebar on desktop, slide-in on mobile.**

Contains:
- MOAM compass emblem (top)
- Today's date
- Personal mission statement field (editable inline — user's one-sentence mission)
- Navigation tabs with badge counts
- Morning/Evening mode toggle (Sun / Moon)
- User profile display (name + email)
- Logout button

**Mission statement:** The sidebar shows the user's personal mission statement at all times — a one-line reminder of why they're doing this. Editable with a pencil icon. Empty state prompt: *"What is your mission?"*

---

## Authentication

- **OAuth via Manus** (third-party OAuth provider)
- User accounts: name + email stored
- App state persisted to backend per user via tRPC
- Sign-in screen: centered compass emblem, dark background, clean input form

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 18 + TypeScript |
| Routing | Wouter |
| State | React hooks + Zustand-style local stores |
| Animations | Framer Motion |
| UI Components | shadcn/ui (Radix primitives) |
| Icons | Lucide React |
| Styling | Tailwind CSS |
| Backend | Node.js + tRPC |
| Database ORM | Drizzle |
| Build | Vite |
| Testing | Vitest |

---

## Key Links

| Resource | URL |
|----------|-----|
| Community | https://www.manonmission.ca/ |
| Skool Community | https://www.skool.com/manonamission |
| YouTube Channel | https://www.youtube.com/@mattchenard |
| YouTube Channel ID | `UCxKvfRHB1GBOmAMSEFCjPcA` |
| Compass Emblem CDN | `https://d2xsxph8kpxj0f.cloudfront.net/310519663280547267/9RdhS7AVQjVgnADdR9npSb/compass_emblem_a1f152d8.png` |

---

## Design Notes for Agents

**Do:**
- Use `#0A0A0A` (not pure black) for all dark backgrounds
- Use `#7B9E8E` sage green exclusively for active/positive/complete states
- Bebas Neue for all display text — always tracked wide (`letter-spacing: wider`)
- Treat the app like a premium tool, not a marketing funnel
- Add `filter: invert(1)` when using the compass emblem on dark backgrounds
- State changes should feel consequential — satisfying micro-interactions

**Don't:**
- Use rounded corners larger than `rounded-lg` (8px)
- Add decorative elements without function
- Use white backgrounds — off-white `#F5F5F0` only
- Show price, coaching pitch, or sales content inside the app (except the Join tab)
- Use maroon `#800000` for anything positive — it's the pain/problem color

**Animation standard:**
- Framer Motion for all transitions
- Entry: `opacity: 0 → 1`, `y: 8 → 0`, duration `0.2s`
- Progress bars: smooth fill with `duration: 0.5s`
- Completion states: brief green pulse, then settle

---

## Brand Alignment

The Daily Clarity System lives inside the broader MOAM brand ecosystem:

| Element | Master Brand | DCS |
|---------|-------------|-----|
| Background | Mission Black `#0D1117` | Stealth Black `#0A0A0A` |
| Accent | Mission Gold `#C9A84C` | Sage Green `#7B9E8E` |
| Pain state | — | Maroon `#800000` |
| Primary font | Bold condensed sans | Bebas Neue |
| Body font | Calibri / Arial | Open Sans |
| Mood | Bold, mission-driven | Dark, tactical, ascent |

The DCS is the front door to MOAM — it's how men experience the philosophy before they experience the community.
