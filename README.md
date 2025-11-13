# Articles API

Static JSON API served via GitHub Pages.

## Structure

- JSON files are in `api/articles/`
- Files use linked list navigation via `nextPage`/`previousPage` metadata
- Navigation path: page-1 → page-2 → page-3 → page-5 → page-6 (page-4 is orphaned)

## Deployment

Deployed via GitHub Actions to GitHub Pages. Files are accessible at:
- `https://smartconfigai.github.io/articles-api/api/articles/page-1.json`
