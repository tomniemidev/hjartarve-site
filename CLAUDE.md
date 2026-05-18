# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A single-file static promotional site for **Hjartarvé**, a Nordic folk metal band. The entire site — HTML, inline CSS, inline SVG — lives in `index.html`. There is no build step, no package manager, no test suite, no git repository in this directory.

Deployment target: **Azure Static Web Apps**, served as-is.

## Working with the site

- Edit `index.html` directly. No bundler, no transpiler — what you write is what ships.
- Preview by opening `index.html` in a browser, or serve the directory with any static server (`python -m http.server`, `npx serve`, etc.).
- Fonts come from Google Fonts via `<link>` in the `<head>`. For air-gapped deployment, swap that link for a local `@font-face` block (noted in the file's own header comment).

## Launch checklist — `TODO:` markers in the file

The `<head>` comment block lists the placeholders that must be replaced before launch. Search for these literal strings:

- `TODO: social links` — footer Bandcamp/Instagram hrefs.

When making changes, keep the in-file `<head>` comment block in sync with what's still outstanding.

## Page architecture

`index.html` is structured as one top-level `<header>` (sticky topbar nav), one `<main>` containing four `<section>`s, and one `<footer>`. The sections, in order, are: **hero** → **about** → **album** → **reviews**. The topbar nav anchors (`#about`, `#album`, `#album-player`, `#reviews`) must stay in sync with the section IDs — note that `#album-player` is an in-section anchor that targets the player block inside the album section, not a separate section.

## Design system

All visual tokens are CSS custom properties defined under `:root` near the top of the `<style>` block — colors (`--ink`, `--bark`, `--moss`, `--bone`, `--ember`, …), font stacks (`--f-display`, `--f-head`, `--f-body`), and layout rhythm (`--maxw`, `--pad-y`, `--gut`, `--border-faint`, `--border-ember`). Prefer reusing these tokens over introducing new literal colors or sizes — the aesthetic (aged bone on dark bark, ember accents, fraktur display type) depends on them being applied consistently.

The decorative `.fog` layers and inline SVG sigils/runes are intentional atmosphere — when restructuring sections, keep them rather than stripping them as "unused" markup.
