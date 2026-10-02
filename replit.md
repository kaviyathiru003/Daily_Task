# DAILY TASK

A local-first productivity app for planning tasks, focusing with a Pomodoro timer, and reviewing personal progress.

## Run & Operate

- `pnpm --filter @workspace/daily-task run dev` — run the DAILY TASK web app
- `pnpm --filter @workspace/daily-task run typecheck` — typecheck the web app
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

- `artifacts/daily-task/src/App.tsx` — routes, local state, account flow, tasks, and app screens
- `artifacts/daily-task/src/index.css` — app theme and responsive styles
- `artifacts/daily-task/index.html` — document title and social metadata

## Architecture decisions

- Accounts, sessions, tasks, and preferences stay in browser storage; there is no server auth or cross-device sync.
- Local account credentials are not suitable for sensitive or production authentication; use a real auth provider before treating accounts as secure.

## Product

DAILY TASK supports browser-local sign-up/sign-in, task CRUD, search/filter/sort, calendar planning, a Pomodoro timer, computed analytics, profile editing, settings, data export, and confirmed task-data clearing.

## User preferences

- Keep the visual direction minimal and premium, with mostly black-and-white UI, thin outlines, rounded cards, and generous whitespace.
- Keep the app responsive and accessible across desktop, tablet, and mobile.

## Gotchas

_Populate as you build — sharp edges, "always run X before Y" rules._

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
