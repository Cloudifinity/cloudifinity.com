# cloudifinity.com

The Cloudifinity landing page. A single static page served by GitHub Pages on
the custom domain [cloudifinity.com](https://cloudifinity.com).

No build step, no framework. GitHub Pages serves `index.html` from the repo root
as-is.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The page (hero, about, services, contact, footer). |
| `styles.css` | All styling. Brand palette and responsive layout. |
| `favicon.svg` | Favicon built from the Cloudifinity infinity mark. |
| `CNAME` | Tells GitHub Pages to serve on the custom domain. |
| `assets/` | The logo and social-preview image actually used by the page. |

> The full brand logo set (SVG, PNG, PDF, EPS) lives outside this repo, in the
> parent `website/cloudifinity-logo/` folder, so only the assets the site serves
> are published.

## Local preview

From the repo root:

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000/>.

## Deploying with GitHub Pages

1. Push to the `main` branch.
2. In the repo: **Settings -> Pages**.
3. Under **Build and deployment**, set **Source** to *Deploy from a branch*,
   branch `main`, folder `/ (root)`. Save.
4. The `CNAME` file sets the custom domain to `cloudifinity.com` automatically.
5. Once the certificate has provisioned, tick **Enforce HTTPS**.

## DNS records

Set these at your domain registrar / DNS provider for the apex domain.

**A records** (`cloudifinity.com` -> GitHub Pages):

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

**AAAA records** (IPv6, same host):

```
2606:50c0:8000::153
2606:50c0:8001::153
2606:50c0:8002::153
2606:50c0:8003::153
```

**CNAME record** for the `www` subdomain:

```
www  ->  cloudifinity.github.io
```

DNS changes can take a little time to propagate. After they do, GitHub will
issue a TLS certificate for the domain, at which point you can enforce HTTPS.

## Editing content

The copy lives directly in `index.html`. Service cards are in the
`#services` section, contact details point at `hello@cloudifinity.com`. Update
the text in place and push.
