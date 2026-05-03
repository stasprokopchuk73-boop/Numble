# 🛠 Product Concept — Nimble

## Vision

Transform audiobook listening from passive entertainment into an active, social, and educational experience — powered by AI that knows exactly where you are in the book.

---

## MVP Scope (2 months)

The MVP focuses on the core loop that makes Nimble unique: **listen → understand → retain**.

---

## What's IN the MVP

### 1. 🎧 Smart Audio Player

The player is the foundation. It needs to feel as polished as Audible or Spotify from day one — because if the core listening experience is poor, nothing else matters.

- Play / pause
- 15s rewind, 30s forward skip
- Chapter navigation (⏮ ⏭)
- Variable playback speed (0.75x, 1x, 1.25x, 1.5x, 2x)
- Scrubable progress bar with thumb indicator
- Real book page equivalent tracker (e.g. "Page 184 of 412")
- Sleep timer (15 min, 30 min, end of chapter)
- Car mode — enlarged controls, minimal UI, one-tap interaction
- Progress shown as both time remaining and percentage

---

### 2. 🤖 AI Chat Assistant (Core Differentiator)

The AI assistant is the heart of Nimble. It operates under two strict rules that no competitor has implemented:

**Rule 1 — Position Awareness**

Every user session stores current reading state:

```json
{
  "user_id": "u_123",
  "book_id": "b_456",
  "current_chapter": 7,
  "current_position_seconds": 8040,
  "equivalent_page": 184
}
```

This context is injected into every AI query automatically.

**Rule 2 — Spoiler Prevention**

System prompt instructs the model:

> "You are a reading assistant for [Book Title]. The user is currently at Chapter 7, page 184 of 412. You must NEVER reference events, characters, or plot points that occur after this position. If asked about future events, politely decline and explain why."

**What users can ask:**
- "Who is this character?"
- "What does this word mean?"
- "Explain what just happened"
- "What's the historical context of this scene?"
- "Is this based on real events?"
- "Why did this character do that?"

**Chat UI:**
- Compact AI pill button on main player screen — one tap to open
- Bottom sheet slides up covering ~75% of screen
- Mini player strip stays visible at top while chat is open
- AI responses stream token-by-token — user sees it thinking in real time
- Session history saved per book
- Close button returns to full player without losing position

---

### 3. ✂️ Clip & Note System

**Clip (one tap during playback):**
- Saves current timestamp automatically
- Auto-transcribes last 15–30 seconds
- Tagged with book title and chapter

**Manual Notes:**
- Save words with AI-generated definition
- Save sentences or quotes
- Free-form notes tied to a specific book position
- Notes Library tab — organized and filterable by book

---

### 4. 🔁 AI Spaced Repetition via Push Notifications

The AI reads the user's notes library and sends smart daily push notifications:

- "Remember 'іманентний' from Майстер і Маргарита? What does it mean?"
- User answers in notification or taps to open app
- AI evaluates the response and adjusts repetition frequency
- Based on SM-2 algorithm — same as Anki and Duolingo

Key **daily retention driver** — brings users back even between books.

---

### 5. 🔥 Streak System

- Tracks consecutive days of listening
- Visible on home screen
- Duolingo's streak is their #1 cited retention mechanic
- Simple: a number and a fire emoji — no complex gamification needed in MVP

---

### 6. 📚 Catalog — 15 Books at Launch

- Mix of Ukrainian public domain classics and 2–3 contemporary titles via revenue-share agreements
- Each book: cover image, author, narrator, total duration, genre tags, chapter list
- Browse and search on Library tab

---

### 7. 👥 Basic Social Layer

- Add friends via username or phone number
- See friends' current book and reading progress percentage
- Leave emoji reactions on friends' progress updates
- Simple activity feed: "Аліna finished Chapter 5 of 1984"

*Full comments and discussion threads pushed to v1.1*

---

## What's NOT in MVP (v1.1+)

| Feature | Reason |
|---|---|
| Dynamic AI voice narration with character voices | Most complex feature — separate R&D needed |
| AI-generated sound effects | Requires audio pipeline not needed for core loop |
| Voice input for AI chat | Text covers 95% of use cases at MVP stage |
| Book recommendations AI | Needs usage data first — add post-launch |
| Full comment threads | Reactions-only social is faster to ship |
| CarPlay / Android Auto | Add when user base justifies it |
| Publisher analytics dashboard | PDF royalty reports sufficient for MVP |

---

## UX Principles (Don Norman's Design of Everyday Things)

Every screen decision in Nimble follows three principles:

**1. Affordances** — Every element communicates its function visually. The play button is circular and elevated — it looks pressable. The progress bar has a visible thumb — it looks scrubbable. The AI pill is outlined not filled — secondary to the player, clearly tappable.

**2. Mapping** — Controls follow spatial logic. 15s rewind is on the left, 30s forward is on the right. The AI chat slides up from the bottom — the natural gesture for "reveal more." Notes are one tap from the player without losing listening context.

**3. Feedback** — Every action confirms itself immediately. Progress bar updates in real time. Notes save with a micro-animation. AI responses stream token-by-token. Streak increments with a small animation each day.

---

## Technical Architecture

```
┌────────────────────────────────────────┐
│         React Native App               │
│    (iOS + Android, single codebase)    │
│         Built via vibe coding          │
└───────────────┬────────────────────────┘
                │
┌───────────────▼────────────────────────┐
│           Supabase Backend             │
│  - Auth (email + Google Sign-In)       │
│  - PostgreSQL (users, books, notes,    │
│    listening events, friendships)      │
│  - Real-time (friends activity feed)   │
│  - Storage (audio files, covers)       │
└───────────────┬────────────────────────┘
                │
┌───────────────▼────────────────────────┐
│             AI Layer                   │
│  - Google Gemini API (chat assistant)  │
│  - OpenAI Whisper (clip transcription) │
│  - GPT-4o-mini (spaced repetition      │
│    question generation)                │
└───────────────┬────────────────────────┘
                │
┌───────────────▼────────────────────────┐
│         Push Notifications             │
│  - Firebase Cloud Messaging (FCM)      │
└────────────────────────────────────────┘
```

---

## Royalty Tracking System

Every listening session fires an event every 30 seconds:

```javascript
listening_event({
  user_id: "u_123",
  book_id: "b_456",
  publisher_id: "pub_789",
  start_timestamp: 8010,
  end_timestamp: 8040,
  duration_seconds: 30
})
```

Monthly royalty calculation:

```
royalty_owed = (publisher_minutes / total_minutes) × (monthly_revenue × royalty_rate)
```

Exported as PDF per publisher. Transparent, auditable, automated from day one.
