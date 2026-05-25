# World Cup 2026 — Juicer Opportunity

**Author:** Denis
**Date:** 2026-05-12
**Status:** Brainstorming / for discussion

---

## TL;DR

The 2026 FIFA World Cup (June 11 – July 19) opens in **30 days** on Juicer's home turf — the tournament is hosted across the US, Canada, and Mexico. This is a once-in-a-cycle moment to pull three goals at once: **promote the new public API, drive new signups, and grow revenue from existing customers.** This document is a menu of ideas to discuss, not a finished plan.

---

## Why this matters now

- **First 48-team format** → more nations engaged than any prior World Cup → long-tail country/team hashtags to mine.
- **Hosted in our largest market.** US fans will engage online at a scale they never have before.
- **We just shipped the public API.** Perfect coincidence — gives us a credible "show, don't tell" moment for developers.
- **Tight window.** 30 days to kickoff. Anything we ship has to be small, focused, and reuse what we already have.

---

## Three goals, one campaign

The strategic insight: one campaign can pull all three levers if the artifacts reinforce each other.

| Goal | What moves the needle |
|---|---|
| **Promote the API** | A real public site built ON the API that we open-source as a starter repo |
| **New signups** | SEO traffic on country/team queries + "embed this on your site" CTAs everywhere |
| **Revenue** | Pre-built templates that activate new users fast + plan-upgrade prompts when usage spikes |

---

## Idea menu

Grouped by area. Pick the ones we have capacity for; the rest become input for future tournaments (Euros 2028, LA Olympics 2028, etc.).

### 🟦 Product — inside the dashboard

- **World Cup template gallery.** One-click feeds: per country (`#TeamUSA`, `#Mondiali`, `#LesBleus`…), per group, per match-day hashtag, plus an "all fans" master feed. 30-second time-to-value.
- **Pre-tuned moderation defaults** for football fan content (slur lists, brigading flags, NSFW). Default-on for World Cup templates.
- **In-app trending hashtag suggestions** during the tournament — show "trending football tags right now" when an existing customer creates a new source.
- **Match-day mode** — temporary refresh-rate boost for accounts running World Cup feeds (or pitch it as a Pro upsell).
- **"Country picker" UI element** for embedded feeds — let visitors swap between countries on a single embed. Distinctive widget, demos well.

### 🟦 Marketing — public-facing

- **juicer.io/worldcup hub.** A free public site with a feed per country, master feed, match-day rolling reels. Every embed on the page links back to "embed this on your site" / signup.
- **Country landing pages.** SEO play — "world cup 2026 fan reactions [country]" has massive search volume during the tournament.
- **Daily "trending moments" content** on Juicer socials, drawn from the hub's data. Free fuel for 32 days of organic content.
- **"Goal of the day" / "Best fan reactions" widget** that customers can embed and we share back as social proof.
- **Email campaign** to existing customers — "Add a World Cup feed in 30 seconds" before kickoff.
- **Paid acquisition** ($5–10k budget) targeting sports bars, hospitality, and tourism boards on LinkedIn + Reddit football subs.

### 🟦 Sales — outbound

Target verticals where a fan wall is genuinely useful for 30 days:

- **Host city tourism boards** — NYC, LA, Miami, Dallas, Atlanta, Toronto, Mexico City, Vancouver, Seattle, Boston, Philadelphia, Kansas City…
- **Sports bar chains** — Buffalo Wild Wings, BrewDog, Hooters, regional sports bar groups, BWWGo.
- **Supporters' clubs** — official US Soccer fan club, country-specific supporters' clubs in the US.
- **Travel + hospitality** — Airbnb host networks in host cities, hotel groups serving inbound fans.
- **Sports media + blog networks** — fan-wall widgets under article comments / live blogs.
- **Brand activations** — sponsors running UGC campaigns (#MyTeam, branded hashtag walls).
- **Offer:** time-limited "World Cup Pack" — 30-day free Starter/Pro with the template pre-loaded. Convert what stays post-tournament.

### 🟦 Developer / API

- **Open-source starter repo** — `juicer-io/worldcup-starter`. A clean Next.js / Bolt template that mirrors the hub. Easy to fork, hosted on Vercel.
- **Blog post:** "How we built juicer.io/worldcup with our own API in N days." Cross-post to Hacker News, dev.to, r/webdev, r/nextjs.
- **API docs landing page** for the World Cup use case — copy-paste examples in 3 languages.
- **Sponsor a "build with Juicer API" prize** in a developer community already doing it (Vercel templates gallery, Bolt.new featured, etc.). Cheap PR for the API.
- **Public Postman / Insomnia collection** for the API, pre-populated with World Cup endpoints.

### 🟦 Brand / PR

- **Case studies during the tournament.** Every bar / tourism board running a Juicer wall = case study material.
- **Post-tournament report.** "What 50M fans tweeted during the World Cup, visualized." Aggregated insights from our own data — keeps SEO juice flowing into 2027.
- **Influencer / micro-influencer push.** Light spend on football creators sharing fan walls during high-moment matches.
- **Press pitch** — to MarTech / SaaS press, framing Juicer as the engagement-layer of the tournament.

---

## Risks and things to figure out

| Risk | What it means | Mitigation |
|---|---|---|
| **FIFA / World Cup IP** | "FIFA," official marks, trophy imagery, kit logos are off-limits | Use generic "World Cup," country names, public hashtags. Legal pass before anything goes public. |
| **View-limit blowouts** | A bar with a fan wall during a goal spikes views hard | Pre-flag affected customer accounts. Proactive upgrade outreach at 70% usage. |
| **Refresh rate ceiling** | Free plan = 24hr refresh, useless for live fan walls | Use as a natural upgrade trigger in template gallery copy. |
| **Moderation load** | Fan content during high-emotion matches = worst of social media | Default-on moderation for WC templates. Pitched as a feature, not a fix. |
| **API stress-test** | OSS repo + dev community traffic will expose any rough edges | Audit docs and rate limits *now*. Fix in next 2 weeks, not on launch day. |
| **Hub infra costs** | We pay social platform API costs + bandwidth on free traffic | Budget as marketing spend, not infrastructure cost. |

---

## What I think we should do (recommendation)

If we want all three goals, the minimum viable bet is:

1. **Dashboard template gallery** — small effort, every existing customer benefits, becomes permanent infrastructure for future tournaments.
2. **juicer.io/worldcup hub** — SEO + brand + the canvas for the API showcase.
3. **Open-source starter repo** — almost free to extract from the hub, gives us the developer story.
4. **Outbound sales push** — list of ~50 target accounts, templated email, 1 person for 2 weeks.

Everything else is upside. Paid acquisition, influencer push, press pitches, etc., can be added if budget is available — but the four items above carry the campaign on their own.

---

## Decision points for the CEO / team

These are the calls that need to be made this week before anything ships:

1. **Are we in?** Yes / no / scaled-down version.
2. **Engineering capacity for the next 30 days.** Is there ~1 engineer × 2-3 weeks available, or do we cut to the dashboard-only version?
3. **Marketing budget.** $0, $5k, $10k? Determines whether paid acquisition is in scope.
4. **Owner.** Who runs this end-to-end? (Not "which team" — which named person.)
5. **Legal pass on FIFA IP.** Who does it, by when?
6. **Existing customers in football / sports** — who do we talk to first as the design partner?

Maybe Idea for AI Hackhaton???

---

## What this becomes after July

The framework we build for the World Cup gets reused for:

- **UEFA Euro 2028** (June 2028)
- **LA Olympics 2028**
- **Super Bowl LX** (Feb 2026 — already passed) → LXI (Feb 2027)
- **Copa América 2028**
- Any future tentpole event with a hashtag

The investment isn't 30 days of work — it's the start of an "events playbook" that pays off every tournament cycle.

---

*Open for discussion. Bring questions, push back on the recommendations.*
