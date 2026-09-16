# GoSolarQuotes — Astro vs. WordPress Demo

This is a proof-of-concept rebuild of the **[GoSolarQuotes](https://www.gosolarquotes.com.au/)** homepage in [Astro](https://astro.build). Only the home page has been recreated — the goal is to give the client a side-by-side feel for how the same page performs and behaves when built with Astro instead of WordPress, not to reproduce the full site.

## Why this exists

WordPress renders pages on request (or via a caching layer bolted on top) and ships a fair amount of framework/plugin overhead to the browser. Astro renders this page to static HTML at build time, so there's:

- No PHP/MySQL request-time rendering
- No plugin bloat — only the markup and CSS this page actually needs ships to the browser
- Fast, predictable load times out of the box, with the option to add interactivity only where it's needed

This repo demonstrates that with a real page from the client's own site, rather than a generic template.

## Project structure

```text
/
├── public/                  # Static files served as-is
├── src/
│   ├── assets/               # Images, optimized by Astro at build time
│   ├── components/
│   │   ├── Header.astro
│   │   ├── Footer.astro
│   │   └── home/              # Sections that make up the home page
│   │       ├── Hero.astro
│   │       ├── HowItWorks.astro
│   │       ├── PlanCostsSavings.astro
│   │       ├── PowerStorageBatteries.astro
│   │       ├── FreeSolarCalculators.astro
│   │       └── SolarSystemSizeCalculator.astro
│   ├── layouts/
│   │   └── Layout.astro       # Shared page shell (head, header, footer)
│   ├── styles/
│   │   └── global.css
│   └── pages/
│       └── index.astro        # The home page — the only route in this demo
└── package.json
```

## Commands

This project uses [pnpm](https://pnpm.io). All commands are run from the root of the project:

| Command                | Action                                           |
| :---------------------- | :----------------------------------------------- |
| `pnpm install`           | Install dependencies                             |
| `pnpm dev`               | Start the local dev server at `localhost:4321`   |
| `pnpm build`             | Build the production site to `./dist/`           |
| `pnpm preview`           | Preview the production build locally             |
| `pnpm astro ...`         | Run Astro CLI commands (e.g. `astro check`)       |

When working with an AI coding agent in this repo, start the dev server in the background: `astro dev --background` (manage it with `astro dev stop`, `astro dev status`, `astro dev logs`) — see `AGENTS.md`.

## Scope

This is a demo, not a migration in progress:

- Only the home page is built — no blog, guides, or inner pages
- Content and copy are taken directly from the live WordPress site for an accurate comparison
- Not intended for production deployment as-is

## Learn more

- [Astro documentation](https://docs.astro.build)
