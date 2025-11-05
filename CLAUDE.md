# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Kaapi** is a minimal, responsive Hugo theme inspired by filter coffee which simply happens to be my favourite kind of coffee.

## Essential Commands

### Development
```bash
# Start development server from theme directory
hugo server --source exampleSite

# Start development server from a site using this theme
hugo server

# Build the site
hugo

# Create new content
hugo new posts/my-post.md
hugo new posts/my-post/index.md  # For page bundles
```

### Theme Testing
```bash
# Create a test site to test the theme
hugo new site testsite
cd testsite
ln -s ../themes/kaapi themes/kaapi  # Or use git submodule
hugo server
```

## Architecture

### Directory Structure

```
themes/kaapi/
├── archetypes/        # Content templates for `hugo new`
├── assets/
│   ├── css/          # Stylesheets (processed by Hugo Pipes)
│   └── js/           # JavaScript files (optional)
├── content/          # Example content for theme demo
├── layouts/          # Template files
│   ├── _partials/    # Reusable template components
│   ├── baseof.html   # Base template (defines HTML structure)
│   ├── home.html     # Homepage template
│   ├── page.html     # Single page template
│   ├── section.html  # Section list template
│   ├── taxonomy.html # Taxonomy list (e.g., all tags)
│   └── term.html     # Term list (e.g., posts with specific tag)
├── static/           # Static assets (copied as-is to output)
├── hugo.toml         # Example site configuration
├── theme.toml        # Theme metadata
└── README.md         # Theme documentation
```

### Template Hierarchy

Hugo uses a template lookup order. Key templates in this theme:

1. **baseof.html** - Base template that wraps all pages with:
   - HTML structure
   - Header (via partial)
   - Main content block (defined by child templates)
   - Footer (via partial)
   - Container wrapper for centered content

2. **home.html** - Homepage template that:
   - Displays site content from `content/_index.md`
   - Lists only posts (filters by Type "posts" using `where site.RegularPages "Type" "posts"`)
   - Shows custom descriptions from front matter `description` field
   - Excludes About page from post listings
   - Shows dates and "Read more" links with animated arrow

3. **page.html** - Single page/post template that:
   - Displays page title with animated underline on hover (LTR on hover, RTL on mouse out)
   - Shows date and reading time
   - Optional table of contents (if `toc: true` in front matter)
   - Renders full content
   - Shows tags at the bottom (via terms partial)

4. **section.html** - Section list template (e.g., `/posts/`)
   - Similar to home.html but scoped to section pages
   - Shows section title and content
   - Lists pages within that section

5. **taxonomy.html** - Lists all terms in a taxonomy (e.g., `/tags/`)
   - Displays taxonomy title
   - Shows all tags as clickable badges

6. **term.html** - Lists pages for a specific term (e.g., `/tags/hugo/`)
   - Shows term title
   - Lists all pages with that tag using the post-item layout

### Partials

Reusable components in `layouts/_partials/`:

- **header.html** - Site title (linked to home) and About link navigation
- **footer.html** - Theme attribution
- **menu.html** - Navigation menu renderer (legacy, not used in current design)
- **terms.html** - Displays tags/categories as styled badges
- **toc.html** - Table of contents (enabled with `toc: true` front matter)
- **head.html** - HTML `<head>` section with meta tags, CSS, and JS includes
- **head/css.html** - CSS asset pipeline (Hugo Pipes processes `assets/css/main.css`)
- **head/js.html** - JavaScript asset pipeline

### Styling Approach

The theme uses a single CSS file (`assets/css/main.css`) with:

- **Filter Coffee Color Palette**:
  - Background: `#fdfcfa` (warm cream)
  - Text Primary: `#1a0f08` (deep brown)
  - Text Secondary: `#3d2817` (medium brown)
  - Accent Primary: `#8b4513` (saddle brown - filter coffee)
  - Accent Secondary: `#6b3410` (deep brown)
  - Borders: `#d9cfc4` (light tan)
  - Gradient: Deep browns only (#6b3410 → #8b4513 → #a0522d → #cd853f)

- **Typography Hierarchy**:
  - Desktop: Site title 38px, Post titles 26px, H2 26px, H3 22px, H4 19px, Body 17px
  - Mobile: Site title 28px, Post titles 24px/22px, H2 20px, H3 18px, H4 16px, Body 16px

- **System font stack**: -apple-system, BlinkMacSystemFont, Segoe UI, Roboto, Inter, etc.
- **Container-based layout**: Max-width 760px, centered with padding
- **Responsive design**: Mobile-first with breakpoint at 768px

- **Key CSS classes**:
  - `.container` - Main centered wrapper (760px max-width)
  - `.site-title-wrapper` - Flexbox for header with site title and About link
  - `.author-nav` - About link in header
  - `.post-list` - Container for post listings
  - `.post-item` - Individual post in a list
  - `.post-meta` - Date and metadata
  - `.post-summary` - Post excerpt
  - `.tags` - Tag container
  - `.tag` - Individual tag badge
  - `.toc` - Table of contents container

## Development Workflow

### Making Template Changes

1. Edit templates in `themes/kaapi/layouts/`
2. Hugo automatically reloads when running `hugo server`
3. Test across different page types (home, single, list, taxonomy)

### Styling Changes

1. Edit `themes/kaapi/assets/css/main.css`
2. Hugo Pipes automatically processes changes
3. Test responsive behavior at different viewport sizes

### Content Structure

Content organization follows Hugo conventions:

```
content/
├── _index.md              # Homepage content
├── about.md               # Single page (/about/)
└── posts/                 # Section
    ├── _index.md          # Section landing page (/posts/)
    ├── first-post.md      # Single post
    └── another-post/      # Page bundle
        ├── index.md       # Post content
        └── image.jpg      # Post resource
```

### Front Matter

Standard front matter for posts:

```yaml
---
title: "Post Title"
date: 2025-01-15
tags: ["tag1", "tag2"]
description: "Custom summary for homepage listing (recommended)"
toc: true  # Optional: enable table of contents
draft: false
---
```

**Important fields**:
- `description` - Custom summary shown on homepage (if omitted, no summary appears)
- `toc` - Set to `true` to show table of contents (defaults to H2 headings only)

## Key Design Principles

1. **Single Author Focus**: Built for personal blogs with integrated About page (not multi-author)
2. **Filter Coffee Philosophy**: Strong, patient, focused—like South Indian filter coffee
3. **Minimalism**: Clean, distraction-free reading experience
4. **Typography**: Strong hierarchy with carefully sized headings (38px site title → 26px posts → body 17px)
5. **Minimal Animation**: ONLY one animation—post title underline on hover (reversible with CSS transitions)
6. **Spacing**: Generous whitespace for better readability
7. **Responsiveness**: Mobile-first, single-column layout with proper mobile typography
8. **Performance**: No JavaScript dependencies, minimal CSS, single CSS file
9. **Manual Descriptions**: Forces thoughtful summaries via `description` field (no auto-generated excerpts)
10. **Simplicity**: Straightforward template structure, easy to understand and modify

## About Page Setup

The theme includes a default About page at `themes/kaapi/content/about.md`:

1. **Edit the default**: Modify `themes/kaapi/content/about.md` directly
2. **Override (recommended)**: Create `content/about.md` in your site root to override

The About link appears in the header next to the site title. The About page will NOT appear in post listings on the homepage.

## Table of Contents Configuration

By default, TOC shows **only H2 headings** (major sections). To change this in `hugo.toml`:

```toml
[markup.tableOfContents]
  startLevel = 2
  endLevel = 2  # Change to 4 to include H2, H3, H4
  ordered = false
```

Enable TOC on individual posts with front matter: `toc: true`

## Customization Points

Users can override:

1. **Templates**: Create matching file in site's `layouts/` directory
2. **CSS**: Create `assets/css/main.css` in site to override theme CSS
3. **Partials**: Override any partial by creating same path in site's `layouts/_partials/`
4. **Configuration**: Set params, menus, and taxonomies in `hugo.toml`
5. **About Page**: Create `content/about.md` to override default

## Critical Styling Rules

### Animation Policy
**IMPORTANT**: This theme has ONE animation only—the post title underline progress bar.

- Post title underline animates LTR on hover, RTL on mouse out (using CSS `transition`, not `animation`)
- Read more arrow has infinite slide animation on hover only
- **NO OTHER ANIMATIONS** should be added (no fadeIn, transforms, page transitions, etc.)
- Use CSS transitions for reversible effects, never keyframe animations except for the arrow

### Typography Rules
- Site title MUST be larger than post titles
- Maintain strict hierarchy: Site title (38px) > Post titles (26px) > Content headings
- Mobile typography must scale proportionally with proper hierarchy
- Never make article h1 and h2 the same size

### Color Palette Rules
- Use only filter coffee browns (no light tan, beige, or cream accents)
- Gradients must use deep browns only: `#6b3410` → `#8b4513` → `#a0522d` → `#cd853f`
- No dark mode toggle or support (intentional design decision)

### Homepage Filtering
- Homepage MUST filter to only show posts: `{{ range where site.RegularPages "Type" "posts" }}`
- About page should NOT appear in post listings
- Use `description` field from front matter (no auto-generated summaries)

## Hugo Template Functions Used

Common functions in templates:
- `{{ .Content }}` - Rendered page content
- `{{ .Title }}` / `{{ .LinkTitle }}` - Page titles
- `{{ .Date }}` - Page date
- `{{ .Params.description }}` - Custom description from front matter (used on homepage)
- `{{ .Summary }}` - Auto-generated summary (used in section/term pages)
- `{{ .Truncated }}` - Whether summary was truncated
- `{{ .ReadingTime }}` - Estimated reading time in minutes
- `{{ .TableOfContents }}` - Auto-generated TOC
- `{{ .RelPermalink }}` - Relative URL to page
- `{{ range .Pages }}` - Iterate over pages
- `{{ range where site.RegularPages "Type" "posts" }}` - **Critical**: Filter to only show posts (excludes About)
- `{{ site.Title }}` - Site title from config
- `{{ site.RegularPages }}` - All regular pages
- `{{ partial "name.html" . }}` - Include partial template
- `{{ partialCached "name.html" . }}` - Include cached partial (for performance)
- `{{ .GetTerms "taxonomy" }}` - Get page's taxonomy terms
- `{{ time.Format "2006-01-02" .Date }}` - Format dates (machine-readable)
- `{{ time.Format "January 2, 2006" .Date }}` - Format dates (human-readable)

## Testing Checklist

When making changes, verify:
- [ ] Homepage displays only posts (About page excluded)
- [ ] Custom `description` field shows on homepage
- [ ] About link appears in header and works
- [ ] Post titles have hover animation (underline grows LTR, shrinks RTL)
- [ ] Read more arrow animates on hover
- [ ] Single posts render with proper formatting
- [ ] TOC appears when `toc: true` is set (H2 headings only by default)
- [ ] Tags display and link correctly
- [ ] Typography hierarchy correct: Site title (38px) > Post titles (26px) > Body (17px)
- [ ] Mobile typography maintains proper hierarchy (28px > 24px/22px > 20px > 18px > 16px)
- [ ] Responsive layout works on mobile (< 768px)
- [ ] Filter coffee color palette throughout (browns, no light hues)
- [ ] Header alignment looks balanced (site title and About link)
- [ ] No unwanted animations or transitions
- [ ] Hugo build completes without errors
- [ ] Hard refresh (Ctrl+Shift+R) if styles don't update
