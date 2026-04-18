[![GitHub](https://img.shields.io/badge/GitHub-Cameraptor-181717?logo=github)](https://github.com/Cameraptor)
[![License](https://img.shields.io/badge/License-MIT-21c134.svg)](LICENSE)
[![Node.js](https://img.shields.io/badge/Node.js-20+-339933?logo=nodedotjs&logoColor=white)](https://nodejs.org)
[![Platform](https://img.shields.io/badge/Platform-Win%20%7C%20Mac%20%7C%20Linux-blue)]()
[![Telegram](https://img.shields.io/badge/Telegram-Community-2CA5E0?logo=telegram)](https://t.me/voogieboogie)

# Dreamina Monitor — Real-Time AI Generation Dashboard & Best Agent Prompter for Seedance 2.0

### The visual command center for [JiMeng / Dreamina CLI](https://jimeng.jianying.com/cli). Expert prompt system included. Monitor like a director. Pay the lowest prices on Earth.

---

### Why This Exists

[JiMeng (即梦)](https://jimeng.jianying.com/) by ByteDance is the most cost-effective AI video generation platform in the world. **Seedance 2.0** produces cinema-grade results at a fraction of what Western platforms charge — and it keeps getting better.

JiMeng offers [an official CLI](https://jimeng.jianying.com/cli) that unlocks the full power of the platform from the terminal. The CLI is excellent — 8 generation types, multiple models, reference images, videos, audio, multi-frame narratives — everything you need.

**But the CLI is blind.** You submit a task, get a `submit_id`, and then... nothing. No visual feedback. No queue position. No way to see your results without manually running `query_result` for each task. No thumbnails of your references. No way to compare outputs side by side.

**Dreamina Monitor gives the CLI its eyes.**

Now combine this with **AI coding agents** (Cursor, Windsurf, Codex, any IDE agent) that can write expert Seedance 2.0 prompts automatically using our included `seedance` prompt skill — and you get the most powerful, most convenient, and most affordable AI video production pipeline available today.

```
Agent writes prompt → CLI submits to JiMeng → Monitor shows it live → You review like a director
```

**One file. Zero dependencies. Self-configuring. Auto-selects free port. Works on any OS.**

**Team:** [Cameraptor](https://cameraptor.com/voogie) | **Author:** Voogie

---

![Dreamina Monitor — Boot Sequence](assets/dreamina_loading.jpg)

---

## The Problem

**The JiMeng web interface** works for casual browsing, but for serious production work it becomes a bottleneck. The site is overloaded and slow — pages lag, the UI feels heavy, asset management is clunky, sorting through generations is tedious, and there's no batch download. It's a consumer-grade UI trying to serve power users, and it shows.

**The Dreamina CLI** is the answer for power users — fast, scriptable, full API access. But it's completely blind. You submit tasks into a void. No visual feedback, no queue position, no thumbnails, no way to quickly scan your results. You end up context-switching between terminal and file browser constantly.

**If you use AI agents** to write prompts and submit generations, you have zero visual feedback. You're directing a film with your eyes closed.

---

## The Solution

**Dreamina Monitor** bridges the gap: all the power of the CLI, with a real-time visual dashboard that makes you feel like a director in a control room.

```bash
node monitor.js
# → http://localhost:3333 (auto-selects free port if busy)
```

![Dreamina Monitor — Main View](assets/dreamina_view.jpg)

*Every card: model, ratio, duration, credit cost, full prompt with copy, all reference files as clickable thumbnails, video result with hover-to-play, download + like.*

---

## The Director's Experience

This is built for people who generate dozens of videos per session and need to review them fast:

- **Hover-to-play** — scrub through results without clicking. Like reviewing dailies on a Moviola.
- **Gallery grid** — see 24+ generations at once. Spot the best take instantly.
- **Lasso select** — drag to select a batch, download all at once. No more one-by-one.
- **Save to any folder** — native directory picker. Organize by project, scene, take.
- **Like the best** — heart your favorites, filter by Liked tab, batch download liked.
- **Full prompt on every card** — always know exactly what produced what.
- **Input thumbnails** — see your reference images and videos right on the card. Never lose track of what you fed the model.
- **Queue position + ETA** — know exactly when your generation will be ready. Plan your time.
- **Sound + push notifications** — step away, get notified when it's done.

This is the best experience for working with Seedance 2.0. Period.

---

## What You Get vs. Raw CLI

| | Raw Dreamina CLI | With Dreamina Monitor |
|---|---|---|
| **Submit** | Terminal command → submit_id | Same — but now you SEE it appear live |
| **Queue** | No visibility | Exact position #4,231 / 141,681 + progress bar + ETA |
| **Reference files** | Forgotten after submit | Thumbnails of all inputs on every card |
| **Results** | `query_result --submit_id=...` manually | Hover-to-play video, one-click download |
| **Batch work** | One file at a time | Lasso-select → download all at once |
| **Credits** | `dreamina user_credit` manually | Always visible + session spending breakdown |
| **History** | Scroll through CLI output | Full dashboard with filters, sort, search by type |
| **Comparison** | Open files separately | Gallery grid — all results on one screen |
| **Favorites** | Remember the submit_id... | Heart button, Liked tab, batch download liked |
| **Notifications** | Check terminal | Sound beep + push notification when done |
| **Agent workflow** | No visual feedback | Full visual loop without leaving IDE |

---

## Every Feature

### Real-Time Monitoring
- **Auto-refresh** every 15/30/60 seconds — flicker-free DOM diffing, no page reload
- **Live queue position** with progress bar + ETA countdown (~500-900 positions/minute)
- **Processing shimmer** animation for active tasks
- **Dynamic tab title** — `(3 active) Dreamina Monitor` — see status without switching tabs
- **Sound alerts** — distinct beeps for success and failure (Web Audio, zero files)
- **Push notifications** — browser notification when a generation completes in background
- **Session timer** — running clock showing total session duration
- **Credit balance** — always visible in header with Today / 7d / All spending breakdown

### Cards & Content
- **Full prompt** on every card with expand/collapse and one-click copy
- **Input file thumbnails** — all reference images, videos, audio shown as clickable previews with labels (@1, @2...)
- **Video hover-to-play** — instant preview without clicking. Click for fullscreen lightbox
- **Image lightbox** — fullscreen viewer with arrow key navigation
- **Model info** — model name, aspect ratio, duration displayed as chips
- **Credit cost** per task — estimated for queued, actual for completed
- **Task ID** — click to copy submit_id for CLI reuse
- **Color-coded status** — green/yellow/red dots with status text

### Views
- **Expanded list** — full card with all details, prompt, inputs, result, controls
- **Gallery grid** — compact thumbnail grid for visual scanning
- **Filter tabs** — All / Active / Done / Failed / Liked
- **Type filter** — dropdown by generation type (text2video, img2video, multimodal, etc.)
- **Sort** — by status priority, newest, or oldest
- **Ghost detection** — zombie tasks auto-detected and collapsible

### Download & Workflow
- **One-click download** — to default or custom folder
- **Save As** — choose destination with native directory browser
- **Batch select** — lasso drag or Shift+click multiple cards
- **Batch download** — all selected results at once
- **Retry failed** — copies prompt for resubmit
- **Hide zombie tasks** — clean up stuck or cancelled generations
- **Likes** — heart any generation, persists across sessions
- **Download all liked** — batch export your best work

### Design & UX
- **Hacker boot sequence** — ASCII art terminal startup with animated status lines
- **Breathing radar grid** — animated canvas background, auto-pauses when tab hidden
- **Dark theme** — Raptor Green (#21C134) on deep black, built for long sessions
- **Embedded fonts** — Cormorant Garamond, Raleway, DM Mono
- **Cameraptor branding** — custom embedded logo and favicon
- **Auto port selection** — if 3333 is busy, finds next free port automatically
- **Responsive** — 13" laptops to 32" monitors

---

![Dreamina Monitor — Gallery Grid](assets/dreamina_previews.jpg)

*Gallery grid: scan all generations at a glance. Hover to play. Green hearts = liked. Each card shows model, ratio, duration, cost.*

---

## Quick Start

### 1. Install Node.js

Download from [nodejs.org](https://nodejs.org/) — version 20 or higher.

### 2. Clone & Run

```bash
git clone https://github.com/Cameraptor/Dreamina-CLI-Monitor-For-Jimeng-.git
cd Dreamina-CLI-Monitor-For-Jimeng-

node monitor.js
```

### 3. Open Dashboard

The URL prints in terminal (default: **http://localhost:3333**).

**No `npm install`. No build step. No config. One file = one app.**

### First Launch Auto-Setup

On first run, the monitor automatically:
1. Detects your OS (Windows / macOS / Linux + ARM64)
2. Checks for Dreamina CLI — **downloads and installs it if missing**
3. Verifies login — shows setup banner with instructions if not
4. Starts polling for your generations

---

## Supported Generation Types

The monitor tracks all Dreamina CLI generation types:

| Type | CLI Command | What it does |
|------|-------------|-------------|
| Text to Video | `text2video` | Prompt → video |
| Image to Video | `image2video` | Single image + prompt → video |
| Frames to Video | `frames2video` | First + last keyframe → interpolated video |
| Multi-Frame | `multiframe2video` | 2-20 images → coherent video narrative |
| Multimodal | `multimodal2video` | Images + videos + audio → video (flagship) |
| Text to Image | `text2image` | Prompt → image |
| Image to Image | `image2image` | Image + prompt → transformed image |
| Image Upscale | `image_upscale` | Upscale to 2K / 4K / 8K |

### Models

| Model | Type | Cost |
|-------|------|------|
| `seedance2.0_vip` | Video | VIP 15s 720p = 210 cr, 1080p = 495 cr |
| `seedance2.0` | Video | 15s 720p = 120 cr |
| `seedance2.0fast` | Video | 15s 720p = 75 cr (fast, lower quality) |
| `seedance2.0fast_vip` | Video | 15s 720p = 165 cr (VIP-fast) |
| `5.0` / `4.6` / `4.5` / `lab` | Image | Various quality tiers |

Video ratios: `16:9` `9:16` `1:1` `4:3` `3:4` `21:9` | Duration: **4-15 seconds** | Resolution: 720p

---

## The Agent Superpower

The real magic: combine Dreamina Monitor with AI coding agents.

```
You (in IDE) → AI Agent → Dreamina CLI → JiMeng API
                                              │
              Dreamina Monitor ◄──────────────┘
              (localhost:3333)    reads CLI logs
```

1. **Prompt** — ask your agent to write a Seedance 2.0 prompt (the `seedance` skill generates expert-level prompts automatically)
2. **Submit** — agent runs `dreamina text2video --prompt="..." --model=seedance2.0_vip`
3. **Monitor** — generation appears on dashboard in real-time with queue position
4. **Review** — hover-to-play the video, check reference images, compare in gallery
5. **Iterate** — tweak prompt in agent, resubmit, compare side by side
6. **Export** — download the best results with one click or batch

**You never leave your IDE.** The monitor is your visual feedback loop.

### Works With Any Agent or IDE

Cursor, Windsurf, GitHub Copilot, Codex CLI — anything that can run shell commands. The `seedance` and `dreamina` skills work with any agent that supports custom skill files.

---

## Included AI Agent Skills

### Seedance Prompt Skill (`skills/seedance/`)

A complete prompt engineering system for Seedance 2.0. Activates automatically when you ask your agent to write video prompts.

| Module | What it covers |
|--------|---------------|
| **SKILL.md** | Master prompt formula, 3 modes (PROMPT/GENERATE/DUAL), @ reference system |
| **camera-motion.md** | All shot types: dolly, crane, orbit, Hitchcock zoom, chase choreography |
| **character-consistency.md** | Face lock, multi-character, style transfer |
| **video-extension.md** | Forward/backward extension, scene insertion |
| **commercial-ads.md** | Ad creation, product showcases, multi-language localization |
| **editing-effects.md** | Character swaps, VFX transfer, beat-synced montages |
| **one-take-storytelling.md** | Continuous one-take shots, multi-shot narrative |
| **audio-lipsync.md** | Voice cloning, dialogue, lip sync, music, SFX |
| **prompt-templates.md** | 20+ ready-to-use templates by category |
| **community-patterns.md** | 20 curated best prompts from 190+ community submissions |

### Dreamina CLI Skill (`skills/dreamina/`)

Direct generation submission from your agent. Handles command selection, VIP model usage, image compression, queue tracking, and auto-integration with the monitor.

---

## Architecture

```
monitor.js (~2700 lines — the entire application)
│
├── Node.js HTTP Server (localhost only, auto port)
│   ├── /api/status          → all tasks with enriched details
│   ├── /api/credits         → JiMeng account balance
│   ├── /api/thumb           → serve local input file thumbnails
│   ├── /api/track-inputs    → link reference files + model to task
│   ├── /api/download        → download generation result
│   ├── /api/like            → toggle task like
│   ├── /api/settings        → user preferences
│   ├── /api/setup-status    → health check (Node, CLI, auth)
│   └── + 6 more endpoints
│
├── Auto-Tracker (every 3 seconds)
│   └── Parses ~/.dreamina_cli/logs/ → model, ratio, duration, input files
│
└── Frontend (zero external dependencies)
    └── Embedded HTML + CSS + JS + SVG + favicon
```

| Decision | Why |
|----------|-----|
| **Single file** | Zero setup. `node monitor.js` — done. |
| **No npm** | No node_modules, no supply chain risk |
| **No framework** | Vanilla Node.js HTTP. No Express, no React. |
| **No Electron** | 150MB Electron vs **1.1MB** monitor.js |
| **Localhost only** | Your data never leaves your machine |

---

## For AI Agents — Self-Setup Guide

If you are an AI agent reading this repository:

1. **Run the monitor:** `node monitor.js` — self-configures on first launch
2. **Submit generations:** use Dreamina CLI (see [DREAMINA_CLI.md](DREAMINA_CLI.md))
3. **Write prompts:** load `skills/seedance/` for Seedance 2.0 prompt engineering
4. **Dashboard URL** prints in terminal — tell the user to open it
5. **JSON files** are auto-managed — do not edit manually

```bash
# Key commands
dreamina login                    # Auth (opens browser)
dreamina user_credit              # Check balance
dreamina text2video \
  --prompt="..." \
  --model=seedance2.0_vip \
  --ratio=16:9 --duration=15      # Submit generation

dreamina multimodal2video \
  --prompt="@Image1 as env..." \
  --image="ref1.jpg" \
  --image="ref2.jpg" \
  --model=seedance2.0_vip          # With references
```

---

## Supported Platforms

| Platform | Status |
|----------|--------|
| Windows 10/11 (x64) | Fully supported |
| macOS Intel | Supported |
| macOS Apple Silicon (M1-M4) | Supported |
| Linux x64 | Supported |

---

## Roadmap

| Version | Status | What |
|---------|--------|------|
| **v1.0** | Done | Dashboard, cards, filters, gallery, lightbox, batch download |
| **v1.1** | Done | Settings, likes, notifications, session stats, radar grid |
| **v1.2** | Done | Cross-platform, self-configuring, auto-download CLI |
| **v1.3** | Next | Standalone `.exe` / binary — double-click to run |
| **v2.0** | Planned | Side-by-side comparison, tags, prompt search, WebSocket |

Full details in [ROADMAP.md](ROADMAP.md).

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| CLI not found | `curl -s https://jimeng.jianying.com/cli \| bash` then restart terminal |
| Not logged in | `dreamina login` — opens browser for auth |
| No tasks | Submit something: `dreamina text2video --prompt="test" --model=seedance2.0_vip` |
| Thumbnails missing | Reference files must exist at original paths on disk |
| Content filter | Remove brand names, soften descriptions — credits refunded on rejection |
| Queue slow | Normal at peak: ~500-900 positions/min. VIP models may be faster |

---

## Legal & Compliance

**Dreamina Monitor is 100% legal and does not violate JiMeng/Dreamina platform rules.**

- **Uses only the official Dreamina CLI** — published by JiMeng (ByteDance) at [jimeng.jianying.com/cli](https://jimeng.jianying.com/cli), designed for programmatic access
- **No reverse engineering** — reads CLI logs and calls the same public API the CLI uses
- **No scraping** — zero interaction with the JiMeng web interface
- **No credential theft** — authentication via `dreamina login`, the official flow
- **Personal use tool** — a convenience dashboard for your own account and files
- **The CLI exists for this** — ByteDance published it for developers and creators to build workflows. This is that workflow.

Not affiliated with ByteDance, JiMeng, or Dreamina. Independent open-source tool.

---

## Support & Community

- **Telegram:** [Join @voogieboogie](https://t.me/voogieboogie)
- **Issues:** [GitHub Issues](https://github.com/Cameraptor/Dreamina-CLI-Monitor-For-Jimeng-/issues)
- **Website:** [cameraptor.com/voogie](https://cameraptor.com/voogie)

---

## License

MIT License — see [LICENSE](LICENSE) file for details.

---

## 致即梦团队和中国用户

我们对即梦（JiMeng）团队和字节跳动怀有最深的敬意与感谢。

Seedance 2.0 是当今世界上最令人印象深刻的 AI 视频生成模型之一。它所展现的技术实力、创新速度和对创作者的赋能，代表了中国科技领域最前沿的成就。

即梦平台以无与伦比的性价比，将世界级的 AI 能力带给了全球创作者。官方 CLI 工具的开放精神，让开发者能够自由构建工作流，这正是我们创建 Dreamina Monitor 的灵感来源。

我们向即梦团队的工程师、研究员和设计师致以崇高的敬意。向中国用户社区致敬——你们的创意和反馈推动着这项技术不断进步。

感谢中国在人工智能领域的卓越贡献和技术领导力。你们正在塑造未来。

**谢谢。** 🙏

---

<p align="center">
  <a href="https://cameraptor.com/voogie">
    <img src="assets/cameraptor_logo.png" alt="Cameraptor" width="280">
  </a>
</p>

<p align="center">
  <em>We're a team of passionate artist-researchers creating bespoke projects<br>at the intersection of art and cutting-edge technology.</em>
</p>

<p align="center">
  <em>Where boundaries end, we build portals.</em>
</p>
