# tsuku.dev

Website for [tsuku](https://github.com/tsuku-dev/tsuku) - a self-contained package manager for developer tools.

## Structure

```
tsuku.dev/
├── index.html          # Landing page
├── install.sh          # Installation script (served at get.tsuku.dev)
├── assets/
│   └── style.css       # Minimal dark theme CSS
├── stats/
│   └── index.html      # Telemetry dashboard (placeholder)
├── telemetry/
│   └── index.html      # Privacy policy (placeholder)
├── _redirects          # Cloudflare Pages routing
├── _headers            # Custom HTTP headers
└── README.md           # This file
```

## Deployment

This site is deployed via Cloudflare Pages:

- **Main site**: https://tsuku.dev
- **Install endpoint**: https://get.tsuku.dev

## Local Development

Open `index.html` in a browser. No build step required.

For testing with a local server:

```bash
# Python
python3 -m http.server 8000

# Node.js (if serve is installed)
npx serve
```

## License

MIT License - See the main [tsuku repository](https://github.com/tsuku-dev/tsuku) for details.
