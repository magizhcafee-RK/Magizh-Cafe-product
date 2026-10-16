# Magizh × B5 Shopping (flat deployment package)

All project files are in this folder's root so they can be uploaded together to GitHub/Render without nested project folders.

## Run
- Node.js 20+
- `npm install`
- `npm start`
- Customer page: `/`
- Admin page: `/admin`
- Partner page: `/partner`
- Health check: `/api/health`

Default admin password for a fresh demo database: `MagizhAdmin@2026`. Change it from Admin > Security before production. Set `SESSION_SECRET` and `ADMIN_PASSWORD` environment variables on deployment.

Customer actions include login/register, cart quantity updates, coupon preview and savings popup, checkout with payment proof upload, order history, B5 coin request with registered mobile/B5 ID/email validation, and district/category/search filtering for partner shops. Admin approves coin requests and may set the approved coin amount.

Note: this demo stores data in `db.json` on the server filesystem. Use persistent storage or a managed database before production deployment. Partner directory shows partners created in Admin; partner images/category management can be extended in the next correction round.
