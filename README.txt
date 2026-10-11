SINCHO DROPSHIP — BODYWORLD CATEGORY IMPORTER (MVP)

WHAT'S INCLUDED
- 62 distinct category links identified in the provided BodyWorld Italy homepage HTML.
- Turkish interface with Categories, Discover Products, and Drafts sections.
- Category search and product search.
- Product card extraction using the observed BodyWorld selectors: .c-product-card, a.c-product-card__name, image, price, description, and stock labels.
- “+ Ekle” saves a product into local browser draft storage; duplicate source URLs are detected.
- Editable product fields, Italian eBay draft helper, 80-character title limit, CSV export, and JSON backup.
- HTML-file import fallback if server-side source access is blocked.
- Cloudflare Worker endpoints: /api/health, /api/categories, /api/scrape.

IMPORTANT LIMITS
- The 62 categories are the distinct category links found in the supplied homepage HTML, not a guarantee that every category on the live site has been captured.
- Live BodyWorld access was not tested from the deployed Worker. The code is syntax-checked and product extraction was tested against the supplied saved HTML, which yielded 36 product cards.
- The importer does not bypass bot protection. If live requests are blocked, use an authorized supplier feed/API or the HTML-file import fallback.
- This MVP reads the category page returned by the source URL; it does not yet crawl every pagination page or all product detail pages.
- eBay publishing/OAuth is not connected. “Ekle” only saves a local draft. Nothing is published automatically.
- Drafts are stored in the current browser's localStorage; they are not synced between devices.
- Before listing, verify price, stock, variants, shipping, product claims, and rights to reuse supplier images/descriptions.

DEPLOY WITH CLOUDFLARE WORKERS (NO TERMINAL OPTION)
1. Open https://dash.cloudflare.com/ and go to Workers & Pages.
2. Create a Worker and open its code editor.
3. Replace the example code with the complete contents of worker.js.
4. Click Deploy and open the assigned *.workers.dev URL.
5. Test /api/health. The homepage is served at /.

DEPLOY WITH WRANGLER
1. Install Node.js LTS.
2. Extract the ZIP and open a terminal in this folder.
3. Run: npm install
4. Run: npx wrangler login
5. Run: npm run deploy

FILES
- worker.js: Cloudflare Worker, embedded UI and server-side scraper.
- index.html: standalone UI preview / HTML-import fallback; server-side scraping requires Worker deployment.
- wrangler.jsonc: Worker configuration.
- package.json: Wrangler scripts.
