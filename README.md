# Scoop Legal Site

Static HTML pages hosted on GitHub Pages at `scoop-ice-cream.com`.

- `index.html` — landing with links
- `privacy.html` — Privacy Policy
- `imprint.html` — Impressum (§5 TMG)
- `CNAME` — custom domain config for GitHub Pages

## One-time deploy (5 min)

1. **Fill in the email placeholders.** Search for `[YOUR SCOOP EMAIL]` in `privacy.html` and `imprint.html` and replace with your support email (3 occurrences total).
2. **Create a public GitHub repo** named `scoop-legal` (or anything you like).
3. **Push these files** to the repo's default branch:
   ```bash
   cd legal-site
   git init
   git add .
   git commit -m "Initial legal site"
   git branch -M main
   git remote add origin git@github.com:<your-username>/scoop-legal.git
   git push -u origin main
   ```
4. **Enable GitHub Pages**: GitHub repo → Settings → Pages → Source: `Deploy from a branch` → Branch: `main` / `(root)` → Save.
5. **Configure custom domain DNS** at your domain registrar (Namecheap, etc.):
   - Add a CNAME record: `www` → `<your-username>.github.io`
   - Or four A records on the apex pointing to GitHub's IPs:
     - `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
6. **Wait 1–10 min** for DNS propagation, then visit `https://scoop-ice-cream.com`. GitHub auto-issues a Let's Encrypt cert.

## Final URLs

- `https://scoop-ice-cream.com/` — index
- `https://scoop-ice-cream.com/privacy.html` — Privacy Policy
- `https://scoop-ice-cream.com/imprint.html` — Impressum

Use the `/privacy.html` URL in:
- `src/app/paywall.tsx` (`PRIVACY_URL` constant)
- App Store Connect → App Information → Privacy Policy URL

## Updating

Just edit the HTML, commit, push. GitHub Pages redeploys in ~30 seconds.