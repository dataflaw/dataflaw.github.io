# CLAUDE.md

This file documents the structure, conventions, and development workflow for this repository, intended to help AI assistants understand the codebase quickly.

## Repository Overview

**dataflaw.github.io** is a personal GitHub Pages static website. It is a single-page HTML/CSS/JS site with no build tooling, no package manager, and no external dependencies.

- **Live URL**: `https://dataflaw.github.io`
- **Hosting**: GitHub Pages (auto-deploys from the `master` branch)
- **Stack**: Vanilla HTML, CSS, JavaScript only

## Repository Structure

```
dataflaw.github.io/
├── index.html       # Single-page website (the entire site)
├── .pages.yml       # GitHub Pages configuration (currently empty)
└── CLAUDE.md        # This file
```

## Current State

`index.html` is currently a blank page — it contains only a minimal HTML shell with an empty `<body>`. The repository's git history shows that a full single-page resume/CV website (for Giri Pancharatnam) was previously built and then intentionally removed. The blank page is the deliberate current state.

## Development Workflow

### Making Changes

Because there is no build step, development is straightforward:

1. Edit `index.html` directly — all HTML, CSS (`<style>`), and JavaScript (`<script>`) live in this single file.
2. Open `index.html` in a browser to preview changes locally.
3. Commit and push to `master` to deploy.

### Deployment

GitHub Pages automatically publishes the `master` branch root to `https://dataflaw.github.io`. There is no CI pipeline, no build command, and no deployment script — pushing to `master` is the deploy.

### Branch Naming

Feature/AI-generated branches follow this pattern:
```
claude/<task-slug>-<session-id>
```
Example: `claude/create-report-website-JmKdm`

Work is developed on a named branch, a pull request is opened, and it is merged into `master`.

## Key Conventions

### HTML/CSS/JS
- All code lives in a single `index.html` file — no separate `.css` or `.js` files.
- CSS goes in a `<style>` block in `<head>`.
- JavaScript goes in a `<script>` block at the end of `<body>`.
- No external frameworks (React, Vue, Bootstrap, etc.) — pure vanilla web platform.
- No package manager (`npm`, `yarn`, etc.) — do not introduce one unless explicitly asked.

### CSS Variables
When writing styles, prefer CSS custom properties (variables) for colours and spacing, defined in `:root`:
```css
:root {
    --primary: #1a2744;
    --accent: #2c5282;
    /* ... */
}
```

### Responsive Design
The site should be mobile-friendly. Use:
- Flexible layouts (`flexbox` or `grid`)
- Media queries for mobile breakpoints
- A hamburger nav pattern for small screens

### No Build Tooling
Do **not** add:
- `package.json` / npm scripts
- Webpack, Vite, Parcel, or any bundler
- TypeScript compilation
- Any preprocessor (Sass, Less, PostCSS)

unless the user explicitly requests it.

## Git History Reference

| Commit | Description |
|--------|-------------|
| `eff67df` | Merge PR #2 — remove all page content, leave blank page |
| `e53938b` | Remove all page content, leave blank page |
| `2a25298` | Merge PR #1 — add resume website |
| `eec5803` | Add single-page resume website for Giri Pancharatnam |
| `35afe36` | Create `.pages.yml` |

The prior full site (commit `eec5803`) was a professional CV for Giri Pancharatnam built with vanilla HTML/CSS/JS. It included: responsive fixed navigation, hero section, timeline-style work experience section, education section, scroll fade-in animations, and contact links. That implementation can serve as a reference for the site's expected design language if the content is rebuilt.

## Common Tasks

### Replace the blank page with new content
Edit `index.html` — replace the empty `<body>` with the desired HTML. Add CSS in `<head>` and JavaScript before `</body>`.

### Add a new section
Add a `<section>` element inside the main content container in `index.html` and corresponding styles in the `<style>` block.

### Check what the site looks like
Open `index.html` directly in a browser — no server is required for a purely static file.

### Deploy
```bash
git add index.html
git commit -m "describe the change"
git push origin master
```
