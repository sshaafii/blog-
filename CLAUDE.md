# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Hugo-based personal blog/portfolio site (SHAAFI) focused on a QA to DevOps/SRE journey. The site features a minimalist design with floating tech-related logo animations and technical blog posts about DevOps, Kubernetes, and related topics.

## Build and Development Commands

### Local Development
```bash
# Start Hugo development server with drafts
hugo server -D

# Start server without drafts
hugo server

# Build the site (output to public/)
hugo

# Build with drafts included
hugo -D
```

### Content Management
```bash
# Create a new blog post
hugo new content/blog/post-name.md

# Create content using default archetype
hugo new content/section/file-name.md
```

### Asset Processing
Hugo automatically processes assets during build:
- CSS files in `assets/css/` are concatenated into `public/css/bundle.min.css`
- SVG logos in `assets/images/logos/` are inlined into HTML via Hugo pipes
- No separate build step needed for CSS/JS

## Architecture and Structure

### Site Configuration
- **hugo.toml**: Main configuration file containing:
  - Base URL: https://shaa.fi/
  - Site metadata and SEO settings
  - Syntax highlighting configuration (Monokai theme)
  - Pagination settings (10 posts per page)

### Layout System
Hugo uses a template hierarchy with the following key components:

1. **Base Template** (`layouts/_default/baseof.html`):
   - Root HTML structure
   - Includes floating logos partial
   - Contains header, main content block, and footer

2. **Page Templates**:
   - `layouts/index.html`: Homepage with blog post listing
   - `layouts/_default/single.html`: Individual blog post pages

3. **Partials** (`layouts/partials/`):
   - `head.html`: Meta tags, SEO, CSS asset pipeline
   - `header.html`: Site title/branding
   - `footer.html`: Social links
   - `seo.html`: Structured SEO metadata
   - `floating-logos.html`: Background logo animations

### Asset Pipeline
CSS concatenation happens in `layouts/partials/head.html`:
```go
{{ $main := resources.Get "css/main.css" }}
{{ $floatingLogos := resources.Get "css/floating-logos.css" }}
{{ $responsive := resources.Get "css/responsive.css" }}
{{ $styles := slice $main $floatingLogos $responsive | resources.Concat "css/bundle.css" | resources.Minify }}
```

All three CSS files are combined and minified into a single bundle.

### Styling Architecture
The site uses CSS custom properties for theming:
- **Color scheme**: Black background (#000000) with white/gray text
- **Typography**:
  - Titles: 'Bebas Neue' (uppercase, wide letter-spacing)
  - Body: 'Space Mono' (monospace)
- **Layout**: Max content width of 700px, centered

Three main CSS files:
1. `assets/css/main.css`: Core styles, typography, blog layout
2. `assets/css/floating-logos.css`: Animated background logos with keyframe animations
3. `assets/css/responsive.css`: Mobile/tablet responsive adjustments

### Floating Logos Feature
The site includes animated SVG logos that float in the background:
- Logos are loaded from `assets/images/logos/` and inlined as SVG via Hugo resources
- Each logo has unique keyframe animations (24-32 second loops)
- Positioned with fixed positioning and low opacity (0.18)
- Current logos: Bitcoin, Ethereum, Linux (Tux), Kubernetes (2 variants), Silk Road icon

To add new floating logos:
1. Add SVG to `assets/images/logos/`
2. Add logo div in `layouts/partials/floating-logos.html`
3. Define animation keyframes in `assets/css/floating-logos.css`

### Content Structure
Blog posts live in `content/blog/` as Markdown files with front matter:
```yaml
---
title: "Post Title"
date: 2026-01-10T14:00:00-05:00
excerpt: "Brief description for listing page"
tags: ["tag1", "tag2"]
---
```

The homepage (`layouts/index.html`) automatically lists all pages in the "blog" section.

## Hugo Version
Site built with Hugo v0.154.4+extended (required for SCSS/SASS processing if added in future)

## Important Files
- `hugo.toml`: Site configuration
- `layouts/_default/baseof.html`: Master template
- `layouts/partials/head.html`: Asset pipeline and meta tags
- `assets/css/*.css`: Styling (concatenated during build)
- `content/blog/*.md`: Blog post content
