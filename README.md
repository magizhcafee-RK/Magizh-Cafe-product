# Magizh × B5 Shopping

## Run
- Node.js 20+
- `npm install`
- `npm start`
- Customer page: `/`
- Admin page: `/admin`
- Partner page: `/partner`

## Customer update in this build
- Preserves the approved mobile storefront HTML/CSS layout.
- Customer profile no longer displays B5 Member ID; supports up to three saved delivery addresses.
- Bottom navigation uses View Cart instead of Wallet.
- B5 coin request form asks for registered mobile number, B5 Member ID, email ID, and request details. Requests are stored for admin review; admin approval credits the customer wallet.
- Partner directory is sourced from active partners in the database, with district filtering and shop search.
- Hero text rotates between three promotional messages. Admin-managed promotion image upload and email-based password reset still require a separate backend/configuration step.

## Important configuration
Set `SESSION_SECRET` and `ADMIN_PASSWORD` in the deployment environment before production use. The forgot-password endpoint currently returns a clear message because outbound email service is not configured; it does not claim to send an email.
