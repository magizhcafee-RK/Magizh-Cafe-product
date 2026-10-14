# Magizh × B5 Shopping Project — Refined Mobile UI

## Pages
- `/` — customer shopping website (classic compact Magizh mobile home layout)
- `/admin` — separate admin page
- `/partner` — separate partner page
- `/api/health` — service health check

## What's updated
- Removed Admin and Partner from the customer's bottom navigation and hamburger menu. Admin and Partner remain separate pages at `/admin` and `/partner`.
- Refined mobile cart to use a cleaner white marketplace-style checkout sheet, stronger bold typography, product cards, quantity controls, coupon area, free-delivery progress, item MRP, product discount, coupon savings, delivery fee, estimated total, savings total, and B5 coin estimate.
- Address and payment steps remain separate and responsive.

## Render settings
- Root Directory: leave blank
- Build Command: `npm install`
- Start Command: `npm start`
- Set `ADMIN_PASSWORD` in Render Environment Variables.
- Set `SESSION_SECRET` in Render Environment Variables.

## GitHub upload
Extract this ZIP and upload all files from inside it directly into the repository root. `server.js`, `package.json`, `index.html`, `user.js`, `style.css`, `admin.html`, `admin.js`, `partner.html`, `partner.js`, and `db.example.json` should be at the root level, not inside another nested folder.

## Important deployment note
The JSON-file database and in-memory session configuration are suitable for testing only. Before real production use, configure persistent storage/database and durable session storage. Payment is manual: customers submit a payment screenshot and the admin verifies it. B5 Coins are pending until verification.
