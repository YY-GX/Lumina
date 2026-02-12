# Usage Guide

Everything in Lumina is configured through files — no code editing required for basic use.

---

## Site Configuration

All site-wide settings live in **`site.config.yml`** at the project root.

### Profile

```yaml
profile:
  name: "Your Name"
  position: "PhD Student, Department of Computer Science"
  affiliation: ""                          # optional, appended to position
  university: "Your University"
  email: "you@example.com"
  avatar: "/images/avatar.jpg"             # put image in public/images/
  bio: "Your bio here. **Markdown** is supported."
  bio_short: "One-liner for metadata"
```

### Social Links

```yaml
social:
  google_scholar: "https://scholar.google.com/citations?user=YOUR_ID"
  github: "https://github.com/you"
  twitter: ""          # leave empty to hide
  linkedin: ""
  orcid: ""
  semantic_scholar: ""
  dblp: ""
  email: "you@example.com"
```

Only non-empty links appear on the site.

### Toggle Pages

```yaml
pages:
  about: true
  publications: true
  cv: true
  blog: true
  projects: false       # flip to true when ready
  news: false
  teaching: false
  # ... 18 page types total
```

### Theme

```yaml
theme:
  style: "classic"      # classic, modern, minimal, elegant, bold, geek, newspaper, aurora, ocean, retro
  palette: "navy"        # varies per theme (default, navy, forest, plum, slate for classic)
  cursor_spotlight: false
  random_theme: false    # randomize theme on each visit
  avatars:               # multiple avatars for random rotation
    - "/images/avatar.jpg"
    - "/images/avatar2.png"
```

---

## Adding Publications

### 1. Edit your BibTeX file

Publications are stored in `src/content/publications/papers.bib`. Add entries in standard BibTeX format with optional extra fields:

```bibtex
@inproceedings{yang2025mywork,
  title     = {My Paper Title},
  author    = {Yang, Yue and Collaborator, Name},
  booktitle = {IEEE International Conference on Robotics and Automation (ICRA)},
  year      = {2025},
  selected  = {true},
  preview   = {mywork.png},
  pdf       = {https://arxiv.org/pdf/2025.00000},
  code      = {https://github.com/you/repo},
  video     = {https://youtube.com/watch?v=xxx},
  abstract  = {A brief abstract of the paper.}
}
```

### 2. Add preview images

Place thumbnail images in `public/images/publications/` and reference them by filename in the `preview` field.

### 3. Feature on homepage

Set `selected: true` on up to 5 papers to display them in the homepage "Selected Publications" widget.

---

## Writing Blog Posts

### 1. Create a file

Add a `.mdx` or `.md` file in `src/content/blog/`:

```
src/content/blog/my-first-post.mdx
```

### 2. Add frontmatter

```yaml
---
title: "My First Post"
date: 2025-06-15
description: "A short description for previews."
tags: ["robotics", "tutorial"]
draft: false
---
```

### 3. Write content

Use standard Markdown plus MDX components:

```mdx
## Introduction

Regular markdown works. **Bold**, *italic*, [links](https://example.com).

### Embedding Video

<Video url="https://youtube.com/watch?v=dQw4w9WgXcQ" />

### Math

<Math formula="E = mc^2" />

<Math formula="\int_0^\infty e^{-x} dx = 1" display />
```

Set `draft: true` to hide a post from the live site while you work on it.

---

## Setting Up the CV

Edit `src/content/cv/cv.yml`:

```yaml
education:
  - degree: "Ph.D. in Computer Science"
    institution: "University of Example"
    year: "2021 - Present"
    details: "Advised by Prof. Someone"

experience:
  - title: "Research Intern"
    company: "Big Lab"
    year: "Summer 2024"
    details: "Worked on robotics."

skills:
  - category: "Languages"
    items: ["Python", "TypeScript", "C++"]

awards:
  - title: "Best Paper Award"
    year: "2024"
    details: "Conference Name"

service:
  - role: "Reviewer"
    venue: "ICRA 2025"
```

To include a downloadable PDF, place it at `public/files/cv.pdf`. To hide the download button, set `hide_pdf_download: true` in `site.config.yml`.

---

## Adding News

Create Markdown files in `src/content/news/`:

```markdown
---
title: "Paper accepted at ICRA 2025"
date: 2025-01-15
---

Our paper on robot learning was accepted!
```

The 5 most recent items also appear as a widget on the homepage (when the news page is enabled).

---

## Adding Images

Place all static files in the `public/` directory:

```
public/
  images/
    avatar.jpg            # profile photo
    avatar2.png           # alternate avatar
    publications/         # paper thumbnails
      mywork.png
  files/
    cv.pdf                # downloadable CV
```

Files in `public/` are served at the site root. `public/images/avatar.jpg` becomes `/images/avatar.jpg`.

---

## Project Structure

```
├── site.config.yml          # All site configuration
├── src/
│   ├── content/
│   │   ├── about.md         # Homepage bio (extended)
│   │   ├── blog/            # Blog posts (.md / .mdx)
│   │   ├── cv/cv.yml        # CV data
│   │   ├── news/            # News items (.md)
│   │   ├── projects/        # Project pages
│   │   ├── publications/    # papers.bib
│   │   ├── teaching/        # courses.yml
│   │   ├── team.yml
│   │   ├── talks.yml
│   │   ├── books.yml
│   │   ├── collaborators.yml
│   │   ├── positions.yml
│   │   ├── repositories.yml
│   │   ├── media.yml
│   │   └── travel.yml
│   ├── components/          # Astro components
│   ├── pages/               # Route pages
│   ├── styles/              # CSS themes & palettes
│   └── lib/                 # Utilities & BibTeX parser
├── public/                  # Static assets (images, files)
└── docs/                    # Documentation
```

---

## Tips

- **Preview changes live** — `npm run dev` hot-reloads on every save.
- **Hide pages you don't need** — Set them to `false` in config. They disappear from the navbar instantly.
- **Test the build** — Run `npm run build` before pushing to catch any errors locally.
- **Theme exploration** — Use the palette icon in the navbar to browse all themes live, then set your favorite in config.
