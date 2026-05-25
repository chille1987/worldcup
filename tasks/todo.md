# World Cup 2026 — Juicer Demo Project

**Goal:** Internal pitch material for the Juicer team. A small Next.js site with 3–4 demo pages that show what a juicer.io/worldcup campaign could feel like, all powered by the real Juicer API.

**Audience:** Juicer CEO / team. Not public-ready. Polish enough to be convincing, not so much we waste a week on copy.

---

## Stack

- Next.js (App Router) + TypeScript + Tailwind
- Server Components fetch from Juicer API via a thin server-side client (`lib/juicer.ts`)
- API key in `.env.local` (`JUICER_API_KEY`) — never exposed to the browser
- Deployable to Vercel for sharing the link with the team

---

## Juicer API surface we'll use

| Endpoint | Purpose |
|---|---|
| `POST /authorize` | Get our demo API key |
| `GET /platforms` | Know which platforms accept hashtags vs handles |
| `GET /posts/lookup` | Ad-hoc hashtag pulls (Spain page, live page) — no feed creation |
| `POST /feeds` + `POST /feeds/{id}/sources` | Persistent feed for the bar demo |
| `GET /feeds/{id}/posts` | Filtered post pulls (date range, text search) |
| `GET /feeds/{id}/embed-snippets` | "What a bar pastes into their site" |

---

## Pages to build

### `/` — index
One-screen overview: "3 demos showing what Juicer could do for World Cup 2026." Three cards linking to the demos. Lifts the framing from `world-cup-2026-juicer-ideas.md`.

### `/spain` — country team prep demo
- **Pitch:** "Embed a fan-reaction wall for a single national team."
- **Hashtags:** `#SeleccionEspañola`, `#RFEF`, `#VamosEspaña`, `#LaRoja`, player names (Lamine Yamal, Rodri, Pedri).
- **UI:** Spain red/yellow header, country picker (US, Mexico, Brazil, France, England, Germany, Argentina, Spain) — clicking swaps the hashtag set without reloading.
- **Side panel:** "How this works" — shows the actual API call (`GET /posts/lookup?term=...`) so the team sees it's real.

### `/live` — match-day mode demo
- **Pitch:** "Goal-of-the-day / live fan reactions wall."
- **Filter:** posts from last 90 minutes containing "GOOOL", "GOAL", goal emojis, "⚽", team mentions.
- **UI:** Scoreboard chrome at top (mock score, minute), reactions stream below, auto-refresh every 15s.
- **Toggle:** "Live mode" vs "Post-match recap" (last 24h, top-engagement only).

### `/bar` — sports bar pitch demo
- **Pitch:** "What a Buffalo Wild Wings location gets when they paste one line of code."
- **UI:** TV-shaped frame (16:9) showing a giant tap-friendly fan wall — designed for a screen on a wall, not a laptop.
- **Sidebar:** the actual embed snippet from `GET /feeds/{id}/embed-snippets`, copy-paste ready.
- **Below the fold:** "Cold email template" — the actual outreach copy we'd send to bar chains from the .md target list.

### `/spec` (optional, if time) — API showcase strip
Stripped-down developer page: every API call this site makes, with the response payload visible. The "show, don't tell" artifact for the public-API goal.

---

## Build order

1. **Scaffold** Next.js + Tailwind in `worldcup/app/`. Add `lib/juicer.ts` with typed wrappers for the 6 endpoints above. Mock data fallback when no API key is set.
2. **`/spain`** — the reference implementation. Once this looks good, the others follow the same pattern.
3. **`/live`** — clone /spain, swap filter logic, add scoreboard chrome.
4. **`/bar`** — different chrome (TV frame), embed-snippet sidebar, email template block.
5. **`/`** — index page tying them together.
6. **README** explaining how to run it and what the team is looking at.

---

## What we're NOT doing (yet)

- Real production polish (mobile responsive nice-to-have, not required)
- Real legal pass on FIFA IP (decision point in the .md, not our problem)
- Actual outreach automation (we hand over the email template, that's it)
- The dashboard template gallery from the .md (that lives inside Juicer's product, not in this demo repo)

---

## Open questions before I start

1. Do you already have a Juicer API key, or should we mock everything until you grab one?
2. Should the bar demo use a real existing chain (Buffalo Wild Wings branding) or a fictional "The Pitch Bar" to avoid trademark issues on the demo itself?
3. OK to commit this as a fresh git repo under `worldcup/`?

---

## Review

**Built (2026-05-25):**
- Scaffold: Next.js 15.5 + React 19 + Tailwind 3, builds clean (6 static pages).
- `lib/juicer.ts` — typed wrapper around `/posts/lookup`, fan-out helper, auto mock fallback when `JUICER_API_KEY` is unset.
- `lib/mock-data.ts` — deterministic mock fixtures (Spain / live / bar templates).
- `lib/countries.ts` — 8 nations (Spain, USA, Mexico, Brazil, France, England, Germany, Argentina), each with hashtags + players + theme.
- `/` — index with three demo cards + live/mock status badge.
- `/spain` — country picker swaps 8 teams via `?team=` query param, themed header, fan wall, sidebar with the exact API call.
- `/live` — match-day mode, dark theme, scoreboard chrome (mock Spain 1-0 France), AutoRefresh client component (15s), live/recap toggle.
- `/bar` — "The Pitch Bar" fictional brand, 16:9 TV chrome with 3×N wall grid, copy-block for embed snippet + cold-email template.

**Next moves if we keep going:**
1. Wire real `JUICER_API_KEY` and validate that `/posts/lookup` response shape matches our normalizer.
2. README with the pitch context for the Juicer team viewer.
3. Polish: real bar photos, mobile responsiveness pass, a small `/spec` page enumerating every API call.
4. Decision: extract this as the OSS starter repo mentioned in `world-cup-2026-juicer-ideas.md` § Developer.

