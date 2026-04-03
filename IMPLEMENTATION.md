# Art Portfolio — Implementation Doc

**Project:** Add a full Art Portfolio page to Dylan Duan's existing portfolio website  
**Deploy target:** GitHub Pages (same repo as `dylanduan/Portfolio`, deployed via `.github/workflows/static.yml`)  
**New file:** `Portfolio/Art.html`  
**Supporting assets:** `Portfolio/art/` folder (see asset checklist below)

---

## Overview

Dylan is a student artist with multiple international awards. This page showcases his artworks and certificates in a gallery format where **each artwork gets its own visual style** that echoes the mood and medium of the piece.

### Awards Summary

| Year | Competition | Award | Artwork |
|------|-------------|-------|---------|
| Aug 2024 | 22nd Canada International Children's Art Festival (City of Toronto) | **Silver Award** | *Life After-Effects* |
| Aug 2025 | 23rd Canada International Children's Art Festival (City of Toronto) | **Silver Award** | *Street Corner* |
| Jan 2026 | 4th International Art Games — Carrousel du Louvre, France (WFUCA / ADEFC) | **Gold Medal (Médaille d'Or)** | *Recurrence Between Two Best Friends* |

---

## Asset Checklist

Before building, copy/rename these files into `Portfolio/art/`:

```
Portfolio/art/
├── life-after-effects.jpg        ← the detailed black & white ink drawing
├── life-after-effects-cert.jpg   ← Awards(Art)/2024.jpg  (certificate scan)
├── street-corner.jpg             ← the colorful gouache/acrylic city scene painting
├── street-corner-cert.jpg        ← Awards(Art)/2025.JPG  (certificate scan)
├── recurrence.jpg                ← the white-on-black wolf & constellation piece
├── recurrence-cert.jpg           ← Awards(Art)/jan2026award.JPG  (Louvre cert)
```

> Note: `2024.png`, `2025.png`, `jan2026.JPG` are duplicates — use whichever resolution is best.

---

## Page Structure

```
Art.html
 ├── <head> — shared CSS variables + page-specific styles
 ├── <header> — "Dylan Duan — Art Portfolio"
 ├── <nav> — same sticky nav bar as index.html (Home / About Me / Projects / Art / Contact)
 ├── #intro — short artist statement
 ├── #gallery
 │    ├── .artwork-panel  [Life After-Effects]     ← ink/etching style
 │    ├── .artwork-panel  [Street Corner]          ← bold pop-art style
 │    └── .artwork-panel  [Recurrence Between…]   ← cosmic/dark style
 └── <footer> — same as index.html
```

---

## Visual Style Per Artwork

### 1. *Life After-Effects* — Ink Etching Style
- **Background:** off-white parchment `#f5f0e8`
- **Border:** `4px solid #1a1a1a` with rough crosshatch `box-shadow: 4px 4px 0 #1a1a1a`
- **Typography:** serif font (Georgia or `Playfair Display` from Google Fonts), ink-black `#1a1a1a`
- **Award badge:** small hand-drawn-style ribbon SVG, silver `#aaa9a3`
- **Hover effect:** image desaturates → re-saturates on hover (CSS `filter: saturate(0)` → `saturate(1)`)
- **Description text:** italic, slightly faded `#444`
- **Mood:** old-world engraving, dense detail, serious

```css
/* Ink panel */
.panel-ink {
  background: #f5f0e8;
  border: 4px solid #1a1a1a;
  box-shadow: 6px 6px 0 #1a1a1a;
  font-family: 'Playfair Display', Georgia, serif;
  color: #1a1a1a;
}
.panel-ink img {
  filter: saturate(0) contrast(1.1);
  transition: filter 0.5s ease;
}
.panel-ink:hover img {
  filter: saturate(1) contrast(1);
}
```

---

### 2. *Street Corner* — Bold Retro Pop-Art Style
- **Background:** warm cream `#fffbe6` with subtle diagonal stripe texture via `repeating-linear-gradient`
- **Border:** `5px solid #e65c00` (orange accent matching painting's warm tones)
- **Typography:** `Bebas Neue` or `Impact` — large, bold, uppercase labels
- **Award badge:** bright gold star burst `★ SILVER AWARD` in orange/yellow
- **Hover effect:** panel lifts with `transform: translateY(-6px)` and stronger shadow
- **Color accents:** cobalt blue `#1a3a6b` and burnt orange `#e65c00` (pulled from the painting)
- **Mood:** energetic, urban, graphic-novel feel

```css
/* Pop-art panel */
.panel-pop {
  background: #fffbe6;
  background-image: repeating-linear-gradient(
    45deg,
    transparent,
    transparent 10px,
    rgba(230, 92, 0, 0.04) 10px,
    rgba(230, 92, 0, 0.04) 11px
  );
  border: 5px solid #e65c00;
  box-shadow: 8px 8px 0 #1a3a6b;
  font-family: 'Bebas Neue', Impact, sans-serif;
  letter-spacing: 0.05em;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}
.panel-pop:hover {
  transform: translateY(-6px);
  box-shadow: 14px 14px 0 #1a3a6b;
}
```

---

### 3. *Recurrence Between Two Best Friends* — Cosmic / Night Sky Style
- **Background:** deep navy/black gradient `linear-gradient(135deg, #0a0a1a 0%, #0d1b2a 100%)`
- **Border:** `1px solid rgba(255,255,255,0.15)` with `box-shadow: 0 0 30px rgba(100,149,237,0.3)` glow
- **Typography:** `Cormorant Garamond` or serif italic, white/silver `#e8eaf6`
- **Award badge:** gold foil effect using `background: linear-gradient(135deg, #d4af37, #f9e07a, #d4af37)` with metallic sheen — **Médaille d'Or / Gold Medal**
- **Hover effect:** subtle star-twinkle keyframe animation on scattered `::before` pseudo-elements
- **Accent:** constellation dot-line overlay via CSS `radial-gradient` dots
- **Mood:** mystical, celestial, quiet wonder

```css
/* Cosmic panel */
.panel-cosmic {
  background: linear-gradient(135deg, #0a0a1a 0%, #0d1b2a 100%);
  border: 1px solid rgba(255, 255, 255, 0.15);
  box-shadow:
    0 0 30px rgba(100, 149, 237, 0.25),
    inset 0 0 60px rgba(0, 0, 50, 0.5);
  color: #e8eaf6;
  font-family: 'Cormorant Garamond', 'Palatino Linotype', serif;
  font-style: italic;
}
.panel-cosmic img {
  border-radius: 4px;
  box-shadow: 0 0 20px rgba(255, 255, 255, 0.1);
}
.gold-badge {
  background: linear-gradient(135deg, #b8860b, #ffd700, #daa520);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  font-weight: 700;
  font-size: 1.1rem;
}
```

---

## Gallery Layout

Each `.artwork-panel` follows this HTML pattern:

```html
<div class="artwork-panel panel-[ink|pop|cosmic]">
  <div class="artwork-image-wrap">
    <img src="art/[filename].jpg" alt="[title]" loading="lazy" />
  </div>
  <div class="artwork-info">
    <h2 class="artwork-title">[Title]</h2>
    <p class="artwork-medium">[Medium, e.g. "Ink on paper"]</p>
    <p class="artwork-description">[1-2 sentence description]</p>
    <div class="award-block">
      <span class="award-badge">[Award name]</span>
      <span class="award-event">[Competition name]</span>
      <span class="award-date">[Month Year]</span>
    </div>
    <button class="cert-toggle" aria-expanded="false">View Certificate</button>
    <div class="cert-panel" hidden>
      <img src="art/[filename]-cert.jpg" alt="Certificate for [title]" />
    </div>
  </div>
</div>
```

The certificate image is **hidden by default** and toggled with a small JS snippet (no library needed):

```js
document.querySelectorAll('.cert-toggle').forEach(btn => {
  btn.addEventListener('click', () => {
    const cert = btn.nextElementSibling;
    const open = btn.getAttribute('aria-expanded') === 'true';
    btn.setAttribute('aria-expanded', String(!open));
    cert.hidden = open;
    btn.textContent = open ? 'View Certificate' : 'Hide Certificate';
  });
});
```

---

## Nav Update

Add the Art page link to **all existing HTML files** (`index.html`, `AboutMe.html`, `Projects.html`, `Contacts.html`):

```html
<!-- In .nav-links div, add: -->
<a href="Art.html">Art</a>
```

---

## Artist Statement (Intro Section)

Suggested copy for `#intro`:

> I work across ink, gouache, and mixed media — from dense black-and-white narratives to large-scale colour compositions. My work has been recognized at the Canada International Children's Art Festival (City of Toronto) and exhibited internationally at the Carrousel du Louvre, Paris.

---

## Responsive Layout

- Desktop (≥900px): artwork image left (55%), info panel right (45%), side by side
- Tablet (600–899px): stack image on top, info below, maintain full width
- Mobile (<600px): single column, image 100% width, reduce font sizes

```css
.artwork-panel {
  display: grid;
  grid-template-columns: 55fr 45fr;
  gap: 2rem;
  padding: 2.5rem;
  margin: 3rem auto;
  max-width: 1100px;
  border-radius: 12px;
}

@media (max-width: 900px) {
  .artwork-panel {
    grid-template-columns: 1fr;
  }
}
```

---

## Google Fonts to Import

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital@0;1&family=Bebas+Neue&family=Cormorant+Garamond:ital,wght@1,400;1,700&display=swap" rel="stylesheet">
```

---

## Implementation Steps (in order)

1. **Copy artwork images** into `Portfolio/art/` (see asset checklist above)
2. **Create `Portfolio/Art.html`** using the structure and styles described above
3. **Add `<a href="Art.html">Art</a>`** to the nav in all 4 existing HTML files
4. **Commit and push to `main`** — GitHub Actions will auto-deploy to Pages

---

## Notes

- All existing pages use inline `<style>` — keep the same pattern for `Art.html` (no separate CSS file needed unless you want to refactor later)
- Dark mode toggle exists on `index.html` — optionally propagate it to `Art.html` using `localStorage` to persist the preference across pages
- Image filenames must not contain spaces or special characters (rename before copying)
- The Louvre certificate is in French — include a small English subtitle below: *"Certificate of Honour — Gold Medal"*
