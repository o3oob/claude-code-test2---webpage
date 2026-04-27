# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-file static promotional webpage for the Korean translation of Andy Weir's novel "프로젝트 헤일메리" (Project Hail Mary). It is deployed via GitHub Pages automatically on push to `main`.

## Architecture

The entire application lives in `index.html` (≈930 lines). There is no build system, no package manager, and no external local dependencies — everything runs from CDN or inline code.

**External dependencies (CDN only):**
- Tailwind CSS (`https://cdn.tailwindcss.com`)
- Google Fonts: Noto Sans KR

**Inline JavaScript features:**
- Canvas-based starfield with twinkling and shooting stars
- IntersectionObserver scroll-reveal (triggers `.in` class at 12% visibility)
- Custom easing smooth-scroll (`easeInOutCubic`, 2s duration)
- Navbar opacity transition (threshold: 60px scroll)
- Hero parallax (25% speed + opacity fade)
- Reading progress bar
- Word-by-word title reveal (wraps words in `<span>` with staggered delays)

**CSS design system (CSS variables in `<style>`):**
- `--blue: #0A84FF`, `--green: #30D158`, `--gold: #FFD60A`
- Glassmorphism cards, gradient text, scroll-reveal, timeline, ambient orbs

## Development Workflow

**Viewing the site locally:** Open `index.html` directly in a browser — no server required.

**Deployment:** Pushing to `main` automatically triggers `.github/workflows/static.yml`, which deploys the whole repository to GitHub Pages with no build step.

**No linting, no tests, no build commands exist.** Validate changes by opening the file in a browser.

## Conventions

- All content is in Korean (`<html lang="ko">`).
- Scroll-reveal elements use the `.reveal` class; the IntersectionObserver adds `.in` to trigger CSS transitions.
- Section IDs follow kebab-case (e.g., `#story`, `#characters`, `#author`).
- The starfield canvas is sized and redrawn on `resize` events.
- The reading progress bar element has `id="progress-bar"`.
