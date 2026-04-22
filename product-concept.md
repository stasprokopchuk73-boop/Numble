# 🛠 Product Concept — Nimble

## Vision

Transform audiobook listening from passive entertainment into an active, social, and educational experience — powered by AI that knows exactly where you are in the book.

---

## MVP Scope (2 months, ~$6,000 budget)

The MVP focuses on the core loop that makes Nimble unique: **listen → understand → retain**.

### What's IN the MVP

#### 1. 🎧 Smart Audio Player
- Full playback controls: play/pause, 15s rewind, 30s forward
- Chapter navigation (⏮ ⏭)
- Variable playback speed (0.75x, 1x, 1.25x, 1.5x, 2x)
- Sleep timer (15 min, 30 min, end of chapter)
- Car mode (large buttons, minimal UI)
- Audio progress bar with scrubbing
- Real book page equivalent tracker (e.g. "Page 184 of 412")

#### 2. 🤖 AI Chat Assistant (Core Differentiator)

The AI assistant is the heart of Nimble. It operates under two strict rules:

**Rule 1 — Position Awareness**
Every user session stores:
```
{
  user_id: "xxx",
  book_id: "yyy",
  current_chapter: 7,
  current_position_seconds: 8040,
  equivalent_page: 184
}
```
The AI receives this context with every query.

**Rule 2 — Spoiler Prevention**
System prompt instructs the model:
> "You are a reading assistant for [Book Title]. The user is currently at Chapter 7, page 184 of 412. You must NEVER reference events, characters, or plot points that occur after this position. If asked about future events, politely decline."

**What users can ask:**
- "Who is this character?"
- "What does this word mean?"
- "Explain what just happened"
- "What's the historical context of this scene?"
- "Is this based on real events?"

**Chat UI:**
- Bottom sheet that slides up over the player (takes ~75% of screen)
- Mini player visible at top while chat is open
- Text + voice input options
- Session history saved per book

#### 3. ✂️ Clip & Note System

**Clip:** One-tap button during playback saves:
- Timestamp
- Auto-transcribed text of the moment (via AI)
- Book + chapter reference

**Note:** Users can manually add:
- Words (with definition)
- Sentences / quotes
- Paragraphs
- Free-form notes about any moment

All notes are organized in a **Notes Library** tab, filterable by book.

#### 4. 🔁 AI Spaced Repetition (Push Notifications)

The AI studies the user's notes library and sends smart push notifications:

- "Hey, remember *'іманентний'* from Майстер і Маргарита? What does it mean?"
- Sends a question → user answers in the notification or opens app
- AI evaluates the answer and adjusts repetition frequency
- Based on SM-2 spaced repetition algorithm

This feature is the key **retention driver** — it brings users back daily without them finishing a new book.

#### 5. 📚 Catalog (15 Books at Launch)

Initial catalog strategy:
- Mix of Ukrainian classics (public domain where possible)
- 2–3 contemporary Ukrainian titles via revenue-share agreements with publishers
- Curated selection across genres: literary fiction, thriller, non-fiction

Each book has: cover, author, narrator, duration, genre tags, chapter list.

#### 6. 👥 Basic Social Layer

- Add friends via username or phone
- See friends' current book + progress percentage
- Leave emoji reactions on friends' progress
- Simple activity feed ("Аліна just finished Chapter 5 of 1984")

*Full comments and discussion features pushed to v1.1*

---

## What's NOT in MVP (v1.1+)

- Dynamic AI voice narration with character voices
- AI-generated sound effects
- Full comment threads
- Book recommendations AI
- CarPlay / Android Auto integration
- Publisher analytics dashboard

---

## UX Principles (based on Don Norman's Design of Everyday Things)

Every design decision in Nimble follows three Norman principles:

**1. Affordances** — Every interactive element looks like it should be interacted with. The play button is circular and elevated. The progress bar has a visible thumb. The AI button is a distinct pill — clearly tappable, clearly secondary to the player.

**2. Mapping** — Controls are spatially logical. Rewind is on the left, forward is on the right. The chat slides up from the bottom (natural mobile gesture). Notes are accessible from the player without leaving context.

**3. Feedback** — Every action has immediate visual confirmation. Progress updates in real time. Notes save with a micro-animation. AI responses stream token-by-token so users see it "thinking."

---

## Technical Architecture

```
┌─────────────────────────────────────┐
│           React Native App          │
│  (iOS + Android, single codebase)   │
└──────────────┬──────────────────────┘
               │
┌──────────────▼──────────────────────┐
│           Supabase Backend          │
│  - Auth (email + Google)            │
│  - PostgreSQL (users, books, notes) │
│  - Real-time (friends activity)     │
│  - Storage (audio files)            │
└──────────────┬──────────────────────┘
               │
┌──────────────▼──────────────────────┐
│           AI Layer                  │
│  - Google Gemini API (chat)         │
│  - OpenAI Whisper (transcription)   │
│  - Firebase (push notifications)    │
└─────────────────────────────────────┘
```

---

## Royalty Tracking System

Every listening event is logged:

```javascript
// Event fired every 30 seconds during playback
listening_event({
  user_id: "u_123",
  book_id: "b_456",
  publisher_id: "pub_789",
  start_timestamp: 8010,
  end_timestamp: 8040,
  duration_seconds: 30
})
```

Monthly automated report calculates:
- Total minutes per publisher
- Revenue share owed = (publisher_minutes / total_minutes) × (revenue × royalty_rate)
- Exported as PDF report for each publisher

This makes the royalty model transparent, automated, and audit-ready from day one.
