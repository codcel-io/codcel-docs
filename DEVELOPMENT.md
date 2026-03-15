# Local Development

This guide explains how to build and preview the Codcel documentation on your own machine.

## Prerequisites

- **Python 3.9+** — check with `python3 --version`
- **pip** — included with most Python installations

## Setup

1. Clone the repository:

   ```bash
   git clone https://github.com/codcel-io/codcel-docs.git
   cd codcel-docs
   ```

2. (Optional) Create a virtual environment:

   ```bash
   python3 -m venv .venv
   source .venv/bin/activate   # macOS / Linux
   .venv\Scripts\activate      # Windows
   ```

3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

## Preview Locally

Start the local development server with live reload:

```bash
mkdocs serve
```

Open **http://localhost:8000** in your browser. Changes to any Markdown file will automatically reload.

## Build the Site

Build the full static site into the `site/` directory:

```bash
mkdocs build --strict
```

The `--strict` flag treats warnings as errors, matching what CI runs on every push.

## Project Structure

```
codcel-docs/
├── mkdocs.yml              # MkDocs configuration and navigation
├── requirements.txt        # Python dependencies
├── user-guide/             # All documentation (this is the MkDocs docs_dir)
│   ├── index.md            # Home page
│   ├── introduction.md     # Getting started guides
│   ├── ...                 # Other guide pages
│   ├── mathematical-functions/   # Individual function reference pages
│   ├── statistical-functions/
│   └── ...                 # Other function categories
└── assets/                 # Logo files (used by README on GitHub)
```

- **`mkdocs.yml`** — controls the site name, theme, navigation, and plugins.
- **`user-guide/`** — all Markdown files live here. MkDocs serves this as the root.
- **Navigation** — top-level sections are defined explicitly in `mkdocs.yml`. Individual function pages (460+) are not in the sidebar — they are accessed via links from category index pages.

## Adding a New Page

1. Create a `.md` file inside `user-guide/` (or the appropriate subdirectory).
2. If the page should appear in the sidebar navigation, add it to the `nav` section in `mkdocs.yml`.
3. If the page is a function reference, add a link to it from the relevant category index page (e.g., `mathematical-functions.md`). It does not need to be added to `mkdocs.yml`.

## Deployment

Documentation is automatically deployed to GitHub Pages on every push to `main` via the GitHub Actions workflow in `.github/workflows/docs.yml`. No manual deployment is needed.
