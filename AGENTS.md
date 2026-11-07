# AGENTS.md

Maintainer notes for Awesome-Agent-Services. The site is a [yaal](yaal/) contents/ instance, same pattern as [Awesome-Personal-Agents](https://github.com/0xWelt/Awesome-Personal-Agents) and [Awesome-Vibe-Coding](https://github.com/0xWelt/Awesome-Vibe-Coding).

## Positioning

This list is the complete collection of supporting tools and supporting services an agent can call. That includes fulfillment services (mail, calendar, files, payments, scheduling, support, sales, and the rest) and the infrastructure and code-hosting platforms an agent operates: AWS, Azure, Google Cloud, Vercel, Railway, Render, Netlify, Cloudflare, Docker, GitHub, GitLab, Kubernetes tooling, and their official CLIs.

It also includes code-related supporting tools that are not those platforms: observability, context and quality tools, skill directories, and MCP servers or skills that are products in their own right.

Entries are the tool or service itself. One product, one entry. Do not classify the list by connection type. `tags` record verified connection methods (`mcp`, `skill`, `grok-bot`, `cli`, `chatgpt`). A Grok Bot catalog connector is not `mcp`.

[Awesome-Vibe-Coding](https://github.com/0xWelt/Awesome-Vibe-Coding) keeps coding harnesses and Lovable-like vibe-coding builders: Bolt.new, Replit, Lovable, Open Lovable, Firebase Studio, Cursor, Claude Code, and similar apps that run the agent. Do not list those harnesses here. Infrastructure and code hosts that an agent operates belong here, not in AVC.

[Awesome-Personal-Agents](https://github.com/0xWelt/Awesome-Personal-Agents) keeps named personal-agent products. Do not list Grok Bot, Dots, Claude Duet, Muse, Manus, OpenClaw, or Hermes Agent here.

## Inclusion rule

Include a product when an agent can call it to read or change something outside the chat: a message sent, a meeting booked, a file updated, a payment made, a ticket moved, a campaign launched, a record written, a hosted system operated, or a supporting tool used while that work happens.

Do not include:

- A second entry for a protocol wrapper, CLI, or skill pack that only reaches a product already listed. Link the product and tag the connection.
- A coding harness or Lovable-like app builder. Bolt.new, Replit, Lovable, Open Lovable, Firebase Studio, Cursor, and Claude Code stay in Awesome-Vibe-Coding.
- A named personal agent. Grok Bot, Dots, Claude Duet, Muse, Manus, OpenClaw, and Hermes Agent stay in Awesome-Personal-Agents.
- Cursor or Grok Bot internals (canvases, plugin scaffolding, team kits, the Cursor SDK, and the Grok Bot Tailscale networking helper).

One entry per product. If two catalog plugins are the same product, keep the official or vendor one. Regional brands with their own public sites (Lark and Feishu) can both have entries.

## contents/ conventions

- One markdown file per service under `contents/<category>/` or `contents/<category>/<subcategory>/`.
- Every folder has `_meta.md` with YAML `title:` and a short English description in the body.
- Add a subcategory only when a coherent cluster already exists in that category. Do not add empty placeholder folders. Small coherent categories stay flat.
- Service frontmatter is `name` and `link`. Do not add a `command` field.
- `tags` record verified connection methods on the service. They do not decide which folder a service is in. Vocabulary:
  - `mcp` — official or vendor-hosted Model Context Protocol server.
  - `skill` — Agent Skill (`SKILL.md` or packaged skills the vendor ships).
  - `grok-bot` — listed in the Grok Bot Connect Apps catalog (connector and/or skills there). The seed snapshot is 2026-11-07.
  - `cli` — official command-line interface intended for humans and agents.
  - `chatgpt` — official ChatGPT app or Actions published by the vendor.
- Only add a tag you have verified. A Grok Bot catalog connector is not `mcp`. Do not invent connection methods. Another protocol (for example `a2a`) may be a tag only when a listed service actually offers that surface.
- `link` is the official public product homepage or docs hub. Never use an MCP install URL, a skill gist, or `https://cursor.com/grok-bot/link/v1/plugin/add?id=...`. Strip UTM, referral, and affiliate parameters.
- English throughout. Keep entries factual. Do not invent features, plan limits, or URLs. You may mention verified connection methods in one short factual sentence. The tags are the structured record.
- If a product could sit in two categories, pick one primary home and mention the other surface in the body.
- Entries are services. Do not classify the list by connection type, and do not create a category or subcategory named MCP, Skill, Grok Bot, CLI, ChatGPT, Featured, or Canvas.
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
