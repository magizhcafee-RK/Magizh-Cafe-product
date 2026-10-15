# Magizh × B5 Shopping — Admin/User/Partner project

## Files
Upload all files from this ZIP into the same project root (do not put them inside a nested folder).

- `index.html` — customer shopping page
- `admin.html` — admin control panel (`/admin`)
- `partner.html` — partner portal (`/partner`)
- `server.js` — Express backend and shared database APIs
- `db.json` — initial data; server reads and writes this file
- `db.example.json` — clean example data
- `style.css`, `user.js`, `admin.js`, `partner.js` — UI styles and logic
- `approved_mobile_design_reference.html` — exact customer mobile HTML reference supplied for design comparison; the reference itself is not altered
- logo PNG files

## Run locally
Requires Node.js 20+.

```bash
npm install
npm start
```
Open `/` for the customer page and `/admin` for admin.

## Admin access
The initial preview password is `MagizhAdmin@2026`. Log in and change it under **Security** before using real customer data. For deployment, set `ADMIN_PASSWORD` and a strong `SESSION_SECRET` environment variable.

## Implemented workflows
- Shared server-side data for active products/categories, customer accounts, orders and coin balances.
- Admin category create/rename/delete (a category containing products cannot be deleted until those products are moved).
- Product create/edit, up to 3 image uploads, hide/activate and delete.
- Customer registration/login, profile/address saving, cart, coupon/coin savings, payment screenshot upload and order history.
- Admin payment proof review, payment verification and step-by-step order status updates.
- Manual B5 coin credit and approval of customer coin requests; new credit triggers a one-time wallet celebration on the next authenticated visit.
- Partner login creation and partner coin-redemption portal.

## Deployment note
This project currently uses `db.json` and uploaded files on local disk. Use a persistent disk or migrate the database/uploads to durable managed storage before production; ephemeral deployment filesystems can reset on redeploy. Verify the deployment environment and real payment receipts before processing customer orders.
