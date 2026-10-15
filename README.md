# Magizh × B5 Shopping + Admin + Partner Portal

Mobile-first Node/Express project for GitHub + Render. The customer page, admin panel and partner portal share the same server-side JSON data store in this demo.

## Pages
- `/` — mobile customer shopping page, category/product browsing, profile/address, cart, coupon, B5 coin use, screenshot-based payment proof, order history and status timeline.
- `/admin` — admin dashboard with one sidebar section open at a time: dashboard, category management, products, orders/payments, B5 coins, partners, payment/delivery/coupon settings, and password security.
- `/partner` — partner login/dashboard and customer coin redemption.
- `/api/health` — health check.

## Admin access
- Preview default password: `MagizhAdmin@2026` if `ADMIN_PASSWORD` is not set and no admin password has been changed in the database.
- Recommended: set `ADMIN_PASSWORD` and `SESSION_SECRET` in Render environment variables. After login, use **Security → Change Admin Password** to set a database-backed password. If you change the password in the dashboard, keep the database/persistent disk; a fresh deployment without persistent data may reset it.
- Create each partner username/password under **Partners**. There is no shared default partner password.

## Deploy to Render
- Build command: `npm install`
- Start command: `npm start`
- Environment variables: `NODE_ENV=production`, `SESSION_SECRET=<long-random-secret>`, and preferably `ADMIN_PASSWORD=<strong-password>`.
- Persistent storage: mount a Render persistent disk at the project path used for `db.json` and `uploads`, or replace JSON storage with PostgreSQL before production. Render ephemeral files can reset on redeploy/restart without persistent storage.

## Included workflow
- Admin category add / rename / delete (deletion is blocked while active products still use that category).
- Product create / edit / hide / activate / delete, up to 3 uploaded JPG/PNG/WebP photos, weight, price, description and category dropdown.
- Customer products and admin use the same `/api/public-data` + `/api/admin/data` database.
- Order proof screenshot appears in Admin. Admin verifies payment before moving an order to Payment verified, Packed, Dispatched/Couriered, Delivered. Customer sees the order timeline.
- Admin manually credits B5 coins; customers see a one-time celebration when they next open the site. Coin request approvals also create notifications.
- Coupon code/percentage can be changed in Admin Settings. Default preview coupon is `MAGIZH10` at 10%.
- 1 B5 Coin = ₹1 for checkout; available coins and valid coupon savings reduce the order total.

## Important production notes
This is a testable starter, not a production-hardened commerce system. It uses a JSON file database and the default Express memory session store. Before accepting real payments or customer information, use persistent storage/database, a production session store, CSRF/rate limiting, proper password recovery/email delivery, payment gateway verification, backups, and privacy/security review. Payment screenshot approval is manual; this project does not process payments itself.


FLAT UPLOAD PACKAGE: All project source files are placed at the repository root (no public/, data/, assets/, or uploads/ folders). User uploads are saved as uploaded_* files in the root and served only through /uploads/:file.
