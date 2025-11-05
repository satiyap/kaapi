# Kaapi Theme

A minimal, responsive Hugo theme inspired by filter coffee which simply happens to be my favourite kind of coffee.

## Features

- **Strong Typography** - Clear hierarchy with carefully sized headings and body text
- **Filter Coffee Aesthetics** - Deep brown color palette inspired by filter coffee
- **Animated Progress Bars** - Elegant hover animations on post titles
- **Single Author Focus** - Built for personal blogs with integrated About page
- **Table of Contents** - Optional TOC with front matter flag (`toc: true`)
- **Responsive Design** - Mobile-first, looks great on all devices
- **Fast & Lightweight** - Minimal JavaScript, clean CSS
- **Custom Summaries** - Control post descriptions with `description` parameter
- **Syntax Highlighting** - Beautiful code blocks ready out of the box
- **Clean Navigation** - Simple header with site title and About link

## Installation

### As a Hugo Module (recommended)

```bash
hugo mod init github.com/yourusername/yoursite
```

Add the theme to your `hugo.toml`:

```toml
[module]
  [[module.imports]]
    path = "github.com/yourusername/kaapi"
```

### As a Git Submodule

```bash
git submodule add https://github.com/yourusername/kaapi.git themes/kaapi
```

Then add to your `hugo.toml`:

```toml
theme = "kaapi"
```

### Manual Installation

Clone this repository into your `themes` directory:

```bash
cd themes
git clone https://github.com/yourusername/kaapi.git
```

## Configuration

Example `hugo.toml` configuration:

```toml
baseURL = 'https://example.org/'
languageCode = 'en-US'
title = 'Your Blog Title'
theme = 'kaapi'

[params]
  description = 'A blog about topics that matter'
  author = 'Your Name'
  themeName = 'Kaapi Theme'

[markup]
  [markup.tableOfContents]
    startLevel = 2
    endLevel = 2
    ordered = false
  [markup.highlight]
    style = 'monokai'
    lineNos = true
    lineNumbersInTable = true
    noClasses = false

[module]
  [module.hugoVersion]
    extended = false
    min = '0.146.0'
```

### Optional: Social Links (Coming Soon)

Social links support is planned for a future release.

## Content Structure

### Creating Posts

Create a new post:

```bash
hugo new posts/my-first-post.md
```

Example post front matter with all features:

```yaml
---
title: "My First Post"
date: 2025-01-15
tags: ["hugo", "blog"]
description: "A concise summary that appears on the homepage listing"
toc: true  # Enable table of contents (optional)
---

Your content here...
```

**Important Front Matter Fields:**

- `title` - Post title (required)
- `date` - Publication date (required)
- `tags` - Array of tags (optional)
- `description` - Custom summary for homepage (recommended)
- `toc` - Set to `true` to show table of contents (optional)

### Post Descriptions

The `description` field in front matter controls what appears on the homepage:

```yaml
description: "A short, compelling summary of your post that entices readers to click."
```

If you don't provide a description, no summary will appear on the homepage.

### Table of Contents

To enable TOC on a post, add `toc: true` to the front matter:

```yaml
---
title: "Long Post with Many Sections"
toc: true
---
```

The TOC will automatically generate from your **H2 headings only** (major sections). This keeps the TOC clean and focused on main topics without cluttering it with subsections.

If you want to include H3 and H4 headings in the TOC, update your `hugo.toml`:

```toml
[markup.tableOfContents]
  endLevel = 4  # Show H2, H3, and H4
```

### Page Bundles

You can organize posts with images and resources using page bundles:

```
content/
└── posts/
    └── my-post/
        ├── index.md
        └── image.jpg
```

## About Page Setup

Kaapi is designed for single-author blogs with a built-in About page.

### Quick Setup

1. **Edit the default About page:**

   ```bash
   # Edit the theme's about page directly
   themes/kaapi/content/about.md
   ```

2. **Or override with your own (recommended):**

   ```bash
   # Create your own about page
   hugo new about.md

   # Edit content/about.md with your information
   ```

The About link automatically appears in the header next to your site title.

### About Page Example

```markdown
---
title: "About"
date: 2025-01-20
---

## About Me

Your bio and introduction here.

## What I Write About

- Topic 1
- Topic 2
- Topic 3

## Get in Touch

- **Email**: your@email.com
- **GitHub**: [@yourusername](https://github.com/yourusername)
```

The About page will NOT appear in your post listings—it's accessible only via the header link.

## Customization

### Colors and Styling

The theme uses a filter coffee inspired color palette defined in `assets/css/main.css`. Key colors:

- **Background**: `#fdfcfa` (Warm cream)
- **Text Primary**: `#1a0f08` (Deep brown)
- **Text Secondary**: `#3d2817` (Medium brown)
- **Accent Primary**: `#8b4513` (Saddle brown - filter coffee)
- **Accent Secondary**: `#6b3410` (Deep brown)
- **Borders**: `#d9cfc4` (Light tan)

**CSS Variables:**

```css
:root {
  --bg-primary: #fdfcfa;
  --text-primary: #1a0f08;
  --accent-primary: #8b4513;
  --gradient-accent: linear-gradient(135deg, #6b3410 0%, #8b4513 40%, #a0522d 70%, #cd853f 100%);
}
```

To customize, create your own CSS file in your site's `assets/css/main.css` and it will override the theme's CSS.

### Typography

The theme uses a carefully crafted typographic scale:

**Desktop:**
- Site Title: 38px (weight 800)
- Post Titles: 26px (weight 800)
- H2: 26px, H3: 22px, H4: 19px
- Body: 17px

**Mobile:**
- Site Title: 30px
- Post Titles: 23px
- Body: 16px

### Templates

All templates follow Hugo's standard lookup order. You can override any template by creating the same file structure in your site's `layouts/` directory.

Key templates:
- `layouts/baseof.html` - Base template with HTML structure
- `layouts/home.html` - Homepage with post listings
- `layouts/page.html` - Single page/post template
- `layouts/_partials/header.html` - Site header with title and About link
- `layouts/_partials/footer.html` - Site footer with attribution
- `layouts/_partials/toc.html` - Table of contents (when enabled)

## Development

### Testing the Theme

To test the theme locally:

```bash
# From the theme directory
hugo server --source exampleSite
```

Or create a test site:

```bash
hugo new site testsite
cd testsite
git init
git submodule add ../kaapi themes/kaapi
echo "theme = 'kaapi'" >> hugo.toml
hugo server
```

### Building

```bash
hugo
```

The built site will be in the `public/` directory.

## Browser Support

Kaapi supports all modern browsers:
- Chrome/Edge (last 2 versions)
- Firefox (last 2 versions)
- Safari (last 2 versions)

## Theme Philosophy

Kaapi is named after filter coffee (காபி in Tamil), which is:

- **Strong** - Bold flavors
- **Patient** - Brewed slowly, 10-15 minutes
- **Focused** - Simple equipment, quality beans, proper technique
- **Authentic** - No trends, just what works

This theme follows the same principles:

- Strong typography and clear hierarchy
- Patient in twiddling my thumbs while claude does its thing
- Focused on single-author blogs
- Authentic to its purpose—writing and reading

## Design Decisions

### Why Single Author?

Most personal blogs don't need complex author systems. Kaapi removes that complexity and gives you:
- One About page
- Simple navigation
- Focus on content, not infrastructure

### Why No Dark Mode?

The filter coffee palette is carefully crafted for readability. Adding dark mode would dilute the design. If you need dark mode, this might not be your theme—and that's okay.

### Why Manual Descriptions?

Auto-generated summaries rarely capture what matters. The `description` field forces you to write compelling summaries, making your homepage more effective.

### Why Flag-Based TOC?

Not every post needs a TOC. Long guides do, short posts don't. The `toc: true` flag gives you control without clutter.

## Animations

The theme includes one signature animation:

**Post Title Underline:** Hover over post titles (homepage or single page) to see an elegant left-to-right progress bar animation. It's reversible—slides back when you move your mouse away.

This is the ONLY animation. No page transitions, no loading spinners, no distractions.

## FAQ

**Q: Can I use this for multi-author blogs?**
A: No. Use a different theme. Kaapi is intentionally single-author focused.

**Q: Can I add dark mode?**
A: You can, but you'll need to customize the CSS yourself. It's not part of the theme's design.

**Q: Why filter coffee?**
A: Because it represents the theme's philosophy: strong, patient, and authentic. Also, the creator drinks too much of it.

**Q: Will you add feature X?**
A: Maybe. If it fits the minimal, single-author philosophy. Open an issue and we'll discuss.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. Keep in mind:

- Maintain the minimal aesthetic
- Don't add complexity for edge cases
- Test responsiveness
- Follow the existing code style

## License

This theme is released under the MIT License. See LICENSE for details.

## Credits

- Inspired by filter coffee
- Typography influenced by reading-focused designs
- Built with claude
