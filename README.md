# Gemstone Business — Final project source

## Run on Windows
1. Install Node.js 24 or newer.
2. Extract the whole ZIP into a folder. Do not run it from inside the ZIP.
3. Double-click START-WINDOWS.bat. Keep its window open.
4. Open http://localhost:3000 in Chrome or Edge.
5. Select Sign Up and create your account. There is no default password.

Alternatively, open a terminal in this folder and run `npm start`.
No npm package installation, Python or MySQL is required for local use.
Your local database is created at `.local/gemstone.sqlite`. Keep that file to retain your accounts, photos and orders. Local data is separate from the hosted site's data. Back up the database with the app stopped.

## Included changes
- Add and edit listings; preview and replace photos using gallery/camera controls.
- Photo resizing and readable errors, with input files up to 20 MB. Browser-decodable formats supported; use JPG/PNG or a screenshot when HEIC is unsupported.
- Delete your own listings from Marketplace, Inventory or listing details. A confirmation page explains that orders and account history remain intact. Deleted listings cannot be purchased.
- Certificate photo attachments saved with laboratory/report details, separate from QR/barcode scanning.
- Orders, stock, customer details, invoices, sales and payment balances.
- Mobile layouts and simple gem chatbot with clearly labelled basic guidance fallback.

## Using photos
Marketplace: choose your listing → Edit → Choose from gallery (or Take a photo) → wait for the preview → Publish listing.
Certificates: scroll to Link a laboratory report → select your gemstone → enter the laboratory and report number → choose a photo → Save report record. Select the same gemstone later to replace its saved photo.
The scanner reads QR/barcodes only. An uploaded certificate photograph is not proof of authenticity; confirm the report with the issuer.
Phone camera behaviour depends on the browser/device. The hosted HTTPS site is the supported way to use camera scanning on a phone; the local server binds to localhost only.

## AI
Full AI responses require a valid OpenAI API key with active API billing. Basic guidance works without it. No API keys are included. If you already have a key, copy `.env.example` to `.env.local` and configure it there, then restart. Never put secrets in frontend JavaScript or share your .env.local file.
The chatbot does not certify gemstone identity, origin or treatment from photos.

## Checks
`npm test` checks listing persistence, ownership, checkout transactions, stock, balances, report/photo storage and deletion.
`npm run build` creates the hosted Worker artifact; `npm run validate` checks it.

## Project structure
- static/: frontend HTML, CSS, JavaScript and assets
- worker/api.js: API and database schema (Cloudflare D1 in hosting)
- worker/index.js: generated self-contained Worker
- scripts/server.mjs: local Node + SQLite server
- tests/: integration checks using an in-memory SQLite database
- .openai/hosting.json: existing hosted Site configuration

`npm run dev` is an INTERNAL QA preview with synthetic users and preview-only session routes. Use `npm start` for normal local use. Do not publicly expose the QA server.

## Testing limits
Automated photo persistence and deletion checks passed. Native Android/iOS camera capture and the full gallery picker upload were not verified on a physical device. The previous browser file-chooser test was interrupted.
