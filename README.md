# Magizh × B5 Shopping Project

## Customer-side functionality update
The approved mobile design remains the customer `index.html` layout. Customer interactions are in `user.js` and use the Express API in `server.js`.

### Included customer actions
- Load active products and categories from shared backend data.
- Search products, filter by category, and add/remove/change cart quantities.
- Customer registration/login, profile and delivery address save, logout.
- Checkout with delivery calculation, coupon code, B5 coin use and payment screenshot upload.
- Customer order history and status timeline.
- B5 wallet balance, coin request, and notification when admin credits coins.
- Partner offer information view.

## Run
Requires Node.js 20+.
1. Extract all files into one project folder.
2. Run `npm install`.
3. Run `npm start`.
4. Open the site at the deployment URL; Admin is at `/admin` and partner page at `/partner`.

Admin default password (change after first login): `MagizhAdmin@2026`.

Important: this is the customer-side interaction pass. Admin page corrections and a full browser/live deployment test are still separate next steps. For production, configure a persistent database/storage, secure session secret, HTTPS, and a strong admin password.
