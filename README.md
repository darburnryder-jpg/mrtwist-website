# Amazing Mr Twist — Cloudflare Workers Deploy

Static site for **amazingmrtwist.com**. One clean homepage + 2 service pages + utility pages.

## Fixing your deploy (the important bit)

Your Cloudflare project is running as a **Worker** (that's what the `.workers.dev` URL means). Not Pages. The Pages settings you were fighting with won't work — Workers uses different config.

### In Cloudflare dashboard, set these EXACTLY:

Go to your project (`small-rain-e731`) → Settings → Build:

- **Framework preset:** None
- **Build command:** *(leave blank — or set to `echo "no build"` if it insists)*
- **Deploy command:** `npx wrangler deploy`
- **Root directory:** `/mrtwist_v2` (if the repo has files in that subfolder) OR blank if files are at repo root
- **Save**

Then commit + push this whole folder to your GitHub repo. Cloudflare will auto-deploy in ~30 seconds.

The `wrangler.toml` file in this folder tells Wrangler everything it needs:
- Project name: `small-rain-e731` (matches your Cloudflare project)
- Serves all static files from the folder
- Uses `404.html` for missing pages automatically

That's it. No `--project-name` flag needed. No manual config in the dashboard beyond the deploy command.

### If you need to change the project name

Edit line 4 of `wrangler.toml`:
```
name = "your-project-name-here"
```

## What's in this build

**Homepage (index.html)** — single scrolling page:
1. Nav
2. Hero — text left, autoplaying dove/flame/tissue video right (portrait mobile-style)
3. Credentials strip — 20+ years / 1000+ shows / All VIC / 5★ rated
4. YouTube video section — Dan's showreel embedded
5. Two services with photos — Stage Magic Show + Roving Close-Up
6. About — portrait photo of Dan + bio
7. Reviews — Bark + WOMO cards linking out
8. FAQ
9. Contact form — real form, submits via user's email client

**Other pages:**
- `services/magic-show.html` — full stage show details
- `services/roving-magic.html` — full roving details
- `privacy.html`, `terms.html`
- `404.html`, `thank-you.html`

## Placeholders to replace before launch

1. **Favicon** — currently a placeholder gold "M" in `/images/favicon/`. Regenerate at [realfavicongenerator.net](https://realfavicongenerator.net) using Dan's actual logo, replace all files in `/images/favicon/`.

2. **The 4-minute showreel video** — currently the gallery/video sections use Dan's existing YouTube (myd9i4Vv0OQ). If you want the full 4-min video swapped in, upload it to YouTube unlisted, get the ID, then replace `myd9i4Vv0OQ` in `index.html` with the new ID.

## Post-launch checklist

1. **Google Search Console** — verify property, submit `sitemap.xml`, request indexing
2. **GA4** — install measurement ID, link to Search Console
3. **Test contact form** — submit yourself, confirm the email arrives at mrtwist.DS@gmail.com

## Form note

The contact form uses `mailto:` — when someone submits, it opens THEIR email client (Gmail, Apple Mail, etc.) with the message pre-filled and Dan's email pre-filled. They then hit send from their own email account.

**Advantages:** zero backend, works instantly, no signup required, no monthly costs.

**Downside:** on desktop, users without a configured email client see a browser prompt. Most users are on mobile where this works perfectly.

**Upgrade later:** if you want form submissions to land in Dan's inbox automatically (no email client needed), sign up for [Formspree](https://formspree.io) (free tier), grab the endpoint URL, and swap the form's `onsubmit` for their `action=`. 10-minute change if/when you want it.

---

Built August 2026 · Keystone Growth · for Dan Stewart / Amazing Mr Twist
