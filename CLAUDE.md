# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a personal academic website built with Jekyll using the [al-folio](https://github.com/alshedivat/al-folio) theme. It's deployed to GitHub Pages at gonzalobenegas.github.io.

## Development Commands

### Local Development with Docker (Recommended)
```bash
docker-compose up
```
Site available at http://localhost:8080 with live reload on port 35729.

### Local Development without Docker
```bash
bundle install
pip install jupyter  # for notebook support
bundle exec jekyll serve --lsi
```

### Build for Production
```bash
bundle exec jekyll build --lsi
```
Output goes to `_site/` directory.

## Architecture

### Key Directories
- `_pages/` - Main site pages (about.md, publications.md, cv.md, projects.md, etc.)
- `_bibliography/papers.bib` - BibTeX file for publications (auto-generates publications page via jekyll-scholar)
- `_data/` - YAML data files:
  - `coauthors.yml` - Co-author info with links to their pages
  - `cv.yml` - CV/resume data
  - `repositories.yml` - GitHub repos to display
  - `venues.yml` - Publication venue abbreviations
- `_posts/` - Blog posts
- `_projects/` - Project pages (displayed as cards on /projects/)
- `_news/` - Announcements (displayed on homepage if enabled)
- `_config.yml` - Site configuration and theme settings

### Publications System
Publications are managed via `_bibliography/papers.bib`. The jekyll-scholar plugin processes this file. Author matching uses `scholar.last_name` and `scholar.first_name` arrays in `_config.yml` to highlight the site owner. Custom BibTeX keywords control display: `abbr`, `abstract`, `arxiv`, `pdf`, `code`, `blog`, `poster`, `slides`, `website`, `preview`.

### Deployment
GitHub Actions automatically deploys to `gh-pages` branch on push to `master`. The workflow is in `.github/workflows/deploy.yml`.
