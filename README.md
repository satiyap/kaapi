# Kaapi Hugo Theme

**Kaapi** (காபி) — South Indian filter coffee — is a bold, strong Hugo theme inspired by the authentic character of traditional filter kaapi. Like the dark, rich decoction brewed slowly through the filter, this theme is intense, no-compromise design that energizes your content.

## ✨ Features — Filtered to Perfection

- **☕ Authentic Filter Coffee Palette** - Deep browns (#8b4513, #6b3410), bold contrasts, no pale colors
- **🌑 Strong Dark Mode** - Like the decoction itself (#0d0805), dark and intense
- **🎨 Bold Typography** - Clear hierarchy with strong gradient accents
- **📱 Fully Responsive** - Great on every device, from tumbler to dabara
- **⚡ Fast & Strong** - No dilution, pure performance
- **📑 Table of Contents** - Auto-generated navigation for complex posts
- **⏱️ Reading Time** - Know the commitment before you start
- **🎯 Syntax Highlighting** - Code as clear as filtered coffee
- **🔗 Social Links** - Optional social media icons in footer
- **♿ Accessible** - Proper contrast and semantic HTML
- **🎭 Bold Animations** - Strong, purposeful interactions
- **📊 Rich Content** - Tables, blockquotes, lists — all bold

## 🎨 The Filter Coffee Philosophy

**Color Palette — Strong & Authentic:**
- **Light Mode**: Clean white backgrounds (#fdfcfa), bold dark brown text (#1a0f08), strong accents (#8b4513)
- **Dark Mode**: Deep decoction (#0d0805), rich browns (#1a1108), golden highlights (#cd853f)

**No Light Browns** — Following authentic filter coffee:
- Darkest brown: #6b3410 (deep filter coffee)
- Mid brown: #8b4513 (saddle brown)
- Accent: #cd853f (peru/golden)
- **NO pale or light browns** — filter coffee is strong, not diluted

**Filter Coffee Details:**
- Strong gradient underlines on headers
- Bold coffee ring stains on interactive elements
- Deep shadows with dark brown tints (#6b3410)
- Intense, uncompromising color choices

**Typography:**
- System font stack for speed
- Bold gradient text effects
- High contrast for clarity
- Line-height 1.7 for comfortable reading

**Interactions:**
- Strong transitions — no weak fades
- Bold hover effects with dark browns
- Purposeful animations
- Clear visual feedback

## Quick Start

```bash
# Start the development server
hugo server

# Create a new post
hugo new posts/my-first-post.md

# Build the site
hugo
```

## Theme Documentation

See the theme's [README](themes/kaapi/README.md) for detailed documentation.

## Project Structure

- `themes/kaapi/` - The Kaapi theme
- `content/` - Your site content (create this directory and add markdown files)
- `hugo.toml` - Site configuration
- `CLAUDE.md` - Developer guidance for Claude Code

## Getting Started

1. Create content directory:
   ```bash
   mkdir -p content/posts
   ```

2. Create your first post:
   ```bash
   hugo new posts/hello-world.md
   ```

3. Edit the post in `content/posts/hello-world.md` and set `draft: false`

4. Run the development server:
   ```bash
   hugo server
   ```

5. Visit http://localhost:1313

## Customization

### Social Links

Add social links to your footer by editing `hugo.toml`:

```toml
[params.social]
  github = 'yourusername'
  twitter = 'yourusername'
  linkedin = 'yourusername'
  email = 'your@email.com'
  rss = '/index.xml'
```

### Color Scheme

The theme uses CSS custom properties, making it easy to customize. Create a custom CSS file to override:

```css
:root {
  --accent-primary: #your-color;
  --gradient-accent: linear-gradient(135deg, #color1, #color2);
}
```

### Advanced Customization

- Add custom CSS by creating `assets/css/custom.css`
- Override theme templates by creating matching files in `layouts/`
- Modify table of contents settings in `hugo.toml` under `[markup.tableOfContents]`

## Resources

- [Hugo Documentation](https://gohugo.io/documentation/)
- [Kaapi Theme README](themes/kaapi/README.md)
- [CLAUDE.md](CLAUDE.md) - Developer guidance
