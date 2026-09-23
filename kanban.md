# Crystal Belin Website — Kanban Board

## Backlog

### Visual polish pass (amber accent consistency, typography hierarchy)
- [ ] Audit homepage hero: confirm `--accent: #a0522d` used on `.hero-title-italic`, `.label-accent`, primary buttons, mock swatch row — all five touchpoints match
- [ ] Audit homepage features grid: check each feature-icon background color is intentional and within the warm palette (colors, type, space, motion, shadow, version icons)
- [ ] Audit homepage export section: verify code-block background (`var(--text-primary)`) renders correctly against site surface and copy buttons have sufficient contrast
- [ ] Audit homepage audience section: confirm `audience-number` color (`var(--border)`) is legible at 2.5rem size and section-alt background doesn't shift heading contrast
- [ ] Audit homepage CTA section: verify inverted dark section (`--text-primary` bg) uses correct light text values and accent-light for the label
- [ ] Audit about page: confirm `.about-philosophy li::before` em-dash uses `--accent`, contact card borders use `--border`, hover states use `--accent-bg`
- [ ] Audit tools page: confirm all five tool cards use consistent card styling and the tool-specific headings use correct product names
- [ ] Audit software page: check the demo iframe area, export format cards, and any component previews for accent consistency
- [ ] Audit docs page: check table styles, code blocks, and any inline documentation elements for consistent spacing and typography
- [ ] Verify typography hierarchy across all 5 pages: h1→h2→h3 sizing steps are consistent, body copy line-height (1.7) maintained, no inline style overrides that break the scale
- [ ] Check responsive breakpoints: homepage grid collapses correctly at 900px and 600px; about page grid shifts to single column at 768px; nav hides links at 768px (known gap — see mobile nav item)
- [ ] Verify scrollbar, selection color, and focus-visible ring are consistent across all pages

### Favicon update to match DesignTerra branding
- [ ] Audit current favicon.svg: it's a generic black abstract shape with no DesignTerra association
- [ ] Design a new SVG favicon: clean geometric mark in deep bronze (`#a0522d`), optionally incorporating a "D" letterform or token-swatch motif, sized 128×128 viewBox
- [ ] Add a light-mode/dark-mode color swap via `@media (prefers-color-scheme: dark)` so the mark is visible on both
- [ ] Replace `/public/favicon.svg` with the new design
- [ ] Regenerate or replace `/public/favicon.ico` (32×32 and 16×16) to match, or confirm the existing .ico still works with the new SVG
- [ ] Verify the favicon renders correctly in Chrome, Firefox, Safari, and on mobile home-screen bookmark

### Write comprehensive README for the repo
- [ ] Replace the Astro starter default README entirely
- [ ] Add a project header: "DesignTerra — Design Token Workspace" with one-sentence description
- [ ] Add a "Five Products" section listing all brand names and their roles: DesignTerra (main workspace), ChromaBloom (palette tool), GlyphSmith (type-pair tool), TokenMeld (token convert tool), ShadeFold (shadow stack tool)
- [ ] Add a "Live Site" section with the crystalbelin.com URL
- [ ] Add a "Development" section: `npm install`, `npm run dev`, `npm run build`, `npm run preview`
- [ ] Add a "Project Structure" section noting pages (index, software, tools, docs, about), components (Nav, Footer), layout (BaseLayout), and the public/tools/ and public/designterra/ directories
- [ ] Add a "Deployment" section: Vercel + GitHub auto-deploy, custom domain, vercel.json download endpoint for /designterra
- [ ] Add a "Design System" section pointing to src/styles/global.css and summarizing the token palette (warm ivory bg, deep bronze accent, Instrument Serif + Inter + JetBrains Mono)
- [ ] Add an "About the Author" section: Crystal Belin, Eastover SC, contact phone
- [ ] Add a license section (check what license applies; if unclear, note it)

### Set up custom 404 page
- [ ] Create `src/pages/404.astro` using BaseLayout, Nav, and Footer
- [ ] Match the site's visual language: warm ivory background, bronze accent, Instrument Serif headings
- [ ] Include a friendly "page not found" heading and a short explanation
- [ ] Include a "Go home" primary button linking to `/`
- [ ] Include secondary links to `/software` (Live Demo) and `/tools` (Tools) so visitors have somewhere useful to go
- [ ] Test by visiting a non-existent route locally (`npm run dev` then `/this-does-not-exist`)
- [ ] Confirm Vercel serves the custom 404 (Astro's 404.astro is automatically used in production builds)

### SEO: add sitemap and robots.txt
- [ ] Create `src/pages/sitemap.xml.astro` that emits a valid sitemap XML covering `/`, `/software`, `/tools`, `/docs`, `/about`
- [ ] Set the sitemap URL to `https://crystalbelin.com` as the base
- [ ] Create `src/pages/robots.txt.astro` with `Sitemap: https://crystalbelin.com/sitemap.xml` and a permissive policy (the site is public)
- [ ] Verify both files are served at the correct paths in production (`/sitemap.xml`, `/robots.txt`)
- [ ] Submit the sitemap to Google Search Console (if an account is available) — note as manual follow-up if not

### Mobile navigation: implement a working mobile nav
- [ ] Audit current behavior: nav-links are `display: none` below 768px with no replacement — the mobile user sees only the logo + CTA, no way to reach Tools, Docs, About
- [ ] Implement a hamburger menu (or equivalent) for the mobile nav: a button that toggles a dropdown/panel listing all nav links
- [ ] Ensure the mobile menu is keyboard-accessible (Enter/Space to open, Escape to close, focus management)
- [ ] Ensure the mobile menu works with the sticky nav backdrop and doesn't overflow the viewport on short screens
- [ ] Test on a real narrow viewport (or browser devtools device mode at 375px) for all 5 pages

### Open Graph images: add og:image meta tags
- [ ] Audit current BaseLayout: has og:title and og:description but no og:image — social shares will render without a preview card image
- [ ] Create a default OG image (`public/og-default.png` or `.jpg`) at 1200×630, using the site palette and "DesignTerra" branding
- [ ] Add `<meta property="og:image" content="/og-default.png">` to BaseLayout as a default
- [ ] Consider per-page OG images for the homepage (hero composition) and software page (demo screenshot) — optional, can be deferred
- [ ] Add `twitter:card: summary_large_image` meta tag alongside the og:image
- [ ] Test by sharing the URL in a social preview tool or debugger (e.g. Facebook Sharing Debugger, Twitter Card Validator) and confirm the image appears

### Name audit: verify no stale product names remain after rename
- [ ] Grep the entire `src/` and `public/` directories for old names: "Basis", "Palette", "Type Pair", "Token Convert", "Shadow Forge" (case-insensitive)
- [ ] Audit Nav.astro: confirm all five product names appear correctly (product links + "Try DesignTerra" CTA)
- [ ] Audit Footer.astro: confirm product, tools, and company columns use current names
- [ ] Audit index.astro: confirm hero mock-nav shows "DesignTerra", all feature cards and export format references are current, "basis.workspace" mock URL is intentional (or update to designterra.workspace)
- [ ] Audit about.astro: confirm the subtitle doesn't say "team of South Carolina software engineers" if that was the earlier issue, confirm "DesignLoom" references (if any) are intentional or updated to DesignTerra
- [ ] Audit software.astro, tools.astro, docs.astro: grep each for stale names and fix
- [ ] Check the public tool HTML files (designterra/index.html, tools/palette/index.html, etc.) for any embedded old names in titles, headers, or UI labels

---

## In Progress
- [x] Debug live preview iframe on /software — CSS variable leakage + scroll bug identified and fixed
- [x] Name collision audit for all 5 product names — HueForge and ShadeCraft collided; renamed to ChromaBloom and ShadeFold
- [x] Rename implementation: patch all Astro pages, components, tool HTML files, vercel.json; rebuild + deploy
- [x] Eliminate all stale Basis/DesignLoom/Chromis/Glyphic/Forma/Umbra refs across src and public

## Done
- [x] Deploy site to Vercel with custom domain crystalbelin.com
- [x] Disable Vercel auth wall
- [x] Set up GitHub repo + auto-deploy
- [x] Add Crystal Belin contact details (footer + about page)
- [x] Rename all products: Basis→DesignTerra, Palette→ChromaBloom, Type Pair→GlyphSmith, Token Convert→TokenMeld, Shadow Forge→ShadeFold
- [x] Fix download button to actually download designterra.html
- [x] Fix about page text ("team of South Carolina software engineers...")
- [x] Create vercel.json for download endpoint
- [x] Verify custom domain SSL for both bare and www
