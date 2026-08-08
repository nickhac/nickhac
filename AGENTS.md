# AGENTS.md — nickhac GitHub profile

Instructions for AI agents maintaining Nick Holmes à Court's GitHub profile repo (`nickhac/nickhac`) and its source files in this folder.

## What this repo is

The public GitHub profile for Nick Holmes à Court. Audience: hiring executives, VCs, enterprise buyers and engineers evaluating Nick's technical depth. Every change must increase signal of: technical currency, data-led thinking, commercial depth, shipped product.

## File map

| Source (this folder) | Destination (repo) | Purpose |
|---|---|---|
| `readme.md` | `README.md` | Profile page rendered on github.com/nickhac |
| `experience.md` | `EXPERIENCE.md` | Full experience profile, linked from README |
| `hero.svg` | `assets/hero.svg` | Neo-brutalist hero banner (the only place heavy styling lives) |
| `agents.md` | `AGENTS.md` | This file: operating instructions for agents maintaining the repo |

This folder is the source of truth. Edit here first, then copy to a clone of `https://github.com/nickhac/nickhac.git`, commit and push. Auth: HTTPS credentials are in the macOS keychain; `gh` CLI is not installed; SSH keys are not set up.

## Hard constraints — GitHub rendering

1. GitHub strips `<style>` tags, all `style=` attributes and most HTML from README markdown. Never add them to `readme.md` or `experience.md`.
2. Whitelisted and used deliberately: `<table>`, `<tr>`, `<td>` (with `width`, `valign`, `nowrap`), `<kbd>`, `<blockquote>`, `<sub>`, `<sup>`, `<b>`, `<i>`, `<br>`, `<img>` (with `width`, `height`, `alt`), `<a>`, `align` attribute, `<details>`.
3. Anything needing real styling goes in `hero.svg` or a new SVG in `assets/`. SVGs must be valid XML: encode non-ASCII characters as numeric entities (`&#192;` for À, `&#215;` for ×). A corrupted multibyte character makes GitHub render a broken image.
4. After changing any SVG, bump the cache-bust query in the README reference (`assets/hero.svg?v=N`). GitHub's CDN caches for 5 minutes and the image proxy caches failures.
5. Markdown tables force a header row. When no header makes sense, use an HTML `<table>` with no `<th>`.

## Design system

- Palette (SVG only): paper `#f5f1ea`, ink `#0a0a0a`, orange `#ff6600`, dark orange `#e05500`.
- Neo-brutalist rules: thick borders, hard offset shadows, halftone dither patterns, monospace stat labels. No gradients except dither fade masks. No rounded corners.
- Section headers rotate glyphs in order: ▲ ■ ● ◆ (◈ for Research & Writing).
- `<kbd>` tags are the badge element: category labels on cards, row labels in tables, dataset sizes in the research section, button-style links (`FULL CTO EXPERIENCE PROFILE →`).
- Outcome lines inside cards use `<blockquote>` with a bold label (`**BUILT**`, `**RESULT**`) so they render with a left border bar.
- Card cells get `<br>` padding at top and bottom. Descriptions wrap naturally; never insert hard `<br>` mid-sentence.

## Voice — non-negotiable

Prose follows Nick's voice (see `~/.cursor/skills/talk-like-nick/` for the full rules). The rules that matter most here:

1. Zero em dashes anywhere. Use colons, commas or periods. This is an automatic fail.
2. First person in `experience.md` ("I have operated", not "Operated at every layer").
3. No corporate fog words: leverage, robust, seamless, cutting-edge, groundbreaking, empower, showcase, delve, harness, pivotal, landscape, testament.
4. Numbers and concrete scenes over abstract claims. Lead with the dataset or the outcome.
5. No self-congratulation without a mechanism ("The skill people hire me for: X" beats "Known for X").

## Facts registry — do not invent, do not drift

Canonical claims. If a claim is not here or in the source files, ask Nick before adding it.

- 20+ years building production software; 200+ production systems personally shipped and managed
- 3× VC-backed founder, 2 exits
- Former Venture Capital Manager at AWS; ex-MSFT; ex-Betfair
- Bachelor of Computer Science
- Winner, SF Hermes Hackathon Jul 2026 (Acquireable.club, most revenue in cohort)
- Current projects: Nondual.cloud (agent relationship infra), GTM-OS.xyz (autonomous GTM), Acquireable.club, AltitudeOS (altitudegroup.org)
- Research pieces and datasets: Venture Efficiency Report 2025 (1,691 companies), 28 Quiet Winners (LinkedIn: 793 reactions / 984 comments), Leaving Australia model (600M ATO rows, ExitProof.com.au, first 100 respondents avg $4.8M better off over 10 years), Australian AI GitHub scanner piece, ANZ Startup Acquisitions (20 years of M&A)
- Links: linkedin.com/in/nholmesacourt · nickhac.substack.com · nick@altitudegroup.org
- Location: Sydney / San Francisco · Altitude Group

## Workflow for any change

1. Edit the source file in this folder.
2. Clone or reuse `/tmp/nickhac-profile` (re-clone if missing: `git clone https://github.com/nickhac/nickhac.git`).
3. Copy source → repo path per the file map. Set repo-local identity if fresh clone: `nickhac` / `nickhac@users.noreply.github.com`.
4. Commit with a short imperative message. Push to `main`.
5. Verify live: load github.com/nickhac in a browser, confirm images render (check `naturalWidth > 0`, not just HTTP 200) and layout holds at profile-column width (~700px).
6. If an SVG changed and shows broken, wait out the 5-minute CDN cache, then bump the cache-bust version.

## Do not

- Do not commit secrets, keys or personal data beyond the contact details above.
- Do not add repos, stars or activity claims that don't exist.
- Do not restructure the README section order without being asked: hero → badges → Now Shipping → Operating Range → Build Stack → Research & Writing → Operating Principles → experience link → contact.
- Do not force-push. History on this repo is linear.
