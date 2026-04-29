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
| **ARPU $6.50** |

**Pricing rationale:**
- Lower than Audible ($14.95) and Storytel (~$13) to reduce friction in a developing market
- $2.99 entry point removes the "too expensive" objection for Ukrainian audience
- $6.99 is the sweet spot — most features, most likely tier for engaged users


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

### Why Publishers Should Say Yes

1. Zero upfront cost to them — no production needed (we use existing recordings)
2. Monthly automated report with full transparency
3. Growing platform = growing royalties over time
4. Ukrainian market alternative to piracy — legitimate revenue stream
5. Access to user engagement data (which books, which chapters people actually finish)

---

## Cost Structure

MVP Phase (Jul–Aug 2026, ~2 months)
ItemCostAI Developer (2 months × $2,000)$4,000
Vibe coding tools $240
Supabase Free tier - dev phase(when published -$25/m, when we will have large base of users - $599/m) 
OpenAI API (testing during dev)$50
App Store annual fee$99
Google Play one-time$25
Legal (publisher contracts)$400
Figma + design tools$30
Domain + misc$50
Total MVP~$4,894

Ongoing Monthly Costs (Post-Launch, around september 2026+)
Item               0–300 users   300–800 users      800–2,000 users 
AI Developer       $2,000            $2,000            $2,000
Coding subs~       $120              $120              $120AI 
API — GPT-4o-mini  $15               $80               $220
Supabase Pro       $50               $75               $150
Audio CDN          $80               $180              $400
Firebase FCM push  $0                $0                $0          прорахувати 
App Store ($99/yr)
### MVP Phase (Months 1–2, ~$6,000)

| Item | Cost |
Ai-dev tools and other subscriptions for app function. Total for 6 months ~$13.919
MArketing for 6 months - $34.000
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

APRU - $6.50 
BEP ~ 630 users 

### Realistic Scenario


Period                      Paying                  UsersNet               Monthly Revenue           Monthly CostsNet

Month 1–2 (Sep–Nov 2026) 


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
