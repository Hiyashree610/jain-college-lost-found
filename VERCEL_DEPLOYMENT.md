# Vercel deployment

Live: https://jain-campusfind.vercel.app

The Vercel frontend is in `vercel-app`. Build: `npm run build`; output: `dist`; install: `npm install`; Node 24. API requests are proxied to the original Cloudflare/Sites backend, preserving the existing database and photo storage. Keep the original site published. Browser-local report management tokens do not transfer between addresses.
