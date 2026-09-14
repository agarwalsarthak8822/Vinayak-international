# GuideLocks Security Solutions

Premium product catalog and enquiry website for Vinayak International, showcasing security hardware and door-furniture solutions.

## Run & Operate

- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- Required env: `DATABASE_URL` — Postgres connection string

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- API: Express 5
- DB: PostgreSQL + Drizzle ORM
- Validation: Zod (`zod/v4`), `drizzle-zod`
- API codegen: Orval (from OpenAPI spec)
- Build: esbuild (CJS bundle)

## Where things live

- `artifacts/guidelocks/` — Vite/React catalog frontend and static assets
- `artifacts/api-server/` — Express API, currently including `/api/healthz`
- `lib/api-spec/` — OpenAPI source and code generation
- `lib/api-zod/` — generated request/response schemas
- `lib/db/` — Drizzle/PostgreSQL database package and schema
- `artifacts/guidelocks/src/data/products.ts` — product catalog source data
- `artifacts/guidelocks/src/index.css` — theme tokens and global styles

## Architecture decisions

_Populate as you build — non-obvious choices a reader couldn't infer from the code (3-5 bullets)._

## Product

Browse security products by category, view product details, request a quote, open the product catalog PDF, and contact Vinayak International through WhatsApp, email, phone, and social links.

## User preferences

_Populate as you build — explicit user instructions worth remembering across sessions._

## Gotchas

- Run the frontend through the managed `artifacts/guidelocks: web` workflow so Replit supplies `PORT` and `BASE_PATH`.
- Run the API through the managed `artifacts/api-server: API Server` workflow; its health check is available at `/api/healthz`.
- `DATABASE_URL` is not provisioned in the current environment, so database-backed API features will require a database before use.

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
