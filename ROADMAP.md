# Dreamina Toolkit — Roadmap

## Концепция

**Один пакет — три инструмента:**

```
dreamina-toolkit/
├── monitor.js              ← Дашборд (GUI). Кликнул → открылся.
├── skills/
│   ├── dreamina/           ← Claude Code Skill: CLI submit, track, download
│   │   └── SKILL.md
│   └── seedance/           ← Claude Code Skill: промпт-система Seedance 2.0
│       ├── SKILL.md
│       ├── 00_seedance-rules.md
│       ├── 02_camera-motion.md
│       ├── 03_character-consistency.md
│       ├── 04_editing-effects.md
│       ├── 05_video-extension.md
│       ├── 06_commercial-ads.md
│       ├── 07_one-take-storytelling.md
│       ├── 08_community-patterns.md
│       └── 09_audio-lipsync.md
├── install.sh / install.bat ← Установка: CLI + скиллы + автостарт
├── start.sh / start.bat     ← Запуск монитора
└── README.md
```

**Два способа запуска:**
1. Кликнул `start.bat` / `start.sh` → монитор в браузере
2. Из Claude Code → скиллы доступны автоматически (установка через `install`)

**Установщик (`install`) делает:**
- Проверяет/скачивает dreamina CLI
- Копирует скиллы в `~/.claude/skills/`
- Создаёт ярлык для монитора
- Настраивает автостарт (опционально)

---

## v1.0 — Current (2026-04-04)

Single-file Node.js dashboard. Windows only. Всё работает.

### Done
- Dashboard: cards, filters, sort, pagination, ghost filtering
- Auto-track CLI logs → model/ratio/duration/input files
- Compact gallery grid + expanded view
- Lasso drag-select, shift+click, selection mode
- Gallery lightbox with arrow navigation
- Estimated credits from pricing table
- Hide zombie tasks
- Download + batch download with overlay
- Cameraptor brand (embedded logo + fonts)
- Flicker-free auto-refresh

---

## v1.1 — Polish & Settings (Done — 2026-04-04)

- [x] Settings modal: auto-refresh interval (15s/30s/60s/off)
- [x] Sound notifications (Web Audio beep on success/fail)
- [x] Browser push notifications (background tab)
- [x] Session stats — credits spent with Today/7d/All period switcher
- [x] Favicon (Cameraptor hieroglyph via /api/favicon)
- [x] Dynamic tab title with active count
- [x] Empty state → link to "?" info modal
- [x] Canvas: breathing radar distortion grid, pauses when tab hidden
- [x] Likes system (pulled from v2.0): heart on cards, Liked tab, persist, lightbox
- [x] Design audit: warm text (#e8e4dc), --green-hover, gold→green unification

---

## v1.2 — Self-Configuring & Cross-Platform (Done — 2026-04-04)

- [x] PLATFORM_CONFIG: auto-detect OS (win32/darwin/linux) + ARM64
- [x] PATH separator handling (`;` vs `:`)
- [x] Auto-download Dreamina CLI per platform, chmod on Unix
- [x] Startup health check: Node ≥20, port, CLI, login
- [x] Setup banner + login flow in dashboard UI
- [x] Health panel in settings modal
- [x] Dynamic safePrefixes (HOME-based)
- [x] Default settings merge + validation
- [x] Product CLAUDE.md, README.md, AGENTS.md for public repo
- [x] Skills (seedance, dreamina) packaged for distribution
- [x] publish.sh with pre-checks and skills copy

**Нет нужды в webapp/Electron.** Node.js + браузер = кроссплатформа нативно.
Dreamina CLI сам по себе кроссплатформенный (Win/Mac/Linux бинарник).

---

## v1.3 — Standalone Executable

Цель: двойной клик → всё работает. Можно дать коллеге.

- [ ] `npx pkg monitor.js --targets node18-win-x64` → `.exe`
- [ ] `npx pkg monitor.js --targets node18-macos-arm64` → Mac binary
- [ ] Auto-open browser on start
- [ ] Setup wizard (first launch): check CLI, download if missing, login
- [ ] Tray icon (optional, via native-notify or similar)
- [ ] Auto-update check (compare version with remote)

---

## v2.0 — Advanced Features

### Comparison & Review
- [ ] Side-by-side comparison mode (2-4 videos)
- [ ] Star/rate generations (persist rating)
- [ ] Tags/labels on generations (for organizing)
- [ ] Search by prompt text
- [ ] Filter by date range

### Prompt Integration
- [ ] Show prompt diff between related generations
- [ ] "Regenerate with edit" — copy prompt + open editor
- [ ] Prompt templates library (quick-fill from saved templates)
- [ ] Link to Seedance prompt docs from card

### Workflow
- [ ] Auto-download on success (configurable)
- [ ] Watch folder → auto-submit (drop image → generate)
- [ ] Queue management — drag to reorder priority
- [ ] Export session report (CSV/JSON)
- [ ] Discord/Telegram notification webhook

### Performance
- [ ] Lazy load cards (virtual scroll for 100+ tasks)
- [ ] Thumbnail cache (don't re-serve unchanged files)
- [ ] WebSocket instead of polling (real-time updates)

---

## Architecture Notes

### Why one file?
- Zero setup: `node monitor.js` and done
- Easy to distribute: one file = one app
- No npm, no node_modules, no build step
- Embedded assets = works offline
- Easy to package with `pkg`

### Why not Electron?
- 150MB Electron bundle vs 1.1MB monitor.js
- Node.js already has HTTP server
- Browser is already installed everywhere
- No native UI needed — pure web dashboard

### Why not a web app (hosted)?
- Needs local file access (input thumbnails, downloads)
- Needs local CLI access (dreamina binary)
- Privacy: API keys and generated content stay local
- Works offline / on-premise

### Migration path if needed
If requirements change:
1. **Tauri** (Rust+WebView) — 5MB binary, native feel, local file access ✓
2. **Neutralino** — 2MB binary, similar to Tauri
3. **Never Electron** — too heavy for what this does
