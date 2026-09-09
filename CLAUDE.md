# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

**One tracked file: `index.html`.** A self-contained personal portfolio site — inline `<style>`, no
framework, no JS, no build step, no CI, no linter, no README, no dependencies to install. Editing the
site means editing that one file.

**It is live and public.** Verified 2026-09-09 via `gh api repos/alentrgovcevic/alentrgovcevic.github.io/pages`:
GitHub Pages builds from **branch `main`, path `/`**, served at **https://alentrgovcevic.github.io/**,
HTTPS enforced, no CNAME, classic build (no Actions workflow).

```bash
open index.html                                    # the only way to preview — there is no server
gh api repos/alentrgovcevic/alentrgovcevic.github.io/pages   # confirm the deploy config
```

Local preview via `file://` is faithful here because everything is inline; the one exception is the
Google Fonts stylesheet, which needs network either way.

## 🛑 A push to `main` is a deployment

There is no staging branch, no preview build and no review gate between a commit and the public web.
The standing fleet rule already applies — **stage, never commit, never push; the owner does that** — but
here it is load-bearing rather than a workflow preference. Never create or alter an outward-facing
artifact without explicit confirmation.

## Every claim on this page is a factual claim about a real person

This is a CV in HTML. Treat the copy the way the fleet rules treat any number: **never write a figure,
count, date, credential, store link or DOI from memory.**

Ground truth, in order:

1. **`~/Projects/alen_private/Alen_Trgovcevic_BragSheet_2026.md`** — the single source of truth for any
   portfolio claim. It wins every disagreement.
2. `~/Projects/brainstorm/CAPABILITIES.md` — a derived summary; useful, but it says itself that the brag
   sheet wins on conflict.

The page currently asserts: **4 apps in production**, **2,000+ users on TankBilligt**, **3 payment rails
live**, **2 peer-reviewed publications**, plus per-app platform status, four App Store / Google Play
links, two DOIs, an ORCID, and **CVR 46159640**. Re-derive any one of them against the brag sheet before
changing it, and run `fact-verifier` (draft + sources only, never the conversation) on any rewrite that
touches numbers, dates, credentials or links.

⚠️ **A live disagreement to resolve rather than paper over:** `CAPABILITIES.md` lists Lynkort as
"iOS + Android"; this page says "Live on iOS; the Android build is unreleased." Check the brag sheet and
the actual store listing before either is edited to match the other.

Known correction already applied elsewhere and easy to reintroduce: **KøreKlar was never built** and
**labRAG is not an App Store product** (it is an offline RAG tool). Neither belongs in a shipped-apps count.

## Outward-facing work: read the brand files first

Per the global rules, before any copy, design or layout change here, read
`~/Projects/marketing-agent/BRAND.md` and — if the change concerns a specific app —
`marketing-agent/brand/tankbilligt.md` or `brand/blivklar.md`, which carry the hard rules (no fabricated
prices or exam dates; no political commentary on Bliv Klar). `BRAND.md` is symlinked into
`atproductions/` and `atproductions-web/`; **edit the original in `marketing-agent/`**.

The contact address on this page is the **personal** one (`alen.trgovcevic@gmail.com`), never
`@au.mbg.dk`. That is deliberate and matches the rule applied to the outbound emails in
`brainstorm/email_drafts/`: this is a personal/commercial identity, and the university address would
imply institutional backing for work unrelated to the employer. Keep it that way.

## The file as it stands

- `lang="en"`, charset, viewport and a `<meta name="description">` are all present.
- **Dark-only palette.** There is no `prefers-color-scheme` block, no `@media print` block and no
  favicon. That is the current state, not an oversight to fix silently — the fleet's "complete standalone
  HTML" checklist is written for *local reports*, and changing the look of a live site is the owner's call.
- **One external reference: Google Fonts** (`preconnect` + the Inter stylesheet). Everything else — CSS,
  layout, colours — is inline. Do not add a CDN, a font file or an analytics snippet.
- Sections are anchor-linked from the nav (`#apps`, `#ai`, `#science`, `#about`); `nav` is hidden below
  560px. Cards follow one shape: `.top` (title + `.badge`), `<p>`, `.tags`, `.links`. Badge classes are
  `live` / `shipped` / `prep` / bare. Match the existing pattern rather than inventing a variant.
- Most project cards link to a **`-overview` repo** (`PhenoVision-overview`, `labRAG-overview`, …) rather
  than the working repo. That split is intentional — check which one a new link should point at.

One thing worth knowing before repositioning anything as commercial: the site describes **PhenoVision as
YOLOv8/11**, and Ultralytics YOLO is **AGPL-3.0** (network copyleft) — recorded across the fleet docs,
e.g. `parcel-pipeline/README.md`. Fine as described research work; a licensing question the moment the
page frames it as a product.
