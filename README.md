# My CV, auto-deployed with GitHub Actions

## Repository Overview

This is a LaTeX-based CV repository that generates both English and French versions of my CV. The repository uses GitHub Actions to automatically build PDFs and deploy them to GitHub Pages.

## Core Files

- `cv.tex` - English CV source file (LaTeX)
- `cv-fr.tex` - French CV source file (LaTeX)
- `index.html` - Redirects to English CV PDF
- `fr/index.html` - Redirects to French CV PDF

## Build Commands

**Build CV locally:**

```bash
make all          # Builds cv.pdf from cv.tex using latexmk
```

**Clean build artifacts:**

```bash
make clean        # Removes auxiliary LaTeX files (.aux, .bbl, .log, etc.)
make distclean    # Removes auxiliary files and PDF
```

**Manual LaTeX build:**

```bash
latexmk -pdf cv.tex     # Build English CV
latexmk -pdf cv-fr.tex  # Build French CV
```

## Architecture

### Build Process

- Local builds use `latexmk` via Makefile
- GitHub Actions automatically builds both CV versions on push to main
- Built PDFs are deployed to `build` branch and served via GitHub Pages
- Index files provide automatic redirection to PDFs

### GitHub Actions Workflow

1. **Build**: Compiles both CV versions using `dante-ev/latex-action`
2. **Deploy**: Moves PDFs to GitHub Pages deployment
3. **Copy-Index**: Copies HTML redirect files to build branch

### File Structure

- PDFs are generated in CI/CD and not committed to main branch
- HTML files allow automatic redirection to PDFs

## LaTeX Dependencies

The CV uses standard LaTeX packages including:

- `geometry` for page layout
- `xcolor` for colors
- `tabularx` for tables
- `enumitem` for lists
- `titlesec` for custom sections
- `hyperref` for links (implied from usage)

## Deployment

- Repository serves CVs at GitHub Pages
- English CV: `https:cv.mohamedtahiri.com/cv.pdf`
- French CV: `https:cv.mohamedtahiri.com/fr/cv.pdf`
