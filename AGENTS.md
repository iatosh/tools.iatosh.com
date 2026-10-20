# AGENTS.md

Tool index page for https://tools.iatosh.com/. Static files only, no build step.

## Layout

- `public/index.html`: tool list. UI text Japanese. App-launcher style: centered grid of icon cards (like 123apps / pdf24). Not tied to iatosh.com portfolio design.
- `public/icons/<tool>.svg`: card icon, copy of each tool's favicon. `public/favicon.svg`: hub icon (2×2 grid).
- `public/robots.txt`, `public/sitemap.xml`: SEO for whole host. Each tool page URL goes in `sitemap.xml`.
- `public/llms.txt`: site summary for LLMs (llms.txt proposal). One line per tool.
- `public/404.html`: served for unknown paths (`not_found_handling: 404-page`).
- `wrangler.jsonc`: Worker `tools-iatosh-com`, Custom Domain `tools.iatosh.com` (creates DNS).

## How tools attach

- Each tool lives in own repo, own Worker, route `tools.iatosh.com/<tool>*` (zone `iatosh.com`). Routes beat this Custom Domain on same host.
- Tool assets must sit under `<tool>/` in its asset directory (Workers static assets match full request path).
- Add new tool: card in `index.html` + icon in `public/icons/`, URL in `sitemap.xml`, line in `llms.txt`, line in `README.md`.

## Deploy

- Cloudflare Workers Builds, connected in dashboard. Push to `main` deploys. No build command, deploy command `npx wrangler deploy`.
- Free plan: static assets only, no Worker script. Keep it that way so requests stay free and unlimited.

## Conventions

- Commit messages English. No trailer (no Co-Authored-By etc).
- One commit per logical chunk.
