# Academic Portfolio Website Template: Product Specification

## Executive Summary

This document defines the product strategy for a next-generation academic portfolio website template. The template targets a wide spectrum of academics -- from PhD students who want a two-page site in five minutes, to lab directors managing team profiles and news feeds. The core philosophy is **progressive disclosure**: start simple, grow without friction.

---

## 1. User Personas

### Persona A: "The Minimalist" -- Early-Career Researcher

**Who:** PhD student, postdoc, or junior faculty who needs an online presence but does not want to maintain a complex site.

**Goals:** Appear professional in search results. Link from papers to a real homepage. Share contact info and a publication list.

**Needs:**
- About/Bio page (homepage)
- Publications page (auto-generated from BibTeX)
- Contact info / social links
- CV (PDF download link)

**Anti-needs:** Does NOT want a blog, photo gallery, or anything requiring regular updates.

**Setup tolerance:** 5 minutes. Edit one config file, drop in a BibTeX file, deploy.

---

### Persona B: "The Standard Academic" -- Mid-Career Researcher

**Who:** Assistant/associate professor or senior researcher who wants a complete professional presence.

**Goals:** Showcase a research portfolio. Attract students and collaborators. Document teaching record. Present a polished CV.

**Needs:**
- Everything in Persona A
- Research Projects page (with images, descriptions, links to papers/code)
- Teaching page (courses, materials, student resources)
- CV page (rendered from structured data, with PDF download)
- News/Updates feed (paper acceptances, awards, talks)
- Talks/Presentations page

**Anti-needs:** Probably does not want a personal blog or hobbies section. Wants low maintenance.

**Setup tolerance:** 30 minutes. Willing to edit a few YAML files and write Markdown for project descriptions.

---

### Persona C: "The Power User" -- Academic with a Personal Brand

**Who:** Senior researcher, public intellectual, or academic with a media presence who treats their website as a personal platform.

**Goals:** Build an audience. Share ideas beyond papers. Express personality. Attract speaking invitations and media inquiries.

**Needs:**
- Everything in Persona B
- Blog (with tags, categories, RSS, comments)
- Photo Gallery (fieldwork, conferences, lab life)
- Bookshelf / Reading List
- Media/Press page (interviews, podcast appearances, quotes)
- Newsletter signup *(Planned)*
- Talks page with slides/video embeds
- Personal section (hobbies, travel, about-beyond-work)

**Setup tolerance:** Hours. Comfortable with Markdown, may customize CSS/layouts.

---

### Persona D: "The Lab Director" -- Group/Lab Leader

**Who:** PI, lab director, or research group leader who manages a collective identity.

**Goals:** Recruit students and postdocs. Showcase lab's collective output. Maintain a lab news feed. Present the team.

**Needs:**
- Everything in Persona B
- Team/People page (current members with photos, bios, links)
- Alumni page (former members with current positions)
- Lab News feed (distinct from personal news)
- Open Positions / "Join Us" page
- Group Publications (filterable by member)
- Group Projects page
- Collaborators / Partners section
- Lab Resources page (internal tools, datasets, reading lists)

**Setup tolerance:** Moderate. Will delegate to a lab member. Needs clear documentation.

---

## 2. Complete Page Inventory

### 2.1 CORE Pages (Every site has these)

#### About / Homepage
| Attribute | Value |
|-----------|-------|
| **Contains** | Profile photo, name, title/affiliation, short bio (1-3 paragraphs), social links, selected publications, recent news |
| **Why needed** | The landing page. First impression. What Google indexes. |
| **Priority** | CORE -- always present, serves as index |
| **Data source** | `config/site.yaml` for identity; `content/about.md` for bio prose |
| **al-folio equivalent** | `about.md` with frontmatter profile config |
| **Improvements over al-folio** | Social links should NOT be inline SVG in Markdown (current al-folio hack). Should be declared in config and rendered by the template. Support for "selected papers" and "recent news" as opt-in widgets on the homepage. |

#### Publications
| Attribute | Value |
|-----------|-------|
| **Contains** | Full publication list, grouped by year (default) or type. Each entry: title, authors (with self-highlight), venue, year, links (PDF, code, video, slides, poster, project page), thumbnail, abstract toggle, badges (citations, altmetric) |
| **Why needed** | The single most important page for any academic. Hiring committees, collaborators, students all check this first. |
| **Priority** | CORE |
| **Data source** | `data/publications.bib` (BibTeX file). Extra metadata via BibTeX custom fields (preview, pdf, code, video, selected, award). |
| **Configuration** | In `config/site.yaml`: author name for highlighting, grouping preference (year/type), max authors shown, badge toggles |
| **Improvements over al-folio** | Add filterable tags/topics. Support multiple BibTeX files. Add "copy citation" button. Support DBLP/Semantic Scholar auto-import as optional feature. |

---

### 2.2 RECOMMENDED Pages (Most academics want these)

#### CV / Resume
| Attribute | Value |
|-----------|-------|
| **Contains** | Structured CV rendered as HTML, with optional PDF download button |
| **Why needed** | Replaces emailing PDFs. Always up-to-date. Searchable. |
| **Priority** | RECOMMENDED |
| **Data source** | `data/cv.yaml` (structured) following JSON Resume schema. OR simply link a PDF. |
| **Configuration** | Toggle sections: education, experience, publications, awards, skills, service, etc. |
| **Improvements over al-folio** | Support JSON Resume standard for portability. Allow both "full rendered CV" and "just link a PDF" modes. |

#### Research / Projects
| Attribute | Value |
|-----------|-------|
| **Contains** | Grid or list of research projects. Each project: title, description, image/thumbnail, status (active/completed), related publications, links (demo, code, paper). Individual project pages with full write-up. |
| **Why needed** | Tells a narrative about research that a publication list alone cannot. Groups papers into themes. |
| **Priority** | RECOMMENDED |
| **Data source** | Collection: `content/projects/` directory with one Markdown file per project |
| **Configuration** | Enable/disable categories. Choose layout (grid cards vs. horizontal list). Sort by importance or date. |

#### News / Updates
| Attribute | Value |
|-----------|-------|
| **Contains** | Reverse-chronological feed of short announcements (paper accepted, talk given, award received, student graduated) |
| **Why needed** | Shows the site is active. Provides context on About page as a widget. |
| **Priority** | RECOMMENDED |
| **Data source** | Collection: `content/news/` directory, one Markdown file per item. OR inline in `data/news.yaml` for ultra-simple entries. |
| **Configuration** | Number to show on homepage. Scrollable toggle. Standalone page toggle. |

#### Teaching
| Attribute | Value |
|-----------|-------|
| **Contains** | List of courses taught, organized by semester/year. Each: course name, number, role, institution, description, link to materials. |
| **Why needed** | Required for tenure/promotion. Students search for course info. |
| **Priority** | RECOMMENDED |
| **Data source** | `data/teaching.yaml` for structured list. OR `content/teaching.md` for free-form. OR collection `content/courses/` for detailed per-course pages. |

---

### 2.3 OPTIONAL Pages -- Academic

#### Talks / Presentations
| Attribute | Value |
|-----------|-------|
| **Contains** | List of invited talks, conference presentations, panels. Each: title, event, date, location, slides link, video embed. |
| **Why needed** | Demonstrates impact and visibility. Useful for speaker invitations. |
| **Priority** | OPTIONAL |
| **Data source** | `data/talks.yaml` |
| **Not in al-folio** | Yes -- this is new. al-folio has no dedicated talks page. |

#### Awards / Honors
| Attribute | Value |
|-----------|-------|
| **Contains** | Chronological list of awards, fellowships, grants, honors. |
| **Why needed** | Demonstrates recognition. Important for tenure dossiers and grant applications. |
| **Priority** | OPTIONAL (can also live as a CV section) |
| **Data source** | `data/awards.yaml` OR as a section within `data/cv.yaml` |

#### Team / People (Lab Mode)
| Attribute | Value |
|-----------|-------|
| **Contains** | Grid of team members: photo, name, role, short bio, links. Grouped by category (PI, postdocs, PhD students, undergrads, visiting). Alumni section with current positions. |
| **Why needed** | Lab identity. Recruitment. Showing advisor-student relationships. |
| **Priority** | OPTIONAL (essential for Persona D) |
| **Data source** | `data/team.yaml` with member entries. Each member can optionally link to their own site. |
| **Not in al-folio** | Partially exists as `profiles.md` but is rudimentary. Needs proper team data model. |

#### Open Positions / Join Us
| Attribute | Value |
|-----------|-------|
| **Contains** | Current openings (PhD, postdoc, undergrad RA, etc.). Description of what the lab offers. Application instructions. |
| **Why needed** | Recruitment funnel. Saves PI from repeating info in emails. |
| **Priority** | OPTIONAL |
| **Data source** | `content/positions.md` (free-form Markdown) |

#### Collaborators / Partners
| Attribute | Value |
|-----------|-------|
| **Contains** | Grid/list of key collaborators with photos, names, affiliations, links |
| **Why needed** | Shows breadth of network. Useful for interdisciplinary researchers. |
| **Priority** | OPTIONAL |
| **Data source** | `data/collaborators.yaml` |

#### Service / Leadership
| Attribute | Value |
|-----------|-------|
| **Contains** | Professional service: reviewing, program committees, editorial boards, organizing committees. |
| **Why needed** | Documents community contributions. Important for tenure. |
| **Priority** | OPTIONAL (can live as CV section) |
| **Data source** | `data/service.yaml` OR section in `data/cv.yaml` |

#### Repositories / Software
| Attribute | Value |
|-----------|-------|
| **Contains** | GitHub repositories with auto-fetched stats (stars, forks, language). Can also include non-GitHub software. |
| **Why needed** | Showcases code contributions. Important for CS/engineering academics. |
| **Priority** | OPTIONAL |
| **Data source** | `data/repositories.yaml` with GitHub usernames and repo identifiers |
| **al-folio equivalent** | `repositories.md` -- works well, keep the approach |

---

### 2.4 OPTIONAL Pages -- Personal / Brand

#### Blog
| Attribute | Value |
|-----------|-------|
| **Contains** | Dated posts with tags, categories, thumbnails. Pagination. RSS feed. Optional comments (Giscus/Disqus). Reading time estimate. Featured posts. |
| **Why needed** | Thought leadership. SEO. Sharing ideas that don't fit in papers. |
| **Priority** | OPTIONAL |
| **Data source** | Collection: `content/blog/` directory, one Markdown file per post |
| **Configuration** | Comments provider. Posts per page. Tag/category display. External post sources (Medium RSS). |

#### Photo Gallery
| Attribute | Value |
|-----------|-------|
| **Contains** | Albums of photos (fieldwork, conferences, lab life, personal). Lightbox viewing. Captions. |
| **Why needed** | Humanizes the academic. Documents fieldwork. Lab culture showcase. |
| **Priority** | OPTIONAL |
| **Data source** | `content/gallery/` with album subdirectories, each with an `index.yaml` for metadata |
| **Not in al-folio** | Yes -- new page type |

#### Bookshelf / Reading List
| Attribute | Value |
|-----------|-------|
| **Contains** | Books read/reading/want-to-read with cover images, ratings, notes |
| **Why needed** | Intellectual personality. Conversation starter. |
| **Priority** | OPTIONAL |
| **Data source** | Collection: `content/books/` OR `data/books.yaml` |
| **al-folio equivalent** | `books.md` with `_books/` collection |

#### Media / Press
| Attribute | Value |
|-----------|-------|
| **Contains** | Links to interviews, podcast appearances, news articles, quotes in media |
| **Why needed** | Credibility for public-facing academics. Helps journalists find past coverage. |
| **Priority** | OPTIONAL |
| **Data source** | `data/media.yaml` |
| **Not in al-folio** | Yes -- new page type |

#### Consulting / Services *(Planned)*
| Attribute | Value |
|-----------|-------|
| **Contains** | Professional consulting offerings, areas of expertise, how to engage |
| **Why needed** | Senior academics and industry-adjacent researchers often consult |
| **Priority** | OPTIONAL |
| **Data source** | `content/consulting.md` |

#### Travel Map
| Attribute | Value |
|-----------|-------|
| **Contains** | Interactive map showing conference locations, institutions visited, fieldwork sites |
| **Why needed** | Visual, fun, shows international presence |
| **Priority** | OPTIONAL |
| **Data source** | `data/travel.yaml` with location coordinates and descriptions |
| **Not in al-folio** | Yes -- new page type. al-folio has Leaflet support but no dedicated travel/map page. |

---

### 2.5 META Pages (Infrastructure)

| Page | Priority | Description |
|------|----------|-------------|
| **404 Page** | CORE | Custom "not found" page with navigation back to home |
| **Contact** | RECOMMENDED | *(Planned)* Dedicated contact page with email, office location, optional form |
| **Search** | RECOMMENDED | Full-text search across all content (publications, posts, projects) |
| **RSS Feed** | RECOMMENDED | Auto-generated, zero config |
| **Sitemap** | CORE | Auto-generated for SEO |
| **robots.txt** | CORE | Auto-generated |

---

## 3. Configuration Philosophy

### 3.1 The 5-Minute Setup Experience

A new user should be able to go from "I cloned the repo" to "I have a live site with my name, photo, and publications" in under five minutes. This requires:

1. **One primary config file:** `site.config.yml` (in project root)
2. **One data file to drop in:** `src/content/publications/papers.bib`
3. **One image to replace:** `public/images/avatar.jpg`
4. **One command to run:** `npm run dev` (or equivalent)

> **Note:** The actual implementation uses `site.config.yml` (not `config/site.yaml` as shown in the example below). The schema below shows the original design; the implemented schema uses flat sections: `site`, `profile`, `social`, `pages`, `theme` (with `style`, `palette`, `random_theme`, `avatars`, `cursor_spotlight`), `publications`, and `blog`.

The `config/site.yaml` should contain:

```yaml
# ============================================
# IDENTITY (required)
# ============================================
name:
  first: "Yue"
  last: "Yang"
title: "PhD Student"
affiliation: "University of North Carolina at Chapel Hill"
email: "yue@cs.unc.edu"
bio: "I am a CS PhD student working on robotics and human-robot interaction."
profile_image: "profile.jpg"  # relative to assets/images/

# ============================================
# SOCIAL LINKS (all optional, comment out unused)
# ============================================
social:
  google_scholar: "NafmySAAAAAJ"
  github: "yy-gx"
  linkedin: "yue-yang-6a1493185"
  twitter: "YYang9923"
  # orcid: ""
  # semantic_scholar: ""
  # dblp: ""

# ============================================
# PAGES (toggle on/off)
# ============================================
pages:
  about: true          # Homepage -- always true
  publications: true   # BibTeX-driven publication list
  cv: true             # CV page (set to "pdf_only" for just a download link)
  projects: false      # Research projects showcase
  teaching: false      # Teaching record
  news: false          # News/updates feed
  blog: false          # Blog with posts
  talks: false         # Talks and presentations
  team: false          # Lab members (lab mode)
  positions: false     # Open positions / join us
  gallery: false       # Photo gallery
  books: false         # Bookshelf / reading list
  repositories: false  # GitHub repositories
  media: false         # Press / media appearances
  travel: false        # Travel map
  awards: false        # Awards page (separate from CV)
  service: false       # Service page (separate from CV)

# ============================================
# NAVIGATION ORDER (only enabled pages shown)
# ============================================
nav_order:
  - about
  - publications
  - projects
  - teaching
  - blog
  - cv
  - team

# ============================================
# THEME
# ============================================
theme:
  color_scheme: "auto"    # "light", "dark", or "auto"
  accent_color: "#2698BA"  # Primary accent color
  font_family: "system"    # "system", "serif", "sans-serif", or Google Font name
  max_width: "930px"

# ============================================
# PUBLICATION SETTINGS
# ============================================
publications:
  bib_file: "publications.bib"  # relative to data/
  highlight_author: ["Yang"]     # Last names to bold
  group_by: "year"               # "year", "type", or "none"
  show_badges: true              # Altmetric, citation counts
  show_thumbnails: true
  max_authors_shown: 3

# ============================================
# HOMEPAGE WIDGETS
# ============================================
homepage:
  show_selected_papers: true
  show_news: true
  news_limit: 5
  show_latest_posts: false
  posts_limit: 3
```

### 3.2 File Structure Philosophy

```
my-academic-site/
|-- config/
|   |-- site.yaml          # Main configuration (the ONE file most users edit)
|-- content/
|   |-- about.md           # Bio text (Markdown)
|   |-- teaching.md        # Teaching page (simple mode)
|   |-- positions.md       # Open positions (free-form)
|   |-- consulting.md      # Consulting page (free-form)
|   |-- blog/              # Blog posts (one .md per post)
|   |   |-- 2024-01-15-my-first-post.md
|   |-- projects/          # Research projects (one .md per project)
|   |   |-- robot-learning.md
|   |   |-- ar-demonstrations.md
|   |-- news/              # News items (one .md per item)
|   |   |-- 2024-10-paper-accepted.md
|   |-- books/             # Bookshelf entries
|   |-- gallery/           # Photo albums
|       |-- fieldwork-2024/
|           |-- index.yaml
|           |-- photo1.jpg
|-- data/
|   |-- publications.bib   # BibTeX file (THE essential data file)
|   |-- cv.yaml            # Structured CV data
|   |-- team.yaml          # Lab members
|   |-- talks.yaml         # Talks list
|   |-- awards.yaml        # Awards list
|   |-- teaching.yaml      # Teaching data (structured mode)
|   |-- collaborators.yaml # Collaborators
|   |-- media.yaml         # Press/media appearances
|   |-- travel.yaml        # Travel map data
|   |-- repositories.yaml  # GitHub repos to feature
|-- assets/
|   |-- images/            # All images
|   |   |-- profile.jpg
|   |   |-- publications/  # Paper thumbnails
|   |   |-- projects/      # Project images
|   |   |-- team/          # Team member photos
|   |-- documents/
|   |   |-- cv.pdf         # Downloadable CV
|   |-- json/
|       |-- resume.json    # JSON Resume (optional, for CV page)
|-- public/                # Static files served as-is
```

### 3.3 Data Format Decisions

| Data Type | Format | Rationale |
|-----------|--------|-----------|
| **Publications** | BibTeX (`.bib`) | Universal academic standard. Every researcher has one. Zero friction. |
| **CV** | YAML (`.yaml`) | Structured enough to render beautifully, human-readable enough to edit by hand. Compatible with JSON Resume via conversion. |
| **Team members** | YAML | Structured data with clear fields (name, role, photo, links). |
| **Talks, Awards, Media** | YAML | Simple key-value lists. Easy to add entries. |
| **Teaching** | YAML or Markdown | YAML for structured course lists; Markdown for free-form descriptions. User chooses. |
| **Projects, Blog, News** | Markdown with frontmatter | Need both structured metadata and rich prose content. |
| **Gallery** | YAML index + image files | Metadata (captions, order) in YAML; images as files. |
| **Site configuration** | YAML | Single source of truth. Familiar to Jekyll/Hugo users. |

---

## 4. Modularity Strategy

### 4.1 Core Principle: Feature Flags, Not Feature Forks

Every page is controlled by a single boolean in `config/site.yaml` under the `pages` key. Setting a page to `false`:
- Removes it from navigation
- Excludes it from the build
- Requires zero cleanup (no deleting files, no commenting out code)

Setting a page to `true`:
- Adds it to navigation automatically
- Looks for the corresponding data/content files
- Renders with sensible defaults even if data files are empty

### 4.2 Progressive Complexity Tiers

**Tier 1 -- "Business Card" (Persona A)**
```yaml
pages:
  about: true
  publications: true
```
Result: Two-page site. Homepage with bio + selected papers. Full publications page. Requires only `config/site.yaml` and `data/publications.bib`.

**Tier 2 -- "Professional Portfolio" (Persona B)**
```yaml
pages:
  about: true
  publications: true
  projects: true
  teaching: true
  cv: true
  news: true
```
Result: Six-page site. Add project Markdown files, a CV YAML, and news items at your pace.

**Tier 3 -- "Personal Platform" (Persona C)**
```yaml
pages:
  about: true
  publications: true
  projects: true
  cv: true
  blog: true
  gallery: true
  books: true
  talks: true
  media: true
```
Result: Full-featured personal site with blog, gallery, and media presence.

**Tier 4 -- "Lab Website" (Persona D)**
```yaml
pages:
  about: true
  publications: true
  projects: true
  team: true
  positions: true
  news: true
  teaching: true
  cv: true
  repositories: true
```
Result: Lab-oriented site with team profiles, open positions, and group identity.

### 4.3 Theming Without Touching Code

All visual customization happens through `config/site.yaml`:

```yaml
theme:
  color_scheme: "auto"         # light/dark/auto
  accent_color: "#2698BA"       # One color controls buttons, links, highlights
  font_family: "Inter"          # Any Google Font or "system"/"serif"/"mono"
  heading_font: "Playfair Display"  # Optional separate heading font
  max_width: "930px"            # Content width
  navbar_fixed: true            # Sticky navbar
  footer_fixed: false           # Sticky footer
  rounded_images: false         # Circular profile photo
  card_style: "shadow"          # "shadow", "border", "flat"
```

For deeper customization, a `custom.css` file in `assets/` is auto-loaded if present -- no need to modify any template files.

### 4.4 Navigation Auto-Configuration

The navbar is automatically generated from enabled pages, in the order specified by `nav_order`. Users never need to edit navigation HTML. Dropdown menus are supported:

```yaml
nav_order:
  - about
  - publications
  - projects
  - dropdown:
      title: "More"
      children:
        - books
        - gallery
        - travel
  - cv
```

### 4.5 Component Widgets

Key content can appear in multiple places via reusable widgets:

| Widget | Can appear on |
|--------|---------------|
| Selected Publications | About page, Project pages |
| Recent News | About page, standalone News page |
| Latest Blog Posts | About page, standalone Blog page |
| Team Grid | About page (compact), standalone Team page (full) |
| Social Links | About page, footer, navbar |
| Search | Navbar, standalone page |

Widget visibility is controlled per-page in frontmatter or globally in config.

---

## 5. Persona-to-Page Matrix

| Page | A: Minimalist | B: Standard | C: Power User | D: Lab Director |
|------|:---:|:---:|:---:|:---:|
| **About** | YES | YES | YES | YES |
| **Publications** | YES | YES | YES | YES |
| **CV** | pdf link | full | full | full |
| **Projects** | -- | YES | YES | YES |
| **Teaching** | -- | YES | maybe | YES |
| **News** | -- | YES | YES | YES |
| **Talks** | -- | maybe | YES | maybe |
| **Awards** | -- | in CV | standalone | in CV |
| **Blog** | -- | -- | YES | maybe |
| **Team/People** | -- | -- | -- | YES |
| **Positions** | -- | -- | -- | YES |
| **Repositories** | -- | maybe | YES | YES |
| **Gallery** | -- | -- | YES | YES |
| **Books** | -- | -- | YES | -- |
| **Media/Press** | -- | -- | YES | maybe |
| **Travel Map** | -- | -- | YES | -- |
| **Collaborators** | -- | -- | maybe | YES |
| **Service** | -- | in CV | in CV | standalone |
| **Contact** | in footer | dedicated | dedicated | dedicated |
| **Search** | -- | YES | YES | YES |
| **RSS** | -- | auto | auto | auto |
| **Newsletter** | -- | -- | YES | maybe |

---

## 6. Key Improvements Over al-folio

### 6.1 Pain Points in al-folio to Fix

1. **Inline SVG social links in Markdown frontmatter.** The current `about.md` has raw SVG icons in the subtitle field. This is fragile, ugly to edit, and error-prone. Social links belong in a data file (`data/socials.yaml` or `config/site.yaml`), rendered by the template.

2. **Jekyll complexity.** Ruby/Bundler/Gemfile dependency hell. 19 plugins. Users struggle with installation. Move to a modern SSG (Next.js, Astro, Hugo) with fewer dependencies.

3. **Monolithic `_config.yml`.** al-folio's config is 646 lines mixing identity, theme, library versions, plugin settings, and build config. Split into: `site.yaml` (user-facing), `build.yaml` (developer-facing, rarely edited).

4. **No page toggle system.** In al-folio, disabling a page means setting `nav: false` in that page's frontmatter AND potentially removing the page file. Should be a single flag in config.

5. **CV requires manual YAML.** The CV data format is custom and non-portable. Should support JSON Resume standard.

6. **No talks page.** Common need, completely missing.

7. **No gallery page.** Photos are only embeddable in blog posts.

8. **No media/press page.** Increasingly important for academics with public profiles.

9. **Team page is rudimentary.** The `profiles.md` approach requires inline config in frontmatter -- does not scale for labs with 15+ members.

10. **No travel/map page.** al-folio includes Leaflet but no dedicated travel page.

### 6.2 New Features to Add

- **BibTeX auto-sync:** *(Planned)* Optional integration with DBLP/Semantic Scholar to auto-update publication list
- **Copy citation button:** One-click copy of BibTeX/APA/MLA citation
- **Publication filtering:** Filter by year, topic tag, venue type
- **Dark mode that works:** al-folio's dark mode is opt-in and incomplete. Should be system-preference-aware by default.
- **Responsive images by default:** Automatic WebP conversion, lazy loading, srcset -- no configuration needed
- **Accessibility:** WCAG 2.1 AA compliance out of the box
- **Performance:** Target Lighthouse 95+ on all metrics
- **i18n support:** *(Planned)* Multi-language sites for international academics
- **Analytics privacy:** *(Planned)* Support privacy-respecting analytics (Plausible, Umami) alongside Google Analytics

---

## 7. Competitive Landscape

| Feature | al-folio (Jekyll) | HugoBlox Academic | Our Template |
|---------|:---:|:---:|:---:|
| 5-min setup | No (Ruby deps) | Partial | YES |
| Page toggles | Manual | Yes | Yes (single config) |
| BibTeX native | Yes (jekyll-scholar) | Partial | Yes |
| Dark mode | Opt-in | Yes | Auto by default |
| Team page | Basic | Yes | Full (with alumni) |
| Blog | Yes | Yes | Yes |
| Talks page | No | Yes | Yes |
| Gallery | No | No | Yes |
| Media/Press | No | No | Yes |
| Travel map | No | No | Yes |
| Newsletter | Basic | No | Yes |
| Performance | Moderate | Good | Target: Excellent |
| Accessibility | Basic | Basic | WCAG 2.1 AA |
| Active community | 12k stars | 3k stars | Target: > al-folio |

---

## 8. Success Metrics

- **Time to first deploy:** Under 5 minutes for Tier 1 (Persona A)
- **Time to full setup:** Under 30 minutes for Tier 2 (Persona B)
- **Lighthouse score:** 95+ across all categories
- **Zero-config pages:** About + Publications work with just `site.yaml` + `publications.bib`
- **Page toggle:** Any page enabled/disabled with a single line change in config, zero side effects
- **Backward compatibility:** Can import al-folio's `papers.bib` and `_data/cv.yml` with no modifications
