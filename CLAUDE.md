# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

`steadbook-web` is the **public marketing / landing site** for Steadbook — a native
iOS/iPadOS farm-management app (the app itself lives in the sibling repo `../steadbook`).
This is a standalone web project: it is **not** a web port of the app and shares no code or
data store with it. The app has no backend (SwiftData + CloudKit); this site is content-only.

The landing page was imported from the Claude Design project "Steadbook" (file
`Steadbook Landing.html`) via the `claude_design` / DesignSync MCP, then made self-contained
for static hosting.

## Stack

Deliberately minimal — a single static HTML page, no build step:

- `index.html` — the entire page (markup + inlined CSS + a small vanilla-JS `<script>`).
- `screenshots/*.png` — 10 app screenshots (5 screens × dark/light), imported from the design
  project. Referenced as `screenshots/<screen>-<theme>.png`; swapped at runtime by the theme JS.
- Fonts (Bricolage Grotesque, JetBrains Mono) load from the Google Fonts CDN.
- No framework, no bundler, no package.json.

Hosted on **GitHub Pages** (serves `index.html` from the repo root; `.nojekyll` disables
Jekyll processing).

## Working on it

- To preview locally, open `index.html` in a browser, or run `python3 -m http.server` and
  visit the printed URL (a server is needed for the screenshot `fetch`/relative paths to work
  cleanly).
- **Design tokens are inlined** in the `:root` / `html[data-theme="light"]` blocks at the top
  of the `<style>` in `index.html`. They mirror the Steadbook "Greenhouse" design system from
  `../steadbook` — keep them in sync with that system rather than inventing new colors/fonts.
- The email "Notify me" form is a **front-end mock** (no backend) — it just shows a success
  state. Wire it to a real capture endpoint before relying on it.
- Light/dark theme is persisted to `localStorage` under the `sb-theme` key.

## Re-syncing from the design

The source of truth for the design is the Claude Design project (id
`164dd0a8-d622-46c1-bba9-f5ffeea68e09`, file `Steadbook Landing.html`). If that file changes,
re-import via the DesignSync MCP and re-apply the self-contained tweaks (inline the tokens,
keep the relative `screenshots/` paths).

## Conventions

- This repo is independent of `../steadbook`'s delivery workflow (GitHub Issues pipeline,
  session locks, lanes). Do **not** import those processes here unless asked.
- Marketing copy is public — confirm wording/claims and availability dates with the owner
  before publishing; don't invent product features.
