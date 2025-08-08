# Festival E-Card Store — Deployable Package

This repository contains a ready-to-deploy backend and example serverless functions for the Festival E-Card store.

## Contents
- `backend/` — Node.js Express backend (WhatsApp webhook, OpenAI, Canva integration)
- `vercel/functions/` — Example serverless functions for Vercel (create-payment, generate-ideas)
- `.env.example` — example environment variables

## Quickstart (Local)
1. Copy backend/.env.example to backend/.env and fill values.
2. Install dependencies:
   ```
   cd backend
   npm install
   ```
3. Start server:
   ```
   npm start
   ```
4. Expose via ngrok for WhatsApp webhook:
   ```
   ngrok http 5000
   ```
5. In Meta Developer console, set webhook URL to:
   `https://<ngrok-id>.ngrok.io/webhook` and verify token.

## Deploy Options
- **Render / Railway**: Deploy `backend/` as a web service. Set env vars in dashboard.
- **Vercel**: Use `vercel/functions/` as serverless functions (update env in Vercel).
- **Netlify**: Host frontend and call backend URLs on Render/Railway.

## Notes
- Canva API request/response shapes may change — consult Canva docs and adjust `backend/canva.js`.
- Previews are watermarked and short-lived. Final high-res is delivered after payment.
- Replace in-memory or file stores with persistent DB (MongoDB is used in this package).

## Support
If you'd like, I can deploy this to Render and configure webhooks (Twilio/Razorpay/Canva) for you.
