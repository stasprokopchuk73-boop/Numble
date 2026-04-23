# 📖 Nimble — AI-Powered Audiobook Platform

Nimble is an AI-based audiobook app that helps users to learn through an interactive listeting. 
---

##  Market problem

Current audiobook apps (Audible, Apple Books, Storytel )
- Don't have an interactive voice over
- Can't give answears to users questions about the book
- Have no tools to help you get new knowledge 
- Listening in isolation with no social layer

**Result:** People finish books but don't rememder a lot. The audiobook becomes a background tool rather than an learing instrument.

---

## 💡 The Solution — Nimble

Nimble will feature an AI-assitant that knows exactly where you are in the book and helps you understand, retain, and discuss it - without spoilers.

### Core Features (MVP)

| Feature | Description |
|---|---|
| 🎧 Smart Player | Full-featured player with 15s/30s skip, speed control, car mode, sleep timer |
| 🤖 AI Assistant | In-app chat that answers questions about the book - spoiler-free, position-aware |
| 📝 Clip & Note | One tap to clip a moment and save it to your personal notes |
| 📚 Notes Library | Save words, quotes, paragraphs - and learn them with AI |
| 🔁 AI Repetition | Push notifications that quiz you on your saved notes using spaced repetition |
| 👥 Friends & Progress | Add friends, see their reading progress, leave reactions and comments |
| 📖 Real Page Tracker | Shows your equivalent page number in the physical book alongside audio progress |

### How the AI Works

The AI assistant has two key constraints that make it unique:

1. **Position-aware** — it knows exactly which chapter and page you're on
2. **Spoiler-blocked** — it refuses to reveal plot points beyond your current position

This means users can freely ask "Who is this character?" or "What does this word mean?" without fear of ruining the story.

---

## 🛠 Tech Stack (Planned)

| Layer | Technology |
|---|---|
| Frontend (iOS/Android) | React Native via vibe coding |
| Backend | Node.js + Supabase |
| AI Layer | Google Gemini API / OpenAI GPT-4o |
| Audio Streaming | Custom player with HLS |
| Push Notifications | Firebase Cloud Messaging |
| Analytics & Royalty Tracking | Custom event logging per `book_id` + `publisher_id` |

---

## 🎯 Target Market

**Primary:** Ukrainian-speaking readers aged 16–45, both in Ukraine and diaspora
**Secondary:** Post-MVP expansion to other Eastern European languages

---

## 📊 Traction & Validation

- Concept validated through CusDev interviews with potential users
- Exciting problem: users don't retain much knowledge after listening to the book.
- No direct competitor in audiobook market.
- Pre-launch content presence being built across TikTok, Instagram, Threads, Youtube, Linkedln.

---

## 🗺 Roadmap

```
1. MVP Development (player + AI chat + notes + 15 books)
2. Beta testing with users
3. App Store + Google Play launch
4. Content marketing, organic growth, publisher partnerships
5. Friends features, spaced repetition push, Series B features

```

## 📁 Repository Structure

```
/
├── README.md               ← You are here
├── market-research.md      ← Ukrainian & global audiobook market data
├── product-concept.md      ← Full product spec & UX decisions
├── business-model.md       ← Pricing, royalties, financial projections
└── /design                 ← UI prototypes and design decisions
```
