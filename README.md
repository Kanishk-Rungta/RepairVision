# Repair Cafe Hub

A repair cafe management application with a public website, QR check-in,
volunteer repair queues, session scheduling, reports and an admin dashboard.

## Stack

- SvelteKit and Tailwind CSS
- Cloudflare Workers, D1 and R2
- Drizzle ORM and shared TypeScript validation
- Vitest

## Development

Requires Node.js 22 or newer and pnpm (the version is specified in package.json).

```sh
pnpm install
pnpm cf:dev       # Worker and local database at http://localhost:8787
pnpm dev:web      # Frontend development server
pnpm build
pnpm cf:test
```

## Deployment

Configure your own Cloudflare resources and domain.

```sh
pnpm --filter @circularity/cloudflare exec wrangler login
pnpm cf:deploy --domain repair.example.org
```

Telemetry is off until you configure
TELEMETRY_ENDPOINT and explicitly enable sharing in the application.

## Layout

- apps/web: website and admin interface
- apps/cloudflare: Worker, API, database and scheduled jobs
- packages/shared: types, validation and backup format
- demo: optional sample data
