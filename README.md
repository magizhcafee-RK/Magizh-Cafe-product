# Magizh × B5 — Flat GitHub + Render Upload

All source files are placed directly in the project root to make GitHub upload easier. There are no `public/`, `assets/`, or `data/` source folders. The server creates its private database file and `uploads/` folder automatically when it starts.

## Latest mobile UI update
- Preserves the compact Magizh mobile home screen and the green/cream/orange theme.
- Checkout is now a richer 3-step flow: Cart & offers, Delivery address, and Payment proof.
- Shows estimated B5 Coins before placing the order and an order confirmation screen. B5 Coins are credited only after Admin verifies payment.

## Customer page updates in this build
- Register/Login sheet is centered with breathing room on both sides.
- The mobile bottom navigation is customer-only; Admin and Partner are no longer shown there. Their separate pages remain at `/admin` and `/partner`.
- The top-left slide menu contains Shop, Partner Offers, B5 Coin Wallet, My Orders, Coupons & Offers, and Account.
- Product photos open a full-screen gallery with previous/next controls and thumbnails (up to three uploaded photos per product).
- Pack-size selector offers 50 g, 100 g, 250 g, 500 g, and 1 kg. If the product has explicit `variants` with prices, those are used; otherwise the demo calculates size prices proportionally from the base product price. **Before live selling, configure exact pack prices** (the admin editor is the next phase).
- Partner Offers opens a dedicated list backed by active partner records from the server.
- Cart shows selected pack size, quantity controls, coupon application, estimated savings, B5 Coins to be earned, delivery, total, and a three-step address/payment checkout.
- Coupon page supports `settings.coupons` entries (`code`, `percent`, optional `minOrder`, `description`, `active`) and the legacy single `couponCode` / `couponPercent` setting.

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
