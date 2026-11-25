# DigitalStore Pro — starter website

A responsive digital-product storefront starter for PDFs, planners, ebooks and flipbooks. Includes a product catalogue, category filters, checkout email modal, and a server-side Paystack transaction initialization endpoint.

## Run locally

1. Install Node.js 20 or newer.
2. Extract this project and open a terminal in its folder.
3. Run `npm install`.
4. Copy `.env.example` to `.env`.
5. Add your Paystack **test** public and secret keys to `.env`.
6. Run `npm run dev`.
7. Open `http://localhost:3000`.

## Add or edit products

Edit the `products` array in `server/index.js`. Prices are in the smallest currency unit (for ZAR, cents): `14900` means R149.00. Update each product's name, description, category, type and cover style.

## Important before taking real payments

This is a visual and checkout starter, not a finished production commerce system. Before launch:

- Keep the Paystack secret key only in the server `.env`; never put it in browser JavaScript or commit `.env` to GitHub.
- Use Paystack test keys first, then switch to live keys only after testing.
- Implement server-side transaction verification using Paystack's verify endpoint.
- Store orders and payment references in a database.
- Deliver download links / flipbook access only after verified successful payment. Use private file storage and signed, expiring links; do not expose paid PDF files in the public folder.
- Configure the Paystack webhook URL as `https://YOUR-DOMAIN/api/paystack-webhook`.
- Add an admin login with secure authentication before enabling product uploads or order management.
- Add your business contact details, refund policy, privacy policy, terms, and POPIA-appropriate privacy practices.
- Test mobile layouts, failed payments, duplicate webhook events, refunds, and customer delivery emails.

The sample webhook currently validates the Paystack signature and logs successful payment events, but deliberately does not grant downloads. The payment-return page is not proof of payment.

## Deployment

Deploy the Node app to a host that supports Node.js (for example Render, Railway, or another Node host). Set the environment variables in the host dashboard, including `SITE_URL` and Paystack keys. Connect your custom domain after registering it and enable HTTPS.
