# Amazing Mr Twist — Cloudflare Deploy Package

Static HTML site for **amazingmrtwist.com**. 11 pages, fully SEO-optimized, mobile-responsive, dark-themed premium design.

## Deploy to Cloudflare Pages

**Option A — Direct upload (fastest):**
1. Cloudflare Dashboard → Workers & Pages → Create → Pages → Upload assets
2. Drag & drop the entire folder contents
3. Set project name → deploy
4. Custom domain: add `amazingmrtwist.com` in project settings → follow DNS instructions

**Option B — GitHub connection (recommended for ongoing updates):**
1. Push this folder to a GitHub repo (any name)
2. Cloudflare Dashboard → Workers & Pages → Create → Pages → Connect to Git
3. Select repo, set build settings:
   - Build command: (leave blank — no build needed)
   - Build output directory: `/` (root)
4. Deploy → connect custom domain in Pages settings

Both options work. Option B lets you push changes to GitHub and Cloudflare rebuilds automatically.

## Manual bits to replace BEFORE going live

**1. Google Business Profile review link (leave-review.html)**
Find this in `leave-review.html`:
```
<a class="btn btn-gold" id="gbp-link" href="PASTE_GBP_REVIEW_LINK_HERE" target="_blank" rel="noopener">
```
Replace `PASTE_GBP_REVIEW_LINK_HERE` with Dan's actual GBP review link. Get it from:
- Sign into Google Business Profile → your business → "Get more reviews" → copy short URL
- Or format: `https://g.page/r/YOUR_PLACE_ID/review`

**2. Second full-length video (currently missing)**
The homepage hero uses the 9-second tissue→flame→dove clip. For a fuller showreel:
- Upload the 4-min video to YouTube (unlisted or public)
- Get the video ID from the URL
- The gallery page already embeds Dan's existing YouTube (myd9i4Vv0OQ) — swap that ID for the new one if you'd rather use the longer video

**3. Favicon (currently placeholder)**
Current favicon is a placeholder "M" in gold on midnight blue. Generate the proper set:
- Go to https://realfavicongenerator.net
- Upload Dan's Amazing Mr Twist logo
- Download the generated set
- Replace all files in `/images/favicon/`

## Post-launch checklist (do these AFTER Cloudflare goes live)

1. **Google Search Console**
   - Add property: `https://amazingmrtwist.com`
   - Verify via Cloudflare DNS TXT record (fastest method)
   - Submit sitemap: `https://amazingmrtwist.com/sitemap.xml`
   - Request indexing for homepage + top pages

2. **Google Analytics 4**
   - Create GA4 property for amazingmrtwist.com
   - Get Measurement ID (starts with G-...)
   - Add gtag script to each HTML `<head>` (before `</head>`)
   - Link GA4 property to Search Console

3. **Google Business Profile**
   - Ensure Dan's profile is claimed and verified
   - Get direct review link → paste into `leave-review.html` (see above)

4. **Test everything**
   - Every page loads correctly
   - Contact links (phone, email) work on mobile
   - Video plays on iOS Safari and Android Chrome
   - Forms/CTAs behave as expected
   - No broken internal links

## File structure

```
/
├── index.html                         Homepage (hero video, all sections)
├── kids-parties.html                  Audience landing page — kids market
├── adult-themed-shows.html            Audience landing page — adult/corporate
├── gallery.html                       Full photo gallery + YouTube embed
├── reviews.html                       Bark & WOMO review platforms
├── leave-review.html                  Review funnel (4-5★→GBP, 1-3★→dead end)
├── privacy.html
├── terms.html
├── 404.html                           Custom "vanishing act" 404 page
├── thank-you.html                     Post-contact-form thank you
├── sitemap.xml
├── robots.txt
├── _headers                           Cloudflare Pages security + cache
├── _redirects                         Cloudflare Pages redirects
├── services/
│   ├── magic-show.html                Stage show service page
│   └── roving-magic.html              Roving magic service page
├── images/
│   ├── favicon/                       Favicon set (placeholder — regenerate)
│   └── [13 optimized photos]          All under 250KB, EXIF-corrected
└── videos/
    ├── hero_tissue_flame_dove.mp4     3.1MB, H.264, faststart
    └── hero_poster.jpg                Poster frame for video
```

## Design system

- **Colors**: Deep midnight blue background (#0A0E1B), warm gold accent (#D4A574), off-white text
- **Fonts**: Playfair Display (display serif) + Inter (body sans)
- **Vibe**: Premium/theatrical, magic-appropriate, works for both kids and adult positioning

## Contact for updates

If you need site changes made, ping Ryder at Keystone Growth — this build is by Keystone.

---

Built: August 2026 · Keystone Growth · for Dan Stewart / Amazing Mr Twist
