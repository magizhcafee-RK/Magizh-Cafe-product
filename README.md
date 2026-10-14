# Magizh × B5 — Flat GitHub + Render Upload

All source files are placed directly in the project root to make GitHub upload easier. There are no `public/`, `assets/`, or `data/` source folders. The server creates its private database file and `uploads/` folder automatically when it starts.

## Latest mobile UI update
- Preserves the compact Magizh mobile home screen and the green/cream/orange theme.
- Checkout is now a richer 3-step flow: Cart & offers, Delivery address, and Payment proof.
- Shows estimated B5 Coins before placing the order and an order confirmation screen. B5 Coins are credited only after Admin verifies payment.

## Pages
- Customer: `/`
- Admin: `/admin`
- Partner: `/partner`
- Health: `/api/health`

## GitHub upload
1. Extract this ZIP.
2. Open the extracted folder. You should see `package.json`, `server.js`, `index.html`, `admin.html`, `partner.html`, JS/CSS files and logo images together.
3. Upload these files directly to the root of your GitHub repository. Do not upload only the ZIP file.

## Render
- Build command: `npm install`
- Start command: `npm start`
- Environment variables: `ADMIN_PASSWORD` (strong password), `SESSION_SECRET` (long random secret), `NODE_ENV=production`

After deploy, test `/api/health`, then `/`, `/admin`, and `/partner`. Admin must create partner login before partner can sign in.

## Important testing notes
This is a testing build. JSON storage and default in-memory sessions are not production-ready. Render filesystem may reset without persistent storage. Payment is manual; verify payment in your bank/UPI account before marking it verified.
