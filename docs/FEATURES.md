# Lumina — Features

A complete reference of everything Lumina offers.

---

## Themes & Styling

Lumina ships with **10 hand-crafted themes**, each with **5 color palettes** — 50+ visual combinations out of the box.

### Themes

| Theme | Vibe |
|---|---|
| **Classic** | Serif fonts, cream backgrounds, academic elegance |
| **Modern** | Glassmorphic cards, gradient accents, Inter font |
| **Minimal** | Clean, airy, distraction-free |
| **Elegant** | Refined borders, accent typography |
| **Bold** | High contrast, impactful headings |
| **Geek** | Terminal aesthetic, neon accents |
| **Newspaper** | Editorial layout, typographic focus |
| **Aurora** | Rich gradients, colorful vibrancy |
| **Ocean** | Cool water-inspired tones |
| **Retro** | Vintage warmth, nostalgic feel |

### Palettes (per theme)

Each theme defines 5 palettes. For example, **Classic** offers: Default, Navy, Forest, Plum, Slate. **Modern** offers: Default, Indigo, Teal, Rose, Amber. And so on for every theme.

### Dark Mode

Every theme + palette combination has a fully designed dark variant. Lumina auto-detects the system preference and persists the user's choice in `localStorage`. Toggle via the sun/moon icon in the navbar.

### Cursor Spotlight

Optional spotlight effect that follows the cursor. Enable with `cursor_spotlight: true` in config.

---

## Pages (18 Types)

Toggle any page on or off in `site.config.yml` under `pages:`. Only enabled pages appear in the navbar.

| Page | Description |
|---|---|
| **About** | Hero profile with avatar, bio (Markdown), and social links. This is your homepage. |
| **Publications** | Auto-parsed from BibTeX. Grouped by year, filterable, with venue badges and action links (PDF, Code, Video, Slides, DOI). |
| **CV** | Rendered from `cv/cv.yml`. Sections: education, experience, skills, awards, service. Optional PDF download. |
| **Blog** | MDX-powered posts with reading time, table of contents, tags, and draft support. |
| **Projects** | Markdown-based project cards with images and descriptions. |
| **News** | Reverse-chronological news items. Also shown as a widget on the homepage. |
| **Teaching** | Course listings from YAML. |
| **Talks** | Conference talks and presentations. |
| **Awards** | Honors and awards (pulled from CV data). |
| **Team** | Lab members and collaborators with photos and roles. |
| **Positions** | Open positions / job postings. |
| **Collaborators** | Research collaborators grid. |
| **Service** | Professional service and reviewing. |
| **Repositories** | GitHub repository showcase. |
| **Gallery** | Photo gallery with lightbox modal. |
| **Books** | Reading list / book reviews. |
| **Media** | Press and media appearances. |
| **Travel** | Travel log and conference locations. |

---

## Publications System

Lumina parses standard BibTeX (`.bib`) files natively — no external tools required.

### Supported BibTeX Fields

| Field | Purpose |
|---|---|
| `title` | Paper title |
| `author` | Author list (your name is auto-bolded) |
| `year` | Publication year |
| `booktitle` / `journal` | Venue name |
| `doi` | DOI link |
| `url` / `pdf` | Paper URL |
| `code` | Source code link |
| `video` | Video link |
| `slides` | Presentation slides link |
| `abstract` | Paper abstract |
| `selected` | Set to `true` to feature on homepage |
| `preview` | Thumbnail image path |
| `venue_type` | Override auto-detected type: `conference`, `journal`, `workshop`, `preprint`, `thesis` |

### Auto Features

- **Venue type detection** — Automatically classifies venues (conference, journal, workshop, etc.) and shows color-coded badges.
- **Author highlighting** — Your name (set in config) is bolded in every author list.
- **Year grouping** — Publications grouped by year with counts.
- **Selected papers** — Papers with `selected: true` appear in a homepage widget (up to 5).

---

## Blog

Write posts in Markdown or MDX at `src/content/blog/`.

### Frontmatter

```yaml
---
title: "Your Post Title"
date: 2025-01-15
description: "A short summary."
tags: ["robotics", "research"]
draft: false
---
```

### MDX Components

Use these inside `.mdx` posts:

- `<Math>` — LaTeX formula rendering (inline and display)
- `<Video>` — YouTube/Vimeo embed (just paste the URL)
- `<Gallery>` — Responsive image grid
- `<Chart>` — Chart placeholder

### Features

- Auto-generated reading time
- Sticky table of contents with scroll spy
- Tag filtering
- RSS feed at `/rss.xml`
- Draft mode (set `draft: true` to hide from production)

---

## Components

### Navigation

- **Sticky navbar** with glassmorphic blur
- Dynamic overflow handling — extra pages collapse into a "More" dropdown
- Mobile hamburger menu
- Active page indicator

### Search

Press **Cmd+K** (or Ctrl+K) to open the search palette. Instantly navigate to any page.

### Theme Picker

Click the palette icon to open the theme picker. Browse all 10 themes and their palettes in real-time. Changes apply instantly and persist across sessions.

### UI Primitives

- **Card** — Flexible card with optional image, tags, hover effects
- **Badge** — 4 variants: default, accent, success, warning
- **Timeline** — Vertical timeline with dots and connecting line (used in CV)
- **BentoGrid** — Responsive masonry-like grid
- **FilterChips** — Clickable filter buttons

---

## Performance & SEO

- **Static site generation** — Pure HTML, zero client-side framework overhead
- **View transitions** — Smooth page navigation without full reloads
- **Lazy image loading** — Images load on scroll
- **Image optimization** — Sharp-powered at build time
- **Sitemap** — Auto-generated at `/sitemap-index.xml`
- **RSS** — Auto-generated at `/rss.xml`
- **Structured data** — JSON-LD Person schema for search engines
- **Meta tags** — OpenGraph and Twitter card support

---

## Accessibility

- Semantic HTML5 structure
- ARIA labels and roles
- Focus-visible outlines
- Skip-to-content link
- `prefers-reduced-motion` support
- Full keyboard navigation
- Alt text for images

---

## Tech Stack

| Layer | Technology |
|---|---|
| Framework | [Astro 5](https://astro.build) |
| Language | TypeScript |
| Styling | [Tailwind CSS 4](https://tailwindcss.com) |
| Content | MDX, Markdown, BibTeX, YAML |
| Icons | [Lucide](https://lucide.dev) |
| Images | Sharp |
| Deploy | GitHub Pages (Actions) |
