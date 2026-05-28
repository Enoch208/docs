# Meridian docs — Mintlify

The Meridian docs site is built with [Mintlify](https://mintlify.com): MDX
pages + a `docs.json` config + auto-generated API reference pulled from the
FastAPI backend's `/openapi.json`.

## Local preview

```bash
npm i -g mintlify
cd docs
mintlify dev
```

Opens at `http://localhost:3000` with hot reload.

## Deploy to Mintlify (free)

1. Sign in at [mintlify.com](https://mintlify.com) with GitHub.
2. **Install the Mintlify GitHub app** on the `Meridian` repo.
3. In the Mintlify dashboard, **set the docs folder path** to `docs/`.
4. Every push to `main` redeploys automatically.

Mintlify will give you a subdomain like `meridian.mintlify.app`. You can map a
custom domain (e.g. `docs.meridiansw.com`) under **Settings → Custom Domain**.

Once it's live, swap the `LINKS` entry in
[`frontend/lib/links.ts`](../frontend/lib/links.ts) and the navbar **Docs**
link will point at it.

## Structure

```
docs/
├── docs.json              ← Mintlify config (theme, nav, openapi)
├── logo.png               ← shown in the docs navbar
├── README.md              ← this file
├── introduction.mdx       ← "Welcome to Meridian"
├── quickstart.mdx
├── how-it-works.mdx
├── the-scouts.mdx
├── scoring-rubric.mdx
├── evaluate.mdx
├── telegram-bot.mdx
├── track-record.mdx
└── tokenomics.mdx
```

The `launch/` and `superpowers/` subfolders are **internal** docs (the
listing kit and the project specs) — Mintlify only renders pages listed in
`docs.json`'s navigation, so they don't appear on the public docs site.

## API Reference

The **API Reference** tab is generated automatically from
`https://meridian-backend-qae0.onrender.com/openapi.json` — your FastAPI
backend serves that for free. New endpoints show up in the docs the moment
the backend redeploys; no MDX writing needed.

## Adding a new page

1. Drop a new `.mdx` file in `docs/`.
2. Add its slug (filename without `.mdx`) to the right group's `pages` array
   in [`docs.json`](./docs.json).
3. Commit + push. Mintlify rebuilds in seconds.

## Style

- Voice: confident, plain, presenter-tone. No marketing fluff, no triads.
- Honesty rules are the rubric — never claim what you can't verify. Say
  Unknown when it's Unknown.
- Always include the disclaimer where relevant: *worth investigating, never
  financial advice.*
