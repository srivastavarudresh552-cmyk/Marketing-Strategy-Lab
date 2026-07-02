# Think Like a Marketing Strategist: Grow This Brand

An interactive, single-file web app that teaches beginners how marketers *think* — not just how to generate marketing content. Every step explains **what** a strategic decision is and **why** it matters, then has the user make that decision for a real (or randomly generated) brand.

---

## What this is

A guided simulation that walks a user through a full marketing strategy engagement, end to end:

1. **Welcome** — a short primer on what "marketing strategy" actually means
2. **Choose your path**
   - 🏢 **Use My Own Business** — enter a real or planned business
   - 🙋 **Build My Personal Brand** — no business yet? Use your name, expertise, and story as the brand
   - 🎲 **A New Client Has Arrived** — get a randomly generated business brief (industry, audience, budget, competitors, challenge)
3. **Understand the brand & audience** — teaches what a target audience is and why it's the foundation of everything else
4. **Choose platforms** — pick up to 3 social platforms, each scored and explained for fit against the audience (personal brand mode weights LinkedIn, X/Twitter, YouTube, and newsletters more heavily)
5. **Choose content pillars** — pick exactly 3 recurring content themes from a pool that adapts to the mode (personal mode includes Thought Leadership, Personal Story, Wins & Lessons, Audience Education)
6. **30-day roadmap** — four weekly strategic phases (not a post-by-post calendar); Week 1 adapts to "define your POV & optimize your bio" for personal brands
7. **Unexpected event** — a random curveball (viral post, podcast invite, public disagreement, a copycat, a price war, etc.) with multiple response options and real consequences
8. **Growth Report** — a final summary: audience understanding, platform strategy, content strategy, a growth-potential score, the single best decision made, the biggest mistake, and three marketing lessons tailored to the mode

After every major section, a pinned **"How to ask Claude"** note card gives a reusable, copyable prompt so the user also picks up prompt-engineering skills alongside marketing skills.

The whole experience is **replayable** — hitting "Take on a new brand" resets the flow and, in random-client mode, generates a fresh business each time.

---

## Tech stack

- **React 18** (via CDN, UMD build)
- **Babel Standalone** (in-browser JSX transform — no build step)
- Plain **HTML/CSS/JavaScript** — no Tailwind, no npm, no backend, no external APIs
- Single `.html` file — everything (markup, styles, data, logic) lives in one document

## How to run it

1. Download `marketing-strategist.html`
2. Open it in any modern browser (Chrome, Edge, Firefox, Safari) by double-clicking it or dragging it into a browser window
3. That's it — no server, no install, no build step

**Note on internet access:** the file loads React, ReactDOM, and Babel from a CDN (`cdn.jsdelivr.net`) the first time it runs, so an internet connection is needed at load time even though there's no backend or API involved afterward. If your network blocks that CDN, the page won't render — check your network/firewall settings if it fails to load.

## Design notes

- Dark, modern "strategy war-room" visual style: near-black canvas, gold and teal accents, `Space Grotesk` for headings, `Inter` for body copy, `IBM Plex Mono` for data/labels
- A progress rail across the top always shows where the user is in the 8-step flow
- All state lives in React `useState`/`useMemo` in memory — nothing is saved between sessions, and closing the tab resets everything
- Fully responsive, down to mobile widths

## Customizing / extending

Everything is data-driven from a handful of arrays and objects near the top of the `<script type="text/babel">` block, so it's easy to extend without touching the UI code:

| To change... | Edit... |
|---|---|
| The pool of randomly generated businesses | `INDUSTRIES` array |
| Platform scoring logic / explanations | `PLATFORM_META`, `PERSONAL_WEIGHTS`, `DEFAULT_WEIGHTS`, `CATEGORY_KEYWORDS` |
| Content pillar options | `PILLAR_SHARED`, `PILLAR_BUSINESS`, `PILLAR_PERSONAL` |
| The 30-day roadmap copy | `buildRoadmap()` |
| Unexpected events and their consequences | `BUSINESS_EVENTS`, `PERSONAL_EVENTS` |
| Final marketing lessons | `PERSONAL_LESSONS`, `BUSINESS_LESSONS` |
| Growth Report scoring logic | `buildReport()` |
| "How to ask Claude" prompts | the `prompt` variable inside each screen component |
