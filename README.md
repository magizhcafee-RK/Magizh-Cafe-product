# Magizh × B5 Shopping (Customer + Admin + Partner)

## Deploy
1. Upload these files from this ZIP to the same project root in GitHub (do not put them inside an extra folder).
2. Deploy as a Node web service with `npm install` and `npm start` (Node 20+).
3. Set persistent disk/storage for `db.json` and uploaded product/payment images in production; without persistent storage, redeploys/restarts can reset them.
4. Set `SESSION_SECRET` to a long random secret and `ADMIN_PASSWORD` to a strong password in the hosting environment.
5. Open `/admin`, sign in using the configured `ADMIN_PASSWORD` (local preview fallback: `MagizhAdmin@2026`), then add a category first and add products using that category.

## Shared workflow
- Admin categories/products and active product images are served to the customer page through `/api/public-data`.
- Product create/edit supports up to 3 JPG/PNG/WebP images (5 MB each).
- Customer orders are saved in the same `db.json`; Admin > Orders & Payments lists payment proofs and order status changes.
- Admin actions require a valid admin session. If the session expires, the admin login panel is shown again instead of silently leaving the form unusable.
- On mobile, the Management Menu opens a compact two-column slide-out menu; on desktop it stays as a side navigation.

## Important
Before taking real payments, configure secure hosting, persistent storage, strong secrets/passwords, and verify payment screenshots against actual bank/UPI records. This project stores data in a JSON file; for multi-instance production deployment, use a shared database and shared file storage.
