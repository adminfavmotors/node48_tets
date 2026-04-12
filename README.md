# NODE48

Bilingual marketing website for `NODE48`, built with `React`, `Vite`, `TypeScript`, and `Tailwind CSS`.

This repository is the isolated test mirror for client-safe UI and UX work. Day-to-day changes land on `test`, get reviewed on Vercel preview deployments, and are only ported to the main client repository after approval.

## Product Scope

The site currently covers:

- homepage with section-based navigation
- dedicated SEO-oriented service pages under `/uslugi/*`
- isolated portfolio carousel with live case links
- reusable contact overlay for internal-page CTAs
- privacy policy and cookie policy pages

Default locale is Polish (`pl`) with an English switcher (`en`) in the navbar.

## Current State

Implemented and active:

- responsive desktop, mobile, and ultrawide layout system
- rebuilt homepage visual layer with stronger hero, trust strip, simplified CTA card section, and section backgrounds
- unified structural motion system for shell, hero, cards, overlays, and portfolio interactions
- unified light-behavior system with shared cool ambient, warm accent, and interactive highlight tokens
- route-level lazy loading for service and legal pages
- deferred portfolio showcase mount so carousel code loads near viewport
- dedicated SEO-oriented service pages with canonical URLs, redirects, and JSON-LD
- reusable internal-page contact overlay and smart mobile navigation
- global scroll-to-top button
- isolated portfolio carousel backed by structured project data and real preview images
- surface-card system for editorial, showcase, deep, and summary content blocks
- manual SEOHOST deployment and rollback workflow kept only as an exception path

## Documentation

Recent internal documentation:

- [Production Deployments](C:\Users\Admin\Desktop\project\node48_tets\docs\production-deployments.md)
- [AI Dev Prompt](C:\Users\Admin\Desktop\project\node48_tets\docs\ai-dev-prompt.md)

## Stack

- `React 18`
- `Vite 5`
- `TypeScript`
- `Tailwind CSS`
- `Vitest` + `Testing Library`
- `ESLint 9`

## Getting Started

### Requirements

- `Node.js 18+`
- `npm`

### Install

```bash
npm install
```

### Run locally

```bash
npm run dev
```

The app runs on the Vite development server configured in [vite.config.ts](C:\Users\Admin\Desktop\project\node48_tets\vite.config.ts).

## Available Scripts

```bash
npm run dev
npm run build
npm run preview
npm run check:text
npm run lint
npm run test
```

## Project Structure

```text
src/
  components/              Homepage sections and shared UI blocks
  components/contact/      Contact overlay and related form logic
  components/legal/        Legal-page components
  components/portfolio/    Dedicated portfolio carousel module
  components/primitives/   Shared low-level UI and surface/action primitives
  lib/                     i18n, SEO, service data, project data, site config
  lib/service-page-details Service-page content definitions
  pages/                   Route-level pages
  styles/                  Split visual layers for home, shell, service pages, and responsive rules
  test/                    Vitest setup and app-level tests
public/
  .htaccess                Cache rules and redirects
  project-previews/        Static preview images for portfolio cases
  sitemap.xml              Public sitemap
docs/
  *.md                     Internal project reports
```

## Key Config Files

- shared business/config values: [src/lib/contact-config.ts](C:\Users\Admin\Desktop\project\node48_tets\src\lib\contact-config.ts)
- service catalog and slugs: [src/lib/service-pages.ts](C:\Users\Admin\Desktop\project\node48_tets\src\lib\service-pages.ts)
- service page details: [src/lib/service-page-details](C:\Users\Admin\Desktop\project\node48_tets\src\lib\service-page-details)
- project portfolio data: [src/lib/project-cases.ts](C:\Users\Admin\Desktop\project\node48_tets\src\lib\project-cases.ts)
- portfolio carousel module: [src/components/portfolio](C:\Users\Admin\Desktop\project\node48_tets\src\components\portfolio)
- SEO/meta handling: [src/lib/seo.ts](C:\Users\Admin\Desktop\project\node48_tets\src\lib\seo.ts)
- Vercel Git deployment rules: [vercel.json](C:\Users\Admin\Desktop\project\node48_tets\vercel.json)

## Localization

- translations are stored in [src/lib/i18n-data.ts](C:\Users\Admin\Desktop\project\node48_tets\src\lib\i18n-data.ts)
- Polish is the default locale
- selected locale is persisted in `localStorage`
- `html[lang]`, `document.title`, and page metadata update with locale changes

## SEO Notes

- service pages use route-level metadata updates
- canonical URLs are managed in the client SEO layer
- structured data is generated for service pages
- sitemap and legacy service redirects are maintained in `public/`

## Test Preview Workflow

- this repository is the safe test mirror and should be developed on the `test` branch
- Vercel preview deployments are intended to follow `test`
- `vercel.json` disables automatic Vercel Git deployments for every branch except `test`
- the stable test domain is `https://node48tets.vercel.app`
- the URL `https://node48tets-e6se74o4n-adminfavmotors-projects.vercel.app` is a commit-specific deployment URL, not the stable branch URL
- when Vercel Git integration is connected correctly, the branch preview URL for `test` should always point at the latest `test` commit
- only after approval should changes be ported to the main client repository

## SEOHOST Deploy Safety

- automatic SEOHOST deploys are disabled in this test mirror
- the SEOHOST workflow is manual-only and should be treated as an exception path
- deployment and rollback notes for this mirror are documented in [docs/production-deployments.md](C:\Users\Admin\Desktop\project\node48_tets\docs\production-deployments.md)

## Contact Form

- the homepage includes a shared contact section
- internal pages use a reusable modal contact overlay
- form submission currently uses `FormSubmit`
- recipient configuration lives in [src/lib/contact-config.ts](C:\Users\Admin\Desktop\project\node48_tets\src\lib\contact-config.ts)

## Quality Checks

Current main checks:

- `npm run check:text`
- `npm run lint`
- `npm run build`
- `npm run test`
- manual mobile/desktop UI verification after visual passes

## Known Constraints

- service pages still run in an SPA without SSR or prerendering
- form delivery still depends on a third-party endpoint
- portfolio previews are static assets and should be refreshed when the live case sites change significantly
- the visual system is now cleaner, but hero polish, typography tuning, and further performance work still have headroom
- content is now much more mature than the initial template, but the project can still benefit from a CMS or analytics layer later
