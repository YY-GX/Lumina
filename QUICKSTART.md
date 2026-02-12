# Lumina -- Quick Start

## 1. Set Up (2 minutes)

1. Clone the repo and install dependencies:
   ```bash
   git clone https://github.com/yourusername/lumina.git
   cd lumina
   npm install
   ```
2. Open `site.config.yml` and change the name, bio, university, and social links.
3. Start the dev server:
   ```bash
   npm run dev
   ```
4. Open `http://localhost:4321` in your browser.

## 2. Add Your Content

### Your Info

Edit `site.config.yml` -- change `profile`, `social`, and `site` sections to match yours.

### Publications

Replace `src/content/publications/papers.bib` with your own BibTeX file. Minimal entry:

```bibtex
@inproceedings{you2024paper,
  title={Your Paper Title},
  author={Last, First and Last2, First2},
  booktitle={Conference Name},
  year={2024},
  pdf={https://link-to-pdf},
  code={https://github.com/you/repo},
  selected={true}
}
```

Set `selected={true}` to feature a paper on the homepage.

### Profile Photo

Replace `public/images/avatar.jpg` with your photo. If the filename differs, update `profile.avatar` in `site.config.yml`.

## 3. Deploy

Push to GitHub. The included GitHub Action (`.github/workflows/deploy.yml`) auto-deploys to GitHub Pages.

## 4. Toggle Pages

In `site.config.yml`, set pages to `true` or `false`:

```yaml
pages:
  publications: true   # publication list
  blog: false          # enable when you add posts
  projects: true       # project cards
  teaching: true       # course list
  talks: false         # enable and add src/content/talks.yml
  team: false          # enable and add src/content/team.yml
  awards: false        # pulls from cv.yml
```

Only enabled pages appear in navigation. No code changes needed.
