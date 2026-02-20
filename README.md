# New Iberia Church of Christ

Website and staff dashboard for New Iberia Church of Christ. Live at **https://newiberiachurchofchrist.com**.

## Stack

- **Runtime:** Cloudflare Worker (single `worker.js`)
- **Data:** D1 (SQLite), R2 (static HTML/CSS/JS), KV (cache)
- **Images:** Cloudflare Images (Direct Creator Upload)
- **Email:** Resend (all sends logged in dashboard Mail tab)
- **Stream:** Cloudflare Stream (ingest + playback)

No local server; 100% Cloudflare in production.

## Staff dashboard

- **Login:** `/login` → **Dashboard:** `/dashboard` (Overview, CMS, Requests, Mail, Media, Stream, Settings)
- **Media:** Upload/delete images; assign to pages. `/dashboard/images` redirects to `/dashboard/media`.

## Deploy

From the project root (where `worker.js` and `scripts/deploy.sh` live):

```bash
./scripts/deploy.sh
```

Requires Wrangler and Cloudflare secrets set (e.g. `RESEND_API_KEY`, `CLOUDFLARE_IMAGES_API_TOKEN`). No secrets in repo.

## For agents / future work

- Full spec, API list, migrations, and troubleshooting live in the **in-repo README** in the actual project (the copy that gets deployed and is also uploaded to R2). This GitHub repo is a lightweight pointer: project name, live URL, stack, deploy command.
- To work on the build: use the codebase that contains `worker.js`, `wrangler.toml`, `scripts/deploy.sh`, and the full README; deploy with `./scripts/deploy.sh`.
