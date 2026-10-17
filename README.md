# Magizh × B5 Shopping (Admin session/mobile correction)

## Run locally
1. Install Node.js 20+
2. Run `npm install`
3. Run `npm start`
4. Customer: `http://localhost:3000/`
5. Admin: `http://localhost:3000/admin`
6. Default admin password for a fresh database: `MagizhAdmin@2026`

Set `ADMIN_PASSWORD` and `SESSION_SECRET` as environment variables before deployment. On Render/HTTPS, set `NODE_ENV=production`; server trusts the reverse proxy so secure login cookies can persist. Admin login explicitly saves the session before returning success.

Admin → Categories: add/edit/delete categories. Admin → Products: add/edit name, category, price, weight, description and up to 3 photos; hide/activate/delete. Changes are stored in `db.json` and returned by `/api/public-data` to the customer page. Orders submitted with payment proof appear in Admin → Orders & Payments; payment verification and status steps update customer order history.

IMPORTANT DEPLOYMENT NOTE: the JSON database and uploaded photos must be placed on persistent storage for a hosted deployment. A restart/redeploy on ephemeral storage can reset them. Configure a persistent disk or replace JSON storage with a managed database before production.


Latest visual fixes: Magizh logo transparent margins cropped; B5 logo cropped to a circular transparent badge; bottom Partners navigation opens the Partner Shops & Offers panel rather than scrolling to a missing section.
