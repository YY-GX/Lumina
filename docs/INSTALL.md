# Installation

## Prerequisites

- [Node.js](https://nodejs.org) 20 or later
- npm (comes with Node.js)
- Git

## Setup

### 1. Clone the template

```bash
git clone https://github.com/YY-GX/Lumina.git my-site
cd my-site
```

### 2. Install dependencies

```bash
npm install
```

### 3. Start the dev server

```bash
npm run dev
```

Open [http://localhost:4321](http://localhost:4321) to see the site.

## Deploy to GitHub Pages

### 1. Create a GitHub repository

Create a new repo on GitHub. For a personal site, name it `<username>.github.io`.

### 2. Push your code

```bash
git remote set-url origin https://github.com/<username>/<repo>.git
git push -u origin main
```

### 3. Add the deploy workflow

Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: npm
      - run: npm ci
      - run: npm run build
      - uses: actions/upload-pages-artifact@v3
        with:
          path: dist

  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - id: deployment
        uses: actions/deploy-pages@v4
```

### 4. Enable GitHub Pages

1. Go to your repo **Settings > Pages**
2. Under **Source**, select **GitHub Actions**
3. Save

Push any change and the site deploys automatically.

## Other Platforms

Lumina outputs a static `dist/` folder. It works anywhere that hosts static files:

- **Netlify** — Drag and drop `dist/`, or connect your repo (build command: `npm run build`, publish: `dist`)
- **Vercel** — Import repo, framework auto-detected
- **Cloudflare Pages** — Connect repo, build command: `npm run build`, output: `dist`
- **Self-hosted** — Run `npm run build` and serve `dist/` with any web server

## Commands Reference

| Command | Description |
|---|---|
| `npm run dev` | Start dev server at localhost:4321 |
| `npm run build` | Build static site to `dist/` |
| `npm run preview` | Preview the production build locally |
