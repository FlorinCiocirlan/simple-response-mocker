# simple-response-mocker

[![License: MIT](https://img.shields.io/badge/License-MIT-black.svg)](./LICENSE)
[![Live Site](https://img.shields.io/badge/live-mocker.ciocirlan.dev-black)](https://mocker.ciocirlan.dev)
[![Deployed on Vercel](https://img.shields.io/badge/deployed_on-vercel-black)](https://vercel.com)

Marketing site for **Simple Response Mocker** — a Chrome extension that intercepts `fetch` and `XMLHttpRequest` calls in the browser and returns user-defined mock responses with custom status codes, headers, and JSON bodies.

> **Live:** [mocker.ciocirlan.dev](https://mocker.ciocirlan.dev)

---

## Overview

This repository contains the public-facing landing page for the Simple Response Mocker browser extension. The site is intentionally minimal: a single static `index.html` file with no build pipeline, no client-side framework, and no runtime dependencies.

The extension itself is maintained in a separate repository.

## Tech stack

| Layer       | Choice                                              |
|-------------|-----------------------------------------------------|
| Markup      | Static HTML5                                        |
| Styling     | Vanilla CSS (custom properties, no preprocessor)    |
| Typography  | JetBrains Mono, Newsreader (via Google Fonts)       |
| Hosting     | Vercel (static)                                     |
| CI / CD     | Auto-deploy on push to `main`                       |

No JavaScript framework, no bundler, no Node dependencies — the page ships exactly as written.

## Project structure

```
.
├── index.html      # Single-page landing site (markup + inlined styles)
├── vercel.json     # Vercel config: clean URLs and security headers
├── LICENSE         # MIT
├── README.md
└── .gitignore
```

## Local development

No build step is required.

```bash
git clone https://github.com/FlorinCiocirlan/simple-response-mocker.git
cd simple-response-mocker
open index.html        # macOS
# or: xdg-open index.html  (Linux) / start index.html  (Windows)
```

For live reload during development, any static server works:

```bash
npx serve .
# or
python3 -m http.server 8000
```

## Deployment

The `main` branch is connected to a Vercel project. Every push triggers a production deployment; pull requests receive isolated preview deployments.

`vercel.json` declares:

- `cleanUrls: true` — strips `.html` extensions from URLs.
- HTTP security headers applied to all routes:
  - `X-Content-Type-Options: nosniff`
  - `Referrer-Policy: strict-origin-when-cross-origin`
  - `Permissions-Policy: camera=(), microphone=(), geolocation=()`

### Custom domain

The site is served from `mocker.ciocirlan.dev` via a CNAME record pointing to `cname.vercel-dns.com`. TLS is provisioned and renewed automatically by Vercel.

## Contributing

Issues and pull requests are welcome. For substantial changes, please open an issue first to discuss the proposed direction.

## License

Released under the [MIT License](./LICENSE).
