# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

IKAI is a static landing page for an AI-powered proposal automation platform targeting strategy and management consulting firms. The site is built with vanilla HTML, CSS, and JavaScript—no build system or framework required.

## Architecture

### File Structure
- `index_with_trusted_logos.html` — Primary landing page with full feature set including logo carousel
- `index.html` — Alternative version of the landing page
- `styles/root.css` — CSS variables, base styles, and core component definitions
- `styles/main.css` — Page-specific styles, sections, responsive layouts, and animations
- `assets/` — Images, logos, SVGs, and badge icons
  - `assets/logos/` — Client/partner company logos for "Trusted by" section
  - `assets/badges/` — Compliance badge images (ISO, SOC2, GDPR)

### Design System

The site uses a custom design system defined in `styles/root.css`:
- **Color palette**: Purple-based gradient system (`--purple-950` through `--purple-400`) with gray scales
- **Shadows**: `--shadow-soft` and `--shadow-card` for depth
- **Radius**: `--radius-xl` (22px) and `--radius-lg` (14px)
- **Typography**: System font stack with smooth anti-aliasing

### Key Components

**Hero Section** (`index_with_trusted_logos.html:22-87`)
- Gradient background with radial overlay
- Two-column grid layout (text + 3D asset image)
- Feature chips and dual CTA buttons

**Logo Carousel** (`index_with_trusted_logos.html:274-385`)
- Seamless infinite scroll animation
- Dynamically calculates animation duration based on content width
- Touch-friendly pause on mobile
- Respects `prefers-reduced-motion`
- Uses JavaScript (`index_with_trusted_logos.html:734-830`) to measure logo widths and generate dynamic CSS keyframes

**Security & Compliance Section** (`index_with_trusted_logos.html:468-529`)
- Flexbox layout with badge icons and confidentiality details
- Compliance badges: ISO 27001, SOC 2 Type II, GDPR

**Contact Form** (`index_with_trusted_logos.html:531-646`)
- JavaScript-powered mailto: link generation
- No backend—uses default email client

## Development Workflow

### Viewing Changes
Open `index_with_trusted_logos.html` directly in a browser. No build step required.

### Making Updates
1. Edit HTML directly in `index_with_trusted_logos.html`
2. Adjust global styles in `styles/root.css` (colors, spacing, shadows)
3. Modify section-specific styles in `styles/main.css`
4. Refresh browser to see changes

### Adding Logos
1. Add logo image to `assets/logos/`
2. Insert two `<div class="logo-item">` blocks in the carousel markup (lines 293-380)—one in Set A, one in Set B (the duplicate set ensures seamless looping)
3. Use PNG format with transparent backgrounds
4. Logos are converted to black using `filter: grayscale(1) brightness(0)` in CSS

### Responsive Behavior
- **Desktop**: Multi-column grids for pillars, steps, KPIs
- **Tablet** (<1020px): Grids collapse to 2 columns or stack
- **Mobile** (<640px): Single column, full-width CTAs, adjusted padding

## Current Development Status

Based on README.md, the following are in progress:
- **Logos section**: Stakeholder alignment on which logos to include, size adjustments
- **Security & Confidentiality**: Review compliance categories (ISO, SOC 2, GDPR), vertical icon alignment, specialist content review

## Accessibility Features
- Semantic HTML with ARIA labels
- Keyboard focus styles (`:focus-visible` with purple outline)
- Scroll margin for anchor navigation
- Reduced motion support for animations

## Browser Compatibility
- Modern browsers (Chrome, Firefox, Safari, Edge)
- Uses CSS Grid, Flexbox, CSS custom properties
- Intersection Observer API for reveal animations
