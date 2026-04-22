# 📖 Nimble — AI-Powered Audiobook Platform

> *Listen smarter. Learn deeper. Share the journey.*

Nimble is an AI-native audiobook app that transforms passive listening into an active learning experience. Built for Ukrainian-speaking users first, designed to scale globally.

---

## 🔥 The Problem

Current audiobook apps (Audible, Apple Books, Абук) treat listening as a one-way experience. Users:
- Hear words but don't retain knowledge
- Can't ask questions about what they're listening to
- Have no tools to capture and review key ideas
- Listen in isolation with no social layer

**Result:** People finish books but remember almost nothing. The audiobook stays passive entertainment instead of becoming a learning tool.

---

## 💡 The Solution — Nimble

Nimble wraps every audiobook with an AI layer that knows exactly where you are in the book and helps you understand, retain, and discuss it — without spoilers.

### Core Features (MVP)

| Feature | Description |
|---|---|
| 🎧 Smart Player | Full-featured player with 15s/30s skip, speed control, car mode, sleep timer |
| 🤖 AI Assistant | In-app chat that answers questions about the book — spoiler-free, position-aware |
| 📝 Clip & Note | One tap to clip a moment and save it to your personal notes |
| 📚 Notes Library | Saved words, quotes, paragraphs — organized by book |
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

**Primary:** Ukrainian-speaking readers aged 16–35, both in Ukraine and diaspora
**Secondary:** Post-MVP expansion to other Eastern European languages

---

## 📊 Traction & Validation

- Concept validated through CusDev interviews with potential users
- Identified clear pain point: users finish audiobooks but retain little
- No direct competitor in Ukraine offers AI-assisted audiobook listening
- Pre-launch content presence being built across TikTok, Instagram, Threads

---

## 🗺 Roadmap

```
Month 1-2  →  MVP Development (player + AI chat + notes + 15 books)
Month 2-3  →  Beta testing with 50-100 users
Month 3    →  App Store + Google Play launch
Month 4-6  →  Content marketing, organic growth, publisher partnerships
Month 6+   →  Friends features, spaced repetition push, Series B features
```

---

## 👤 Founder

**Stas** — Producer & Marketer
Building Nimble as first startup. Running organic content strategy across social platforms during development phase (YouTube, TikTok, Instagram, Threads).

---

## 📁 Repository Structure

```
/
├── README.md               ← You are here
├── market-research.md      ← Ukrainian & global audiobook market data
├── product-concept.md      ← Full product spec & UX decisions
├── business-model.md       ← Pricing, royalties, financial projections
└── /design                 ← UI prototypes and design decisions
```
