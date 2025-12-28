# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build Commands

```bash
npm run dev      # Start Gulp watch mode (compiles CSS/JS, enables livereload)
npm run zip      # Package theme as ZIP for Ghost upload
npm test         # Run gscan theme validation
```

## Development Environment

```bash
docker-compose up    # Start Ghost at http://localhost:2368 (admin: /ghost)
docker-compose down  # Stop environment
```

Theme files are hot-reloaded via Docker volume mounts.

## Architecture

This is a Ghost 5.x theme based on TryGhost/Ease. It uses:

- **Handlebars** for templates (.hbs files)
- **PostCSS** for CSS processing (autoprefixer, cssnano, postcss-easy-import)
- **Gulp 5** for build pipeline
- **@tryghost/shared-theme-assets** for base CSS/JS that gets extended

### CSS Pipeline
Entry point: `assets/css/screen.css` imports modular CSS files:
- `general/` - Variables (vars.css) and forms
- `site/` - Layout, header, cover, search, featured-tags
- `blog/` - Post, feed, article, pagination, comments
- `misc/` - Utilities, owl carousel styles

Output: `assets/built/screen.css` (minified with sourcemaps)

### JS Pipeline
Sources concatenated in order:
1. `@tryghost/shared-theme-assets` JS
2. `assets/js/lib/*.js` (jarallax, owl.carousel)
3. `assets/js/main.js`

Output: `assets/built/main.min.js`

### Template Structure
- `default.hbs` - Base layout (header, footer, nav)
- `index.hbs` - Homepage with hero, featured posts carousel, tag grid
- `post.hbs` / `page.hbs` - Content templates
- `partials/` - Reusable components (featured-posts, loop, pagination)

### Theme Customization
Ghost admin exposes options defined in `package.json` under `config.custom`:
- Navigation layout (logo position)
- Title/body font selection
- Featured posts toggle

CSS variables in `assets/css/general/vars.css` control colors and spacing.

## Troubleshooting

### Common Issues

- **CSS doesn't update**: If you are running this in a Docker container, ensure `npm run dev` is run to rebuild the theme.

### Debugging Tips

- Mount new template files in the `docker-compose.yml` file to see changes immediately.