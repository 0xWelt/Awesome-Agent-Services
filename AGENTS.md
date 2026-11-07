# AGENTS.md

Maintainer notes for Awesome-Agent-Services. The site is a [yaal](yaal/) contents/ instance, same pattern as [Awesome-Personal-Agents](https://github.com/0xWelt/Awesome-Personal-Agents) and [Awesome-Vibe-Coding](https://github.com/0xWelt/Awesome-Vibe-Coding).

## Positioning

This list collects services an AI agent can call to get something done in the real world or in a person's accounts: mail, calendar, files, payments, scheduling, support, sales, and similar fulfillment and transaction surfaces.

It is not another MCP-server directory and not a dump of adapters, skills, or protocol wrappers.

[Awesome-Vibe-Coding](https://github.com/0xWelt/Awesome-Vibe-Coding) keeps coding harnesses and coding-oriented MCP servers and tools. Do not copy AVC entries here.

[Awesome-Personal-Agents](https://github.com/0xWelt/Awesome-Personal-Agents) keeps named personal-agent products. Do not list Grok Bot, Dots, Claude Duet, Muse, Manus, OpenClaw, or Hermes Agent here.

## Inclusion rule

Include a product when an agent can call it to read or change something outside the chat: a message sent, a meeting booked, a file updated, a payment made, a ticket moved, a campaign launched, a record written, or a hosted system operated.

Do not include:

- The MCP server, skill pack, CLI, or protocol wrapper that merely reaches a product. Link the product.
- A coding harness, coding IDE, or coding-oriented tool. Those stay in Awesome-Vibe-Coding. Replit, Lovable, and Vibecode are examples already listed there.
- A named personal agent. Grok Bot, Dots, Claude Duet, Muse, Manus, OpenClaw, and Hermes Agent stay in Awesome-Personal-Agents.
- Cursor or Grok Bot internals (canvases, plugin scaffolding, team kits, the Cursor SDK, and the Grok Bot Tailscale networking helper).

One entry per product. If two catalog plugins are the same product, keep the official or vendor one. Regional brands with their own public sites (Lark and Feishu) can both have entries.

## contents/ conventions

- One markdown file per service under `contents/<category>/`.
- Every folder has `_meta.md` with YAML `title:` and a short English description in the body.
- Service frontmatter is `name` and `link`. Optional `tags` are short labels. The seed uses `grok-bot` for items from the Grok Bot Connect Apps catalog (snapshot 2026-11-07). Do not add a `command` field.
- `link` is the official public product homepage or docs hub. Never use `https://cursor.com/grok-bot/link/v1/plugin/add?id=...`. Strip UTM, referral, and affiliate parameters.
- English throughout. Keep entries factual. Do not invent features, plan limits, or URLs.
- If a product could sit in two categories, pick one primary home and mention the other surface in the body.
- Do not create top-level sections named MCP, Featured, or Canvas.
- Do not add this repo as a submodule of the Awesome meta repo, and do not edit yaal's own README, from a contents PR. The maintainer will do that later.

Services that were in the Connect Apps catalog but had no verified official homepage are listed in `SEED-GAPS.md`, with the catalog name and the reason.

## Commits

Use [Conventional Commits](https://www.conventionalcommits.org/): `type(scope): description`. A Chinese description is fine; English is fine.

## Toolchain

This repo consumes the `yaal` submodule (Vite+). From `yaal/`:

- `vp install` — install dependencies
- `vp run dev` — development server
- `vp run build` — production build (`yaal/out`)
- `vp run parse-readme` — regenerate site data from `contents/`
- `vp check` — format, lint, and type-check

## GitHub Pages

The homepage is [https://0xWelt.github.io/Awesome-Agent-Services/](https://0xWelt.github.io/Awesome-Agent-Services/).

GitHub Pages for this repo is enabled with **Build and deployment → Source: GitHub Actions** (`build_type=workflow`), same as Awesome-Vibe-Coding. `.github/workflows/smart-deploy.yml` builds the yaal site and deploys it when `README.md`, `contents/`, `yaal.config.yaml`, the `yaal` submodule, or the workflows change on `main`. Renovate updates the nested `yaal` submodule (`renovate.json`).

If Pages is ever unset, an admin turns it back on in **Settings → Pages → Build and deployment → Source: GitHub Actions**. The workflow does not need a `gh-pages` branch. A missing `pages: write` permission on the workflow, or Pages left on "Deploy from a branch", is what blocks the deploy. Fix the source setting; do not fail a contents PR for it.
