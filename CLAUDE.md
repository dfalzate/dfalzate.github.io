# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is Diego Alzate's personal portfolio website. It is a static website originally built with **Create React App** and deployed to GitHub Pages. The repository contains only the production build output, not source code.

The website showcases AI/ML projects with interactive Jupyter notebook exports.

## Repository Structure

```
├── index.html                  # Main entry point (minified React app shell)
├── asset-manifest.json         # Build manifest mapping hashed filenames
├── manifest.json               # PWA manifest
├── favicon.ico                 # Site favicon
├── robots.txt                  # SEO robots file
├── static/
│   ├── css/main.*.css          # Minified stylesheets
│   ├── js/main.*.js            # Minified React app bundle
│   ├── js/*.chunk.js           # Lazy-loaded chunks
│   └── media/                  # Static images (me.png, bow.png)
├── js/                         # Legacy webpack bundles (may be unused)
└── projects/                   # Jupyter notebook HTML exports
    ├── ComputerVision.html
    ├── DeepLearning.html
    ├── EnsembleTechniques.html
    ├── NLP.html
    ├── SupervisedLearning.html
    └── UnsupervisedLearning.html
```

## Important Notes

- **No source code**: This repository contains only compiled/minified build artifacts. The original React source code (src/, public/) is not present.
- **No build tools**: There is no `package.json`, build scripts, or development server configuration in this repository.
- **Static hosting**: The site is designed to be served as static files (e.g., GitHub Pages).

## Serving the Site Locally

Since this is a static website with absolute paths (e.g., `/static/js/main.*.js`), use a local server from the repository root:

```bash
# Option 1: Python 3
python3 -m http.server 8000

# Option 2: Node.js (if installed)
npx serve .

# Option 3: PHP
php -S localhost:8000
```

Then open http://localhost:8000

## Adding New Projects

Projects in the `projects/` folder are standalone Jupyter notebook HTML exports. To add a new project:

1. Export your Jupyter notebook as HTML (File → Download as → HTML)
2. Save it to `projects/YourProjectName.html`
3. The main React app likely has navigation that needs updating in the original source code repository (not this one)

## File Modification Guidelines

- **index.html**: Can be edited to update meta tags, title, or analytics scripts. The `<script>` and `<link>` tags reference hashed filenames defined in `asset-manifest.json`.
- **CSS**: Modify `static/css/main.*.css` directly if needed, though changes may be limited by the minified class names.
- **Projects**: The HTML files in `projects/` are complete standalone pages and can be edited directly.

## Asset References

Static assets use hashed filenames. Check `asset-manifest.json` for the current mappings:
- Main CSS: `/static/css/main.6a21b4f8.css`
- Main JS: `/static/js/main.01f8c42b.js`

If adding new static assets, place them in the appropriate `static/` subdirectory and update references in `index.html` or other files.
