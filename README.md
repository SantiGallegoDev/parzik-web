# Parzik — Corporate Website

## Description

Corporate website for **Parzik**, a digital agency specializing in web development, software solutions, and branding. The site showcases the agency's services, project portfolio, team, and includes an interactive quote builder for prospective clients.

## Tech Stack

- **Framework:** [Astro](https://astro.build/) v5
- **Language:** TypeScript / JavaScript
- **3D Graphics:** Three.js (interactive globe on the projects page)
- **Styling:** Scoped CSS with custom design tokens
- **Hosting:** Vercel (recommended)

## Installation

```bash
npm install
```

## Development

Start the local development server:

```bash
npm run dev
```

The site will be available at `http://localhost:4321`.

## Build

Generate the production build:

```bash
npm run build
```

Preview the production build locally:

```bash
npm run preview
```

The compiled output is written to the `dist/` directory.

## Project Structure

```
/
├── public/                 # Static assets (images, favicons)
│   ├── projects/           # Portfolio project screenshots
│   ├── shop/               # E-commerce demo assets
│   └── team/               # Team member photos
├── src/
│   ├── components/         # Reusable UI components
│   │   ├── Navbar.astro
│   │   ├── Hero.astro
│   │   ├── Services.astro
│   │   ├── ClientCarousel.astro
│   │   ├── Globe.astro
│   │   ├── ScrollAnimations.astro
│   │   └── Footer.astro
│   ├── data/               # Static data files
│   │   └── cotizador-config.json
│   ├── layouts/            # Page layouts
│   │   └── Layout.astro
│   └── pages/              # Route pages
│       ├── index.astro
│       ├── servicios.astro
│       ├── nosotros.astro
│       ├── proyectos.astro
│       └── cotizador.astro
├── astro.config.mjs        # Astro configuration
├── tsconfig.json            # TypeScript configuration
└── package.json
```

## Pages

| Route          | Description                                      |
| :------------- | :----------------------------------------------- |
| `/`            | Home page with hero, services, plans, and CTA    |
| `/servicios`   | Detailed breakdown of all service offerings      |
| `/nosotros`    | About page with team, mission, and history        |
| `/proyectos`   | Portfolio with filterable project grid and 3D globe |
| `/cotizador`   | Interactive step-by-step quote builder            |

## Environment Variables

This project does not require environment variables for basic operation. If you need to configure API keys or third-party services, create a `.env` file in the project root:

```
PUBLIC_SITE_URL=https://www.parzik.com
```

Astro exposes variables prefixed with `PUBLIC_` to client-side code. See the [Astro environment variables docs](https://docs.astro.build/en/guides/environment-variables/) for details.

## Deployment

### Vercel (Recommended)

1. **Connect the repository** — Import the Git repository from the Vercel dashboard.
2. **Framework preset** — Vercel auto-detects Astro. No manual configuration needed.
3. **Build settings:**
   - Build command: `npm run build`
   - Output directory: `dist`
4. **Environment variables** — Add any required variables in the Vercel project settings under *Settings > Environment Variables*.
5. **Domain** — Configure the custom domain under *Settings > Domains* and update DNS records as instructed.

Each push to `main` triggers an automatic production deployment.

## Maintenance

### Adding a new page

Create a new `.astro` file inside `src/pages/`. Astro uses file-based routing, so `src/pages/contact.astro` becomes `/contact`.

### Adding a new component

Place reusable components in `src/components/` and import them into any page or layout.

### Updating the quote builder

Edit `src/data/cotizador-config.json` to add, remove, or modify pricing steps. The quoter page reads this file at build time and renders steps dynamically.

### Updating the portfolio

Add new project screenshots to `public/projects/` and update the `projects` array in `src/pages/proyectos.astro`.

### Styling

All styles are scoped to their respective components using Astro's `<style>` blocks. Global design tokens (colors, fonts, spacing) are defined in `src/layouts/Layout.astro` under `:root`.

## Notes

- The 3D globe on the projects page uses Three.js and renders country borders from TopoJSON data loaded via CDN. It is automatically hidden on low-powered devices.
- Scroll animations are handled by a lightweight Intersection Observer implementation — no external animation library is required.
- The client carousel uses CSS-only infinite scrolling with a JS-enhanced 3D tilt effect on hover.
- All pages are statically generated at build time for optimal performance and SEO.
