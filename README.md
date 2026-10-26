# SiteQuote — Building Materials Quote Comparison

SiteQuote is a lightweight, single-page web prototype that helps construction site managers compare three supplier quotations for the same building material using normalized prices and total landed cost.

## Features

- Three-screen flow: requirements and quotes, supplier comparison, decision summary.
- Searchable material catalogue with an **Other / Custom material** option.
- Three supplier quote forms for the same selected material and required quantity.
- Price normalization across supported quote units and package sizes.
- Landed-cost calculation using material cost, freight, and optional additional charges.
- Flags for incomplete quotes and suppliers unable to fulfil the full order.
- Cheapest viable and fastest viable supplier indicators.
- Copyable purchase decision summary.
- Responsive, standalone HTML; no build step or backend required.

## Run locally

1. Download or clone this repository.
2. Open `index.html` in a modern browser.
3. Enter a material and three supplier quotes, then use the tabs to compare and create the summary.

The app is a prototype. Example values in the source are illustrative; verify all calculations and conversion assumptions before using the tool for real purchasing decisions.

## Publish with GitHub Pages

1. Create a GitHub repository named `sitequote` (or another name you prefer).
2. Upload `index.html`, `README.md`, and `PRD.md` to the repository root.
3. Open **Settings → Pages** in the repository.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select the `main` branch and `/(root)` folder, then save.
6. Wait for GitHub Pages to publish the site. The published URL will be shown on the Pages settings screen.

Because the application is a static HTML file, no server or build command is required.

## Project files

- `index.html` — complete working prototype.
- `SiteQuote_PRD.md` — product requirements for the current version.
- `README.md` — setup and publishing instructions.

## Scope limitations

- Exactly three supplier quotes per comparison.
- No supplier accounts, shared database, or cross-device synchronization.
- No automatic WhatsApp quote capture, negotiation chat, supplier ratings, or saved comparison history.
- The prototype does not fetch real supplier prices.

## Suggested repository description

`A single-page building-material procurement prototype for comparing three supplier quotes by normalized unit price and landed cost.`
