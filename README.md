# jaro.in — Site Scaffold

Static HTML site, same deployment model as your other satellite domains
(mbahub.co.in etc.) — no build step, just static files + `vercel.json`.

## What's included
- `index.html` — homepage, broad multi-program portal (catalog-style layout)
- `programs/` — 6 starter program landing pages (MBA, Data Science, Finance,
  Digital Marketing, HR, Healthcare Management)
- `blog/index.html` — blog-first hub with placeholder posts and category filters
- `assets/css/style.css` — shared design system (single stylesheet, no build tool)
- `robots.txt`, `sitemap.xml` — pre-wired for jaro.in
- `vercel.json` — clean URLs (no `.html` in links), basic security headers

## Important discovery
- Jaro already runs a live subdomain **`amritaonlinemba.jaro.in`** for Amrita's MBA program.
  This means jaro.in's DNS is NOT a blank slate — some subdomain records may already exist.
  **Before pointing the root `jaro.in` A/CNAME record at Vercel, check your DNS provider
  for existing records** so you don't accidentally break that live subdomain.

## What you'll need to customize
- Confirm the real, current list of partner institutes in the trust strip
  (index.html) and each program's "Delivered with" fact — I used your known
  IIM Nagpur partnership plus placeholders for others.
- Replace enrollment CTA links (`https://www.jaroeducation.com/`) with your
  actual UTM-tagged enrollment URLs, same as the remapping you did in the
  187-file broken link audit.
- Swap in real blog posts in `blog/index.html` (currently placeholder rows).
- Add real program fee/eligibility copy once finalized — I kept fact-grid
  values generic (duration/format) so nothing false ships live.

## Deploying to Vercel (same flow as mbahub.co.in)
1. Push this folder to a new GitHub repo (or a folder in an existing repo).
2. In Vercel dashboard → **Add New → Project** → import that repo.
3. Framework preset: **Other** (static site, no build command needed).
   - Build Command: leave blank
   - Output Directory: leave as root (`.`)
4. Deploy — you'll get a `*.vercel.app` preview URL first.
5. Go to the project → **Settings → Domains** → add `jaro.in` (and `www.jaro.in`
   if you want both).
6. Point your domain registrar's DNS to Vercel:
   - `A` record for `jaro.in` → `76.76.21.21`
   - `CNAME` for `www.jaro.in` → `cname.vercel-dns.com`
   (Vercel will show the exact records to add once you enter the domain.)
7. Set `www` → `jaro.in` (or vice versa) as the redirect target in the Domains
   tab, the same way you fixed the www/non-www redirect on mbahub.co.in.
8. Once DNS propagates, submit `https://jaro.in/sitemap.xml` in Google Search
   Console for the new property.

## Notes
- No CMS/database — content changes mean editing HTML files directly, same
  as your other satellite domains.
- If you want this to be genuinely blog-first (frequent publishing), it may
  be worth revisiting whether a lightweight CMS (e.g. a headless setup) makes
  more sense long-term than hand-editing HTML for dozens of posts — happy to
  help scope that if useful.
