# juankibin.space

Personal website for **John Kevin Asprec** (`juankibin`).

One-page Astro static site with a custom JK logo mark and a light Three.js / CSS 3D hero.
Dark premium palette: deep charcoal + electric violet + amber.

**Not** the PreSolved marketing site.

## Repository

Hosted at **https://github.com/PreSolvedxAreyci/juankibin-space** (org fallback — personal `@juankibin` create was blocked by PAT permissions).

## Stack

- [Astro 5](https://astro.build/) static SSG
- Plain CSS
- Three.js (CDN) for the hero wireframe
- Deploy: **Azure Static Web Apps** (Free)

## Local development

Requirements: Node.js **20.3+**.

```bash
npm install
npm run dev
```

| Script | Purpose |
|--------|---------|
| `npm run dev` | Dev server (usually `http://localhost:4321`) |
| `npm run build` | Production build → `dist/` |
| `npm run preview` | Preview `dist/` locally |

## Azure Static Web Apps

| Setting | Value |
|---------|-------|
| Resource | `juankibin-web` in `rg-website-hosting-sea` |
| `app_location` | `/` |
| `output_location` | `dist` |
| `api_location` | _(none)_ |

GitHub Actions workflow: `.github/workflows/azure-static-web-apps.yml`

Required repo secret: `AZURE_STATIC_WEB_APPS_API_TOKEN` (deployment token from the SWA resource).

Default hostname (until custom domain): `https://blue-pond-06b355300.2.azurestaticapps.net`

## Custom domain (morning — do not rush overnight)

Apex: `juankibin.space` → this SWA.

**Preserve existing DNS** for Resend / mail:

- Keep records that serve `noreply@juankibin.space` (Resend)
- Keep `presolved` / mail-related subdomains as they are today

Typical Azure SWA apex setup (Cloudflare):

1. In Azure Portal → Static Web App `juankibin-web` → Custom domains → add `juankibin.space` (and optionally `www`).
2. Follow Azure’s validation instructions (TXT / CNAME as shown in the portal).
3. For apex on Cloudflare: often **CNAME flatten** to the SWA default hostname, or use the A/TXT records Azure displays — match the portal exactly.
4. SSL is provisioned by Azure after validation; wait for Ready before cutting traffic.
5. Do **not** delete MX / Resend TXT / DKIM / SPF records while changing web records.

## Brand assets

| Path | Use |
|------|-----|
| `public/brand/logo.svg` | Primary JK mark |
| `public/brand/logo.png` | Raster mark |
| `public/brand/wordmark.svg` | Wordmark |
| `public/favicon.svg` / `.ico` / `.png` | Favicons |

## Contact

CTA email: `johnkevin.asprec@gmail.com` (mailto only — no contact API).
