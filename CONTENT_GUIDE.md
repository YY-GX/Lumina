# Lumina -- Content Guide

Quick reference for adding and editing content. All content lives in `src/content/`.

---

## Add a Publication

Add a BibTeX entry to `src/content/publications/papers.bib`:

```bibtex
@inproceedings{yourkey2024,
  title={Your Paper Title},
  author={Last, First and Last2, First2},
  booktitle={Conference Name},
  year={2024},
  pdf={https://link-to-pdf},
  code={https://github.com/you/repo},
  selected={true}
}
```

Optional fields: `pdf`, `code`, `video`, `slides`, `doi`, `selected` (shows on homepage).

---

## Add a News Item

Create `src/content/news/your-news.md`:

```markdown
---
title: "Your announcement"
date: 2024-12-01
pinned: false
---
Short description here.
```

Set `pinned: true` to keep it at the top of the list.

---

## Add a Blog Post

Create `src/content/blog/your-post.mdx`:

```markdown
---
title: "Post Title"
date: 2024-12-01
description: "Short summary"
tags: ["tag1", "tag2"]
draft: false
---

Your content in Markdown...
```

Remember to enable the blog in `site.config.yml`: `pages.blog: true`.

---

## Add a Project

Create a folder and file `src/content/projects/project-name/index.md`:

```markdown
---
title: "Project Name"
description: "What it does"
category: "Research"
tags: ["ml", "nlp"]
github: "https://github.com/you/repo"
featured: true
date: 2024-01-01
---

Longer description...
```

Set `featured: true` for a larger card on the projects page.

---

## Edit Your CV

Edit `src/content/cv/cv.yml`. Sections: `education`, `experience`, `skills`, `awards`, `service`.

```yaml
education:
  - degree: "Ph.D. in Computer Science"
    institution: "MIT"
    year: "2017-2021"
    description: "Thesis topic."
```

---

## Add a Course

Edit `src/content/teaching/courses.yml`:

```yaml
courses:
  - course_id: "CS101"
    title: "Intro to CS"
    semester: "Fall"
    year: 2024
    role: "Instructor"
    university: "Your University"
    description: "Course description."
    url: "https://course-url"
```

---

## Enable Optional Pages

In `site.config.yml`, set any page to `true`:

```yaml
pages:
  blog: true      # add posts to src/content/blog/
  talks: true     # add talks to src/content/talks.yml
  team: true      # add members to src/content/team.yml
  awards: true    # uses awards from cv.yml
```

Then add content to the corresponding file in `src/content/`.

---

## Change Theme Color

In `site.config.yml`:

```yaml
theme:
  accent_color: "#DC2626"        # any hex color
  accent_color_dark: "#F87171"   # used in dark mode
```

---

## Custom Domain

1. Create `public/CNAME` with your domain (e.g., `www.yoursite.com`)
2. Update `site.url` in `site.config.yml`
3. Update `site` in `astro.config.mjs`
