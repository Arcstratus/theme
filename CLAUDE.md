# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

### Build and Development
- `npm run build` - Build the theme for production using Rollup
- `pnpm run zip` - Build and create a zip file in dist/ for Ghost deployment  
- `pnpm run deploy` - Build, zip, and upload theme to Ghost via Admin API
- `npm test` - Run Ghost theme validation using gscan

### Development Workflow
The build system uses Rollup with live reload during development. In non-production builds, the system watches for changes to Handlebars templates (.hbs), CSS, and JS files.

## Architecture

This is a Ghost CMS theme built with:

### Core Technologies
- **Handlebars (.hbs)** - Template engine for Ghost themes
- **Tailwind CSS v4** - Utility-first CSS framework with custom design tokens
- **Rollup** - Module bundler with PostCSS processing
- **Ghost Admin API** - For programmatic theme deployment

### Project Structure
- `templates/` - Handlebars templates for different page types (index, post, tag, etc.)
- `templates/partials/` - Reusable template components (header, footer, cards)
- `assets/css/` - CSS files including comprehensive design system variables
- `assets/js/` - JavaScript entry point
- `dist/` - Build output directory (copied templates + bundled assets)

### Design System
The theme uses a comprehensive CSS custom property system in `assets/css/vars.css` with:
- Brand colors (primary, secondary, accent)
- Semantic colors (success, warning, error)
- Design tokens for text, backgrounds, borders, and interactive states
- Arcstratus-specific color variants

### Build Process
1. Rollup processes JS/CSS from `assets/` into `dist/assets/built/`
2. Templates are copied to `dist/` root
3. `ghost-package.json` becomes `package.json` in dist
4. Final zip contains everything needed for Ghost deployment

### Ghost Integration
- Uses Ghost Admin API for automated deployment
- Follows Ghost theme structure with required templates
- Includes Motion.js for animations
- Theme validation via gscan

### Key Files
- `rollup.config.js` - Build configuration with PostCSS, Tailwind, and live reload
- `upload.js` - Ghost Admin API deployment script (requires env.js configuration)
- `routes.yaml` - Ghost routing configuration
- `templates/default.hbs` - Base template layout