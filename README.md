# Articles API - GitHub Pages

This repository serves JSON files as static assets via GitHub Pages for the `smartconfigai` organization.

## Setup Instructions

### Repository Naming Options

You have two options for where your files will be hosted:

**Option 1: Root Domain (Recommended for API)**
- Repository name must be: `smartconfigai.github.io`
- Files accessible at: `https://smartconfigai.github.io/api/articles/page-1.json`
- This gives you the cleanest URLs for an API

**Option 2: Project Site**
- Repository can have any name (e.g., `articles-api`)
- Files accessible at: `https://smartconfigai.github.io/articles-api/api/articles/page-1.json`
- Use this if you want multiple projects under the same organization

**Note:** All JSON files are located in the `api/articles/` directory. The relative paths in the metadata (like `"nextPage": "page-2.json"`) work correctly because all files are in the same directory.

### Setup Steps

1. **Create the repository** on GitHub under the `smartconfigai` organization
   - Choose the name based on your preference above
   
2. **Enable GitHub Pages**:
   - Go to repository Settings → Pages
   - Under "Source", select "Deploy from a branch"
   - Choose the `main` branch and `/` (root directory)
   - Click Save
   - OR: The GitHub Actions workflow will automatically deploy (recommended)

3. **Push files to the repository**:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/smartconfigai/[repository-name].git
   git push -u origin main
   ```

## JSON Structure

Each JSON file follows this structure:

```json
{
  "metadata": {
    "currentPage": 1,
    "previousPage": null,
    "nextPage": 2,
    "numArticles": 10,
    "totalArticles": 50
  },
  "data": {
    "articles": [
      {
        "title": "Article Title",
        "content": "Article content...",
        "likes": 42,
        "comments": [
          {
            "author": "User",
            "text": "Great article!"
          }
        ]
      }
    ]
  }
}
```

## File Naming Convention

- Use descriptive names like `page-1.json`, `page-2.json`, etc.
- Or use date-based naming: `2024-01-15.json`
- Files will be accessible based on your repository name (see Example Usage above)

## Example Usage

Once deployed, access your JSON files at:

**If using root domain (`smartconfigai.github.io` repository):**
- `https://smartconfigai.github.io/api/articles/page-1.json`
- `https://smartconfigai.github.io/api/articles/page-2.json`
- `https://smartconfigai.github.io/api/articles/page-3.json`
- `https://smartconfigai.github.io/api/articles/page-5-new.json`
- `https://smartconfigai.github.io/api/articles/page-6.json`

**If using project site (`articles-api` repository):**
- `https://smartconfigai.github.io/articles-api/api/articles/page-1.json`
- `https://smartconfigai.github.io/articles-api/api/articles/page-2.json`
- `https://smartconfigai.github.io/articles-api/api/articles/page-3.json`
- `https://smartconfigai.github.io/articles-api/api/articles/page-5-new.json`
- `https://smartconfigai.github.io/articles-api/api/articles/page-6.json`

**Navigation:** Follow the `nextPage` and `previousPage` metadata fields to navigate through the linked list. The correct path is: page-1 → page-2 → page-3 → page-5-new → page-6. Note that page-4.json and page-5.json exist but are not part of the navigation chain.

