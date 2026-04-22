# 💰 Business Model — Nimble

## Model Type

**B2C SaaS — Subscription (Freemium)**

Users pay a recurring monthly subscription to access the full catalog and AI features. This is the same model as Spotify, Storytel, and Netflix.

---

## Pricing Tiers

| Tier | Price | What's included |
|---|---|---|
| **Free** | $0 | 1 free book/month, basic player, no AI |
| **Basic** | $2.99/mo | Full catalog access, AI chat (20 queries/day), notes |
| **Standard** | $6.99/mo | Everything + unlimited AI, spaced repetition push |
| **Premium** | $10.99/mo | Everything + priority features, early access, offline |

**Pricing rationale:**
- Lower than Audible ($14.95) and Storytel (~$13) to reduce friction in a developing market
- $2.99 entry point removes the "too expensive" objection for Ukrainian audience
- $6.99 is the sweet spot — most features, most likely tier for engaged users

**Projected tier distribution (Year 1):**
- Free → 60% of signups (conversion funnel)
- Basic ($2.99) → 25%
- Standard ($6.99) → 12%
- Premium ($10.99) → 3%

**Blended ARPU:** ~$4.80/month per paying user

---

## Revenue Model with Publishers

### The Problem
Publishers need guaranteed revenue. Nimble needs to keep costs variable (not pay upfront per book).

### The Solution — Per-Minute Royalty

Nimble pays publishers based on actual listening time, not upfront licensing fees.

**Formula:**
```
Monthly royalty = (publisher_minutes_listened / total_minutes_listened) × (monthly_revenue × royalty_rate)
```

**Royalty rate:** 25–35% of subscription revenue allocated to content pool

**Example:**
- Month revenue: $5,000
- Content pool (30%): $1,500
- Publisher A = 40% of all listening minutes → receives $600
- Publisher B = 25% → receives $375
- etc.

### Why Publishers Should Say Yes

1. Zero upfront cost to them — no production needed (we use existing recordings)
2. Monthly automated report with full transparency
3. Growing platform = growing royalties over time
4. Ukrainian market alternative to piracy — legitimate revenue stream
5. Access to user engagement data (which books, which chapters people actually finish)

### Contract Structure

Each publisher agreement includes:
- Non-exclusive digital streaming license
- Per-minute royalty rate (negotiated, typically 25–35% revenue share)
- Monthly automated royalty report
- 30-day termination notice
- Anti-spoiler API access clause (Nimble must know chapter structure)

---

## Cost Structure

### MVP Phase (Months 1–2, ~$6,000)

| Item | Cost |
|---|---|
| AI Developer (2 months) | $3,500–4,000 |
| Servers + Supabase + OpenAI API | $300–400 |
| App Store ($99) + Google Play ($25) | $130 |
| Book licenses / revenue share agreements | $0–500 |
| Legal (publisher contracts) | $400 |
| Design tools + assets | $200 |
| **Total** | **~$5,500–5,630** |

### Ongoing Monthly Costs (Post-Launch)

| Item | Cost at 500 users | Cost at 2,000 users |
|---|---|---|
| AI API (Gemini/OpenAI) | ~$150/mo | ~$600/mo |
| Servers (Supabase Pro) | $25/mo | $100/mo |
| Audio CDN (storage + delivery) | $50/mo | $200/mo |
| Firebase (push) | Free | Free |
| **Total infrastructure** | **~$225/mo** | **~$900/mo** |

---

## Financial Projections

### Conservative Scenario

| Period | Paying Users | Monthly Revenue | Monthly Costs | Net |
|---|---|---|---|---|
| Month 1–3 (beta) | 0–50 | $0–240 | $300 | -$300 |
| Month 4–6 | 100–200 | $480–960 | $400 | +$80–560 |
| Month 7–12 | 300–600 | $1,440–2,880 | $600 | +$840–2,280 |
| Year 2 | 1,000–3,000 | $4,800–14,400 | $1,500 | +$3,300–12,900 |
| Year 3 | 5,000–10,000 | $24,000–48,000 | $5,000 | +$19,000–43,000 |

### Break-Even Point

**~400–500 paying subscribers** covers all infrastructure + basic operating costs.

At blended ARPU of $4.80 and 500 users: **$2,400/month revenue vs ~$600 costs** → profitable at this scale.

**Realistic break-even: Month 8–14** depending on growth rate of organic content strategy.

---

## Growth Strategy

### Phase 1 — Organic (Months 1–6)
- Founder-led content on TikTok, Instagram Reels, Threads, YouTube
- Content angle: "Building a startup in public" + book-related content
- Goal: Build audience BEFORE launch so Day 1 has waitlist signups
- No paid acquisition in this phase

### Phase 2 — Retention (Months 4–12)
- Spaced repetition push notifications bring users back daily
- Social layer creates network effect (invite friends = more value)
- Streak system (like Duolingo) rewards consistent listening
- Email newsletter with reading insights from AI

### Phase 3 — Paid Acquisition (Year 2)
- Retarget engaged social media followers
- Influencer partnerships with Ukrainian book bloggers
- App Store optimization for "аудіокниги" keywords

---

## Grant & Investment Strategy

### Immediate (Now)
- **Дія.Бізнес grant:** 250,000 UAH (~$6,000) — matches MVP budget exactly
- Requirement: hire 1 employee (built into operational budget as AI developer)

### Post-MVP (Month 3–6)
- **Grant programs for projects with existing MVP:** stronger application with real user data
- **Angel investors:** 500–2,000 users + $2,000+/month revenue = credible pitch
- **EU startup grants:** Ukrainian tech startups eligible for several EU innovation funds

### Why Investors Should Care
- Fastest-growing media format globally (24.4% CAGR)
- Zero AI-native competitor in Ukrainian market
- Low CAC (founder-led organic content)
- High retention mechanism built in (spaced repetition = daily opens)
- Clear path to $1M ARR with 17,000 paying subscribers at blended $5/month

---

## Key Metrics to Track

| Metric | Target (Month 6) | Target (Month 12) |
|---|---|---|
| MAU | 500 | 2,000 |
| Paying subscribers | 150 | 600 |
| DAU/MAU ratio | >40% | >50% |
| Average listening time/session | >25 min | >30 min |
| AI queries per user/week | >5 | >8 |
| Churn rate (monthly) | <8% | <5% |
| Publisher partners | 3 | 8 |
