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
- Environment variables: `ADMIN_PASSWORD` (strong password), `SESSION_SECRET` (long random secret), `NODE_ENV=production`. For password reset email, also set `APP_URL` (your deployed Render URL), `SMTP_HOST`, `SMTP_PORT` (usually 587), `SMTP_USER`, `SMTP_PASS`, optional `SMTP_FROM`, and `SMTP_SECURE=false` unless your SMTP provider requires TLS on connect.

After deploy, test `/api/health`, then `/`, `/admin`, and `/partner`. Admin must create partner login before partner can sign in.

## Important testing notes
This is a testing build. JSON storage and default in-memory sessions are not production-ready. Render filesystem may reset without persistent storage. Payment is manual; verify payment in your bank/UPI account before marking it verified.

## User-page refinement update (October 2026)
- Mobile product cards support pack-size selection (50 g, 100 g, 250 g, 500 g, 1 kg) with proportional pricing when custom variants are not configured. Product photos open a full-screen gallery; upload up to three images per product from Admin.
- Partner Offers, Coupons & Offers, and My Orders open in focused page-style views. The top-left menu slides in as a side drawer.
- Checkout includes View All Coupons, coupon savings, B5 Coin redemption, itemized totals, and a savings amount/percentage counter.
- Admin can create/pause coupons and set the maximum B5 Coin redemption percentage for each product (0–100%). The checkout and server both enforce the per-product limit and customer wallet balance. One B5 Coin equals ₹1.
- Coin redemption is deducted from the customer's wallet when the order is submitted. If a payment is later rejected/cancelled, a refund process must be added before production use.

## Important deployment note
This remains a functional pilot/demo implementation. Before public production use, configure persistent storage/database and durable sessions on Render, add payment-failure coin refunds, review security and privacy, and test all checkout flows using a staging deployment.


## Profile, password reset and partner offer catalogue
- Customers can save profile details and up to 10 delivery addresses from the Profile page. The header button and drawer entry open a dedicated Profile screen (login is requested if the customer is signed out). Profile stores personal details and up to 10 delivery addresses.
- Forgot Password sends a time-limited reset link by email only when SMTP environment variables are configured in Render. Reset links expire after 30 minutes.
- Admin can create partner logins with shop category, offer image URL, offer description, minimum bill and optional maximum coin cap. Partner offers appear as image cards on the customer page.
- Customers may request B5 Coin redemption at a partner. The partner portal displays pending requests and only deducts coins after partner approval; rejected requests do not deduct coins. Partner must verify the bill in person before approval.


## Admin improvements in v6
- Admin can edit partner shop details, username, offer percentage, minimum bill, maximum coin cap, catalogue image URL, address, description and active/paused status. Leave the password field blank when editing to keep the existing password; enter a new password to reset it.
- Admin can configure the global order-reward coin percentage in Payment & Delivery Settings, in addition to the per-product coin redemption percentage.
- Partner records and offer images feed the customer-facing Partner Offers catalogue. The partner login remains separate at `/partner`; admin creates credentials and can pause or reactivate partner visibility.
- Profile opens as a dedicated detail screen rather than showing the home content behind it.


## Temporary test login credentials (change before public launch)
- Admin page: username is not required; password: `MagizhAdmin@2026`. If `ADMIN_PASSWORD` is set in Render Environment, that configured value takes priority. To change it, update `ADMIN_PASSWORD` in Render and redeploy/restart.
- Seeded partner portal: username `nmk001`, password `B5Partner@2026`. On first successful login, the seeded blank password hash is replaced with a secure hash in the JSON database. Admin can later change the partner password from the Admin Partner section.
- These are temporary demo credentials. Change them before sharing the live website publicly.
