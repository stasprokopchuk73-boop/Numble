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

### 2. 🤖 AI Chat Assistant 

The AI assistant is the heart of Nimble. It operates under two strict rules that no competitor has implemented:

**1 — Position Awareness**

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

**2 — AI Voiceover and Spoiler Prevention**

1. Voice Switching
The AI analyzes the text in real time and identifies speaker turns — narrator, protagonist, secondary characters. 
Each character is assigned a distinct TTS voice via ElevenLabs API. When a character speaks, the voice switches automatically. 
When narration resumes, it returns to the default narrator voice.

2. The AI reads scene context and generates ambient sound effects that play underneath the narration. A door scene gets a creak. A rainstorm gets rain. A crowd scene gets ambient noise. Effects are generated via ElevenLabs Sound Effects API and mixed at low volume under the main audio track.


Anti-Spoiler System
Every user session tracks an exact reading position:
json{
  "user_id": "u_123",
  "book_id": "b_456",
  "current_chapter": 7,
  "current_position_seconds": 8040,
  "equivalent_page": 184
}

This position is the hard boundary. 
When a user asks the AI anything, the system checks every piece of information it would return against this boundary before responding.

If the answer requires knowledge of events, characters, or plot points beyond page 184 — the system blocks that portion of the response automatically, regardless of how the question is phrased.

"user: "Does Woland turn out to be the devil?"
system check: → this information exists at page 310
system check: → user is at page 184
system check: → 310 > 184 → BLOCK
response: "I can't answer that yet — it would spoil what's ahead.
           Ask me again when you get further into the book."
           
The AI only draws from the content the user has already heard. It knows the full book — but it deliberately restricts itself to the user's current window. The further the user listens, the more the AI can answer.


**Chat UI:**
- Compact AI pill button on main player screen — one tap to open
- Bottom sheet slides up covering ~75% of screen
- Mini player strip stays visible at top while chat is open
- AI responses stream token-by-token — user sees it thinking in real time
- Session history saved per book
- Close button returns to full player without losing position

---

### 3. ✂️ Note System


**Manual Notes:**
- Save words with AI-generated definition
- Save sentences or quotes
- Free-form notes tied to a specific book position
- Notes Library tab — organized and filterable by book

---

### 4. 🔁 AI Spaced Repetition via Push Notifications

The AI reads the user's notes library and sends smart daily push notifications:

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

- Mix of different genres of books: fiction, non-fiction, detective, thriller.
- Each book: cover image, author, narrator, total duration, genre tags, chapter list
- Browse and search on Library tab

---

### 7. 👥 Basic Social Layer

- Add friends via username or phone number
- See friends' current book and reading progress percentage
- Leave emoji reactions on friends' progress updates
- Simple activity feed: "Аліna finished Chapter 5 of 1984"


---

## What's NOT in MVP 

| Feature | Reason |
|---|---|
| Voice input for AI chat | Text covers 95% of use cases at MVP stage |
| Book recommendations from AI | Needs usage data first — add post-launch |
| Full comment threads | Reactions-only social is faster to ship |
| CarPlay / Android Auto | Add when user base justifies it |
| Publisher analytics dashboard | PDF royalty reports sufficient for MVP |

---

## UX Principles (Tooke inspirations and instructions from Don Norman's Design of Everyday Things)


**1. Affordances** — Every element communicates its function visually. The play button is circular and elevated — it looks pressable. The progress bar has a visible thumb — it looks scrubbable. The AI pill is outlined not filled — secondary to the player, clearly tappable.

**2. Mapping** — Controls follow spatial logic. 15s rewind is on the left, 30s forward is on the right. The AI chat slides up from the bottom — the natural gesture for "reveal more." Notes are one tap from the player without losing listening context.


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
