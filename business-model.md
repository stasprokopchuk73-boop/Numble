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
Firebase FCM push  $0                $0                $0          
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


Period                     Paying Users                 Net Monthly Revenue               Monthly Costs          Net

Month 1 (Jul 2026)          0                           $0                                $4500                  -$4,500                                                
Month 2 (Aug 2026)          0                           $0                                $4500                  -$4,500
Month 3 (Sep 2026)          90                          $350                              $2,443                 -$2,093 
Month 4 (Oct 2026)          296                         $1,152                            $2,443                 -$1,291
Month 5 (Nov 2026)          401                         $1,560                            $2,443                 -$883 
Month 6 (Dec 2026)          466                         $1,814                            $2,443                 -$629

### Optimistic Scenario 


Period                     Paying Users                 Net Monthly Revenue               Monthly Costs          Net

Month 1 (Jul 2026)          0                           $0                                $4500                  -$4,500                                                
Month 2 (Aug 2026)          0                           $0                                $4500                  -$4,500
Month 3 (Sep 2026)          300                         $1,167                            $2,443                 -$1,276
Month 4 (Oct 2026)          650                         $2,529                            $2,443                 +$86
Month 5 (Nov 2026)          900                         $3,501                            $2,443                 +$1,058
Month 6 (Dec 2026)          1.100                       $4,279                            $2,443                 +$1,836

---

Marketing spends for 6 months 

Month 1 (Jul 2026) $1,500
Month 2 (Aug 2026) $2,500
Month 3 (Sep 2026) $10,000
Month 4 (Oct 2026) $7,000
Month 5 (Nov 2026) $7,000
Month 6 (Dec 2026) $7,000

---

