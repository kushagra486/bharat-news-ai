<div align="center">

# 🇮🇳 Bharat News AI

### *Live AI-Powered Daily Intelligence — Built for India*

[![Live Demo](https://img.shields.io/badge/🌐%20Live%20Demo-GitHub%20Pages-2ea44f?style=for-the-badge)](https://kushagra486.github.io/bharat-news-ai/)
[![GitHub Stars](https://img.shields.io/github/stars/kushagra486/bharat-news-ai?style=for-the-badge&color=e91e8c)](https://github.com/kushagra486/bharat-news-ai/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/kushagra486/bharat-news-ai?style=for-the-badge&color=9333ea)](https://github.com/kushagra486/bharat-news-ai/network)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)
[![Made in India](https://img.shields.io/badge/Made%20in-India%20🇮🇳-FF9933?style=for-the-badge)](https://github.com/kushagra486)

<br/>

> **4 Live News Sources · Groq Llama 3.3 70B AI Analysis · Supabase Auth · Instagram-Style UI**

<br/>

<img src="https://raw.githubusercontent.com/kushagra486/bharat-news-ai/main/logo.png" alt="BharatNews.ai" width="420"/>

<br/>

[![🌐 Visit Live Site](https://img.shields.io/badge/🌐%20Visit%20Live%20Site-BharatNews.ai-e91e8c?style=for-the-badge&logo=googlechrome&logoColor=white)](https://kushagra486.github.io/bharat-news-ai/)

</div>

---

## ✨ Features

### 📰 Live News
| Feature | Description |
|---------|-------------|
| **4 Live Sources** | GNews · NewsData.io · The Guardian · NewsAPI.org — fetched in parallel |
| **🇮🇳 India Tab** | Dedicated India news via NewsData `country=in` |
| **🔴 Breaking News** | Auto-detected breaking headlines with live banner |
| **हिंदी Feed** | Hindi news from India via `language=hi` |
| **Live Search** | Real-time search across NewsAPI + GNews simultaneously |
| **Infinite Scroll** | Load more with pagination tokens |
| **Auto-Refresh** | Feed refreshes every 15 minutes silently |
| **Smart Deduplication** | Round-robin merge across 4 sources, title-based dedup |

### 🤖 AI Intelligence (Groq)
| Feature | Description |
|---------|-------------|
| **Deep Analysis** | Per-article: summary · sentiment · key points · timeline · implications |
| **AI Story Clustering** | Groq groups related articles into story clusters |
| **Daily Briefing** | AI-synthesised 3-sentence intelligence brief every morning |
| **Research Mode** | Ask any question — AI answers using today's live news as context |
| **Reading Time** | Word-count based estimate on every card |

### 👤 User System
| Feature | Description |
|---------|-------------|
| **Supabase Auth** | Email/password signup, login, logout, forgot password |
| **Email Verification** | Verified / Unverified badges with re-send option |
| **Profile Page** | Avatar, bio, profession, location, DOB, website |
| **Cross-device Sync** | Bookmarks · Likes · Read history · Preferences via Supabase |
| **Guest Mode** | Browse without account — localStorage fallback |

### 📱 UI / UX
| Feature | Description |
|---------|-------------|
| **Instagram-style** | Stories row, tiled cards, bottom nav on mobile |
| **3 Responsive Layouts** | Desktop 3-col · Tablet 2-col · Mobile full-screen |
| **Dark / Light Mode** | Toggle with `Ctrl+D`, persisted to localStorage |
| **Stories Viewer** | Per-sector stories with progress bars, tap zones, auto-advance |
| **Article Reader** | In-app reader with TTS audio (play/pause/speed) |
| **Share as Image** | Export any article as a branded PNG via html2canvas |
| **Keyword Alerts** | Browser push notifications when articles match keywords |
| **PWA** | Installable on Android & iOS via "Add to Home Screen" |
| **Keyboard Shortcuts** | `Ctrl+K` search · `Ctrl+D` theme · `←→` stories |

---

## 🛠️ Tech Stack

```
Frontend      Vanilla HTML5 · CSS3 · JavaScript (no framework)
AI Engine     Groq API — Llama 3.3 70B Versatile (free tier)
Auth & DB     Supabase (Auth + PostgreSQL + Storage)
News APIs     GNews · NewsData.io · The Guardian · NewsAPI.org
Images        Unsplash (fallback) + real article images
Hosting       GitHub Pages (free, auto-deploy on push)
Share         html2canvas (CDN)
```

---

## 🗄️ Database Schema (Supabase)

```sql
profiles      — id, name, email, bio, profession, location, dob,
                website, avatar_url, avatar_initials, email_verified,
                sector_preferences[], created_at, updated_at

bookmarks     — id, user_id, article_id, article_data (JSONB), created_at
likes         — id, user_id, article_id, created_at
user_prefs    — user_id, prefs (JSONB), alert_keywords[], updated_at
read_history  — id, user_id, article_id, read_at
```

All tables have **Row Level Security** — users can only access their own data.

---

## 🔑 API Keys (Free Tier)

| Service | Free Limit | Used For |
|---------|-----------|---------|
| [Groq](https://console.groq.com) | Generous free tier | AI analysis, clustering, briefing |
| [GNews](https://gnews.io) | 100 req/day | Global headlines + images |
| [NewsData.io](https://newsdata.io) | 200 req/day | India news, breaking, Hindi |
| [The Guardian](https://open-platform.theguardian.com) | Unlimited (free) | Premium journalism |
| [NewsAPI.org](https://newsapi.org) | 100 req/day | 100+ source aggregation |
| [Supabase](https://supabase.com) | 500MB DB, 1GB storage | Auth + user data |

**Total monthly cost: ₹0**

---

## 🚀 Deployment

### GitHub Pages (Current — Recommended)
```
Automatic — every push to main branch deploys in ~60 seconds
URL: https://kushagra486.github.io/bharat-news-ai/
```

### Self-host (Any static server)
```bash
# Just copy index.html to any web server
# nginx, Apache, S3, Cloudflare Pages — all work

# Cloudflare Pages (free, faster than GitHub Pages)
npm install -g wrangler
wrangler pages deploy . --project-name=bharat-news-ai
```

---

## 📐 Architecture

```
Browser
  ├── 4 News APIs (parallel fetch, 15-min cache)
  │     ├── GNews API           → gnews.io/api/v4
  │     ├── NewsData.io         → newsdata.io/api/1
  │     ├── The Guardian        → content.guardianapis.com
  │     └── NewsAPI.org         → newsapi.org/v2
  │
  ├── Groq AI (on-demand)
  │     ├── Article analysis    → llama-3.3-70b-versatile
  │     ├── Story clustering    → JSON structured output
  │     └── Daily briefing      → 3-sentence synthesis
  │
  └── Supabase
        ├── Auth                → email/password + JWT sessions
        ├── PostgreSQL          → user data, bookmarks, prefs
        └── Storage             → avatar images
```

---

## 🗂️ File Structure

```
bharat-news-ai/
├── index.html          # Complete app (single file, ~175KB)
├── README.md           # This file
├── setup-database.html # One-click Supabase table creator
└── .gitignore
```

---

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl + K` | Focus search |
| `Ctrl + D` | Toggle dark/light mode |
| `→` | Next story |
| `←` | Previous story |
| `Esc` | Close any modal |

---

## 🔐 Supabase Setup

1. Create project at [supabase.com](https://supabase.com)
2. Go to **Authentication → URL Configuration**
3. Set **Site URL**: `https://kushagra486.github.io/bharat-news-ai/`
4. Add **Redirect URL**: `https://kushagra486.github.io/bharat-news-ai/`
5. Run `setup-database.html` in your browser to create all tables
6. Update the Supabase URL and anon key in `index.html`

---

## 📊 Sectors Covered

🌐 All News · 💻 Technology · 📈 Finance · 🏥 Health · 🔬 Science · 🏛️ Politics · 🌍 Climate · ⚽ Sports · 🇮🇳 India

---

## 🤝 Contributing

```bash
git clone https://github.com/kushagra486/bharat-news-ai.git
cd bharat-news-ai
# Open index.html in browser — no build step needed
```

PRs welcome for: new news sources, UI improvements, AI features, bug fixes.

---

## 📜 License

MIT © [Kushagra](https://github.com/kushagra486) — free to use, modify and distribute.

---

<div align="center">

**Built with ❤️ for India**

[![GitHub](https://img.shields.io/badge/GitHub-kushagra486-181717?style=flat-square&logo=github)](https://github.com/kushagra486)
[![Groq](https://img.shields.io/badge/Powered%20by-Groq%20⚡-orange?style=flat-square)](https://groq.com)
[![Supabase](https://img.shields.io/badge/Database-Supabase-3ECF8E?style=flat-square&logo=supabase)](https://supabase.com)
[![GitHub Pages](https://img.shields.io/badge/Hosted%20on-GitHub%20Pages-222?style=flat-square&logo=github)](https://pages.github.com)

*Star ⭐ this repo if you find it useful!*

</div>
