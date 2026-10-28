# Import notes

Prepared on 2026-10-28 from the locally available `northstar-complete.zip` and made more self-contained for repository import.

## Important provenance limitation

This is **not a byte-for-byte export of the current published Lovable project**. The available source archive used an older React/Vite + Hono/tRPC/MySQL structure and lacked several files it imported. Missing modules and the base stylesheet have been added so this source package has a complete project shape, but it must be reviewed and verified against your intended production site before deployment.

## Secret handling

- Only `.env.example` is included.
- Real `.env` files, local environment files, and build outputs are ignored by Git.
- Do not paste production secrets into GitHub issues, commits, public logs, or chat.

## Known follow-up

Run `npm install`, `npm run check`, `npm test`, and `npm run build` locally. If you enable the contact form for public traffic, configure the database and rate-limit/proxy settings, then test end-to-end using a non-sensitive test enquiry.
