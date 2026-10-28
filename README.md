# Northstar Student Studio

A responsive student portfolio and small-business web-studio site. The site keeps two things clear: Mohammad Taufeeq's learning/projects, and Northstar Growth Studio's practical web and digital-presence services.

> **Source note:** This repository package was assembled from the `northstar-complete.zip` source archive available in this conversation and completed where files referenced by that archive were missing. It is a standalone source package, **not a byte-for-byte export of the currently published Lovable project**. Review branding, copy, and environment settings before deploying it as your production site.

## Included pages

- `/` — home
- `/about` — about and working principles
- `/projects` — student projects and learning work
- `/lab` — current practice and experiments
- `/insights` — notes placeholder
- `/studio` and `/services` — business services (`/services` redirects)
- `/contact` — contact form
- `/privacy` — privacy overview
- Unknown paths show a 404 page

## Stack

React 19, TypeScript, Vite, React Router, Hono, tRPC, Drizzle ORM, MySQL/MariaDB, and Zod.

## Run locally

Requirements: Node.js 20.19+ (Node.js 22 recommended) and npm.

```bash
cp .env.example .env
npm install
npm run dev
```

Open `http://localhost:3000`. The public pages can be viewed without a live database; for a working contact form, configure a MySQL/MariaDB database and the environment variables described below.

## Environment variables

- `DATABASE_URL` — MySQL/MariaDB connection string.
- `CONTACT_HASH_SECRET` — use a unique random secret with at least 32 characters in production. Generate one with `node -e "console.log(require('crypto').randomBytes(48).toString('hex'))"`.
- `TRUST_PROXY_HOPS` — number of trusted reverse proxies; set this to match your hosting environment.
- `RESEND_API_KEY`, `CONTACT_TO_EMAIL`, `CONTACT_FROM_EMAIL` — optional email notification settings. Without these, form entries can still be saved if the database is configured, but notification delivery is disabled.
- `VITE_SITE_URL` — public site origin, used at build time for canonical metadata, sitemap and robots files.

**Never commit `.env`, private keys, database credentials, API tokens, or production secrets.** Only `.env.example` belongs in Git. The `.gitignore` already excludes `.env*` while allowing `.env.example`.

## Checks and build

```bash
npm run check
npm test
npm run build
```

The project includes contact-validation and security-focused tests. Verify the output in your own environment before deployment, and review current dependency advisories with `npm audit`.

## Production build

```bash
npm run build
npm start
```

The HTTP server listens on `PORT` (default `3000`). Configure the hosting platform's environment settings rather than storing secrets in source control. The `Dockerfile` builds the frontend and server bundle in a separate stage.

## Before public launch

1. Confirm the website's name, copy, contact destination, and GitHub link.
2. Create and configure the production database if the contact form is required.
3. Set `NODE_ENV=production`, `DATABASE_URL`, `CONTACT_HASH_SECRET`, and `TRUST_PROXY_HOPS` in the host's secret/environment panel.
4. Set `VITE_SITE_URL` to the actual public domain at build time.
5. Run the checks above and submit a real test enquiry; confirm both persistence and notification behaviour.
6. Review the privacy notice against the actual hosting, retention and email practices.

## License

No open-source license is included. Add one only if you want to grant other people explicit reuse rights.
