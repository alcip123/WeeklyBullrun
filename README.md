# The Weekly Bullrun

## Project Overview
A weekly financial markets newsletter website built in plain HTML/CSS. No frameworks, no build tools — just files.

## File Structure
- `index.html` — Homepage (latest issue + archive list)
- `archive.html` — Full archive of all issues
- `about.html` — About page (needs content)
- `issue-01.html` — Issue #1 article page
- `issue-02.html` — Add when ready (copy issue-01.html as template)

## How to Add a New Issue Each Week
1. Duplicate `issue-01.html`, rename it `issue-02.html`
2. Update the title, deck, date, and body content
3. In `index.html`: update the hero section with the new article, add a new row to the archive list
4. In `archive.html`: add a new row to the archive list

## Design
- WSJ-inspired: clean white, Georgia serif, tight typography
- No frameworks or dependencies
- Live date in header via JavaScript

## Hosting
- Domain: weeklybullrun.com
- DNS: Cloudflare (nameservers pointed from IONOS)
- Upload all files to your web host root directory

## Style Guide for New Issues
Voice: Direct, confident, no hedging. Build the argument step by step.
Structure:
  1. The Setup
  2. The Hidden Mechanism
  3. Who Gets Forced
  4. The Failure Path
  5. What I'm Watching
  6. How This Thesis Fails
  7. Closing Thoughts
  8. Plain English summary
