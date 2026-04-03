# Changelog

All notable changes to Dylan Duan's art portfolio are documented here.

---

## [2026-04-03] — Prompt 3

### Changed
- Moved `Art.html` and `CHANGELOG.md` from `Portfolio/` to `Art Folder/` — art portfolio is now its own standalone project separate from the dev portfolio
- Updated all image paths in `Art.html` to point to `Art/` subfolder using the correct filenames already present (`life-after-effects.jpg`, `street-corner.JPG`, `recurrence.JPG`, `2024.png`, `2025.png`, `jan2026award.JPG`)

---

## [2026-04-03] — Prompt 2

### Changed
- `Art.html` — Rebuilt as a fully standalone one-pager (no nav links, no contact section)
- Redesigned layout: full dark-background site with three distinct section styles per artwork
  - **Work 1 — Life After-Effects:** crosshatch grid texture, Playfair Display serif, offset shadow frame
  - **Work 2 — Street Corner:** warm amber glow, Bebas Neue bold type, orange border with pop-art offset shadow
  - **Work 3 — Recurrence:** deep navy starfield, animated star-pulse, gold-foil gradient text for the Louvre medal
- Added hero section with large italic name, artist statement, and award pills
- Added scroll hint animation in hero
- Removed dependency on other portfolio pages — `Art.html` works entirely on its own
- Alternating image-left / image-right layout for visual rhythm

### Removed
- Nav bar linking to `index.html`, `AboutMe.html`, `Projects.html`, `Contacts.html`
- Dark mode toggle button (no longer needed for standalone art page)

---

## [2026-04-03] — Prompt 1

### Added
- `Art.html` — Initial art portfolio page with three panel styles (ink etching, pop-art, cosmic/night sky)
- `art/` folder with certificate images:
  - `art/life-after-effects-cert.jpg` — 22nd CICAF 2024 Silver Award certificate
  - `art/street-corner-cert.jpg` — 23rd CICAF 2025 Silver Award certificate
  - `art/recurrence-cert.jpg` — Carrousel du Louvre 2026 Gold Medal certificate
- `CHANGELOG.md` — This file
- `IMPLEMENTATION.md` (in Art Folder) — Full spec doc describing artwork details, award info, visual styles, asset checklist, and build steps for the art portfolio
