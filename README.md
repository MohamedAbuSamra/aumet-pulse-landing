# Aumet Pulse — Landing Pages

Arabic-first (with English toggle) landing pages for **Aumet Pulse**, the all-in-one pharmacy operating system by Aumet.

## Live links

| Page | URL |
| --- | --- |
| B2B — pharmacy operating system, with animated product demo | https://mohamedabusamra.github.io/aumet-pulse-landing/b2b.html |
| P2P — pharmacy-to-pharmacy exchange | https://mohamedabusamra.github.io/aumet-pulse-landing/ |
| Original all-in-one page | https://mohamedabusamra.github.io/aumet-pulse-landing/landing-page.html |

Hosted on GitHub Pages from the `main` branch. Every push to `main` updates the live pages within a minute or two.

## Files

- `b2b.html` — B2B landing page. On desktop the demo plays the seller's dashboard next to the buyer's phone; on mobile it shows the buyer's phone with a step-by-step header, next/previous buttons and swipe.
- `index.html` — P2P exchange landing page.
- `landing-page.html` — the original all-in-one page.
- `pulse-landing-prompt.md` — prompt for rebuilding or refining the page with AI tools.

Each page is a single self-contained HTML file (inline CSS and JS, Google Fonts only), so there is no build step.

## Run locally

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000/b2b.html.
