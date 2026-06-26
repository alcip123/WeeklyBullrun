# The Weekly Bullrun — Claude Instructions

## What This Project Is
A weekly financial markets newsletter at weeklybullrun.com, authored by Alessio Cipriano. Articles cover underrepresented economic topics that have a specific, traceable mechanism affecting equity markets. Published in plain HTML/CSS with no frameworks or build tools.

## Repository
GitHub: https://github.com/alcip123/WeeklyBullrun
Hosted on: GitHub Pages (custom domain weeklybullrun.com)
DNS: Cloudflare (DNS-only, not proxied)

## File Structure
- `index.html` — homepage with hero (latest issue) + archive list. All links to the homepage use `href="/"` not `href="index.html"`
- `archive.html` — full archive page
- `about.html` — about page
- `issue-01.html` through `issue-XX.html` — individual articles
- `CNAME` — contains `weeklybullrun.com`

## How to Add a New Issue
1. Copy `issue-01.html` exactly (all CSS, all HTML structure)
2. Name it `issue-XX.html` (next number in sequence)
3. Update only: page title, article-title, article-deck, article-meta date, all h2 headings and p paragraphs, plain-english section
4. Update `index.html`: change hero to new issue, add article-row above `<!-- NEW ISSUES GO HERE -->`. Use `href="/"` for all homepage links, never `href="index.html"`
5. Update `archive.html`: add article-row above `<!-- NEW ISSUES GO HERE -->`
6. Push to `draft/issue-XX` branch, open a non-draft PR to main
7. Send Telegram notification to bot (see below)
8. Alessio approves by merging the PR on GitHub — no Claude Code needed

## Reading Progress Bar (REQUIRED on every issue page)
Every issue HTML must include this CSS inside `<style>`:
```css
html { scroll-timeline: --page-scroll block; }
@keyframes grow-progress {
  from { transform: scaleX(0); }
  to { transform: scaleX(1); }
}
#progress {
  position: fixed;
  left: 0; top: 0;
  width: 100%; height: 3px;
  background: #111;
  transform-origin: 0 50%;
  animation: grow-progress auto linear;
  animation-timeline: --page-scroll;
  z-index: 999;
}
```
And this as the first element inside `<body>`:
```html
<div id="progress"></div>
```

## Telegram Notification
Bot token: 8977925657:AAFu1voH6uVtdGGSFtU36D_bP58h_RaXqW8
Chat ID: 8958825048
Send via:
```bash
curl -s -X POST "https://api.telegram.org/bot8977925657:AAFu1voH6uVtdGGSFtU36D_bP58h_RaXqW8/sendMessage" \
  -d "chat_id=8958825048" \
  --data-urlencode "text=MESSAGE_HERE"
```
Telegram has a 4096 character limit per message. Split into multiple messages if needed.

## Automated Routine
Routine ID: trig_019DYrnrBdf7PdxwpeNRh1yH
Schedule: Tuesday and Friday at 9am ET (13:00 UTC) — cron: `0 13 * * 2,5`
The routine researches a topic, writes the article, pushes a PR, and sends a Telegram message.
Manage at: https://claude.ai/code/routines/trig_019DYrnrBdf7PdxwpeNRh1yH

## Topic Selection Rules
- Must be underrepresented — NOT in mainstream news (no Fed decisions, S&P 500, big tech earnings, CPI, jobs reports)
- Must have a specific, traceable mechanism by which it affects equity markets
- Must be researchable with real attributable data
- Good areas: credit market stress, sector supply shocks, regulatory shifts repricing industries, hidden liquidity dynamics, commodity cycles with equity knock-ons, commercial real estate, regional bank stress, insurance market dislocations, shipping/logistics cost pass-throughs

## Issues Published So Far (do not repeat these topics)
- Issue #01 (Jun 19, 2026): SPR releases and oil supply — Hormuz closure, strategic petroleum reserve depletion
- Issue #02 (Jun 22, 2026): Private credit / BDCs — mark-to-model accounting, PIK income, redemption gates
- Issue #03 (Jun 22, 2026): Commercial real estate — CMBS delinquency vs. bank book values, extension wave ending
- Issue #04 (Jun 22, 2026): Homeowners insurance — 9% of monthly payment, homebuilder margin compression
- Issue #05 (Jun 26, 2026): Farm debt record — China export collapse, community bank exposure, farmland collateral
- Issue #06 (Jun 26, 2026): Apple/tech price hikes — AI memory shortage, HBM capacity grab, consumer electronics repricing

---

## Article Writing Rules (APPLY TO EVERY ARTICLE — NO EXCEPTIONS)

### Journalistic Standards
1. Truth over persuasion
2. Clarity over cleverness
3. Specificity over generalization
4. Evidence over opinion
5. Brevity over verbosity

Every sentence must justify its existence.

### Voice
Confident without false certainty. Analytical, not promotional. Precise, not dramatic. Accessible to an educated general audience.

### Language Rules
- Concrete nouns and strong verbs
- Short, direct sentences — vary length naturally
- Define technical terms when necessary
- Attribute all claims clearly
- Quantify statements whenever possible
- Eliminate unnecessary adjectives and adverbs

### Banned Filler Phrases (never use)
"In today's fast-paced world", "It is important to note", "It goes without saying", "Needless to say", "Delve into", "Leverage", "Unlock", "Transformative", "Game-changing", "Revolutionary", "Robust", "Seamless", "Cutting-edge"

### Banned AI Clichés (never use)
"Navigating", "Landscape", "Tapestry", "Crucial", "Deep dive", "Underscores", "In conclusion", "Ultimately"

### Absolute Prohibitions
- No em dashes in the article body (em dashes allowed in titles only)
- No emojis
- No exclamation points
- No promotional tone

### Voice Patterns
- Open with a paradox: state the surprising fact, then cut it with a short sentence ("It isn't." / "They don't.")
- Every claim gets a specific number
- End paragraphs with a sharp, short kicker sentence
- State conclusions, not possibilities. No hedging.
- Closing section: two short sentences. The second lands harder than the first.

### Article Structure
Issues #01–#05 used a fixed heading template (Who Gets Forced / The Failure Path / What I'm Watching / How This Thesis Fails / Closing Thoughts). From Issue #06 onward, do NOT use those fixed headings. Use descriptive h2 headings that fit the specific narrative of each article. The Plain English section remains required on every article.

Suggested flow (adapt freely):
1. Open with the specific event or number — what just happened
2. Explain the mechanism that caused it
3. Show who else is affected and how it spreads
4. Quantify the volume/earnings impact
5. State what breaks the thesis
6. Plain English

### Plain English Section
Write this for every article. This is for a normal person, not a market participant. One paragraph, 4-6 sentences.

Formula:
- Opens with "Even though..." — state what looks fine on the surface
- "I argue this because" — explain the hidden mechanism in everyday language
- "Although these have..." — acknowledge the current apparent stability
- Close with real-world consequence for an everyday person

Rules:
- No financial jargon
- Soft qualifiers: "may", "for now", "aren't permanent"
- Speak directly to the reader ("you may start seeing...")
- Casual and conversational, first person

Example (Issue #01):
"Even though one of the world's most important oil shipping routes have been disrupted for over four months at this point, the price at the gas pump hasn't risen nearly as high as experts initially expected. I argue this because governments have been using emergency reserves, China has been buying less oil due to slower economic activity, and producers have found temporary ways to reroute shipments. Although these have kept prices stable for now, they aren't permanent solutions. Once these emergency supplies start running low and demand picks up again, you may start seeing higher gas prices, even after the current crisis ends."

Example (Issue #02):
"Even though the private lending market, where large investment funds loan money directly to companies outside the traditional banking system, is reporting stable values, the loans underneath are quietly getting worse. I argue this because lenders are allowed to value these loans using their own internal models rather than real market prices, and a growing number of borrowers are paying their interest with more debt instead of cash, which keeps the loans looking current on paper even when the borrower is struggling. Although this has made the numbers look healthy for now, it is not a permanent situation. When lenders are eventually forced to reflect the real value of these loans, the losses will hit publicly traded credit funds, the banks that back them, and everyday investors who put money into private credit and are already finding it difficult to get their money back."

### Title and Deck Formula
- Title: declarative, provocative, specific. Em dash allowed here only. Example: "The SPR Trick Is Almost Over — And Nobody Is Talking About It"
- Deck: one sentence stating the tension between what is happening and why it is a problem.

---

## Approval Flow
1. Routine writes and pushes article to `draft/issue-XX` branch
2. Telegram message arrives at @weeklybullrun_bot with full article text and PR link
3. Alessio reads on any device, goes to the PR link on GitHub, clicks "Merge pull request"
4. GitHub Pages deploys automatically within minutes
5. No Claude Code required for approval
