# Bun + React (Vite) + Go + PostgreSQL baseplate

Starter monorepo for full-stack apps: **Bun** frontend (React 19, Vite, Tailwind CSS v4, shadcn/ui Base UI / Nova), **Go** API, and **PostgreSQL** via Docker Compose.

Use **Use this template** on GitHub to spin up a new project from this repo.

## Stack

| Layer | Tech |
| --- | --- |
| Frontend | Bun, React 19, Vite 8, TypeScript, Tailwind CSS v4, shadcn/ui, TanStack Query, React Router, Zustand, oxlint |
| Backend | Go 1.27+, pgx, sqlc (configured), godotenv |
| Database | PostgreSQL 17 (Docker) |

## Prerequisites

- [Bun](https://bun.sh)
- [Go](https://go.dev) 1.27+
- [Docker](https://www.docker.com/) (OrbStack, Docker Desktop, etc.)

## Quick start

### 1. Database

```bash
docker compose up -d
```

Postgres listens on `127.0.0.1:5432` with user/db `sprint` and password `sprint_dev` (see `docker-compose.yaml`).

### 2. Backend

```bash
cp backend/.env.example backend/.env
cd backend
go run ./cmd/api
```

API default port: `8080` (`PORT` in `.env`).

### 3. Frontend

```bash
cd frontend
bun install
bun run dev
```

Vite dev server: [http://localhost:5173](http://localhost:5173).

## Scripts (frontend)

| Command | Description |
| --- | --- |
| `bun run dev` | Vite dev server |
| `bun run build` | Production build |
| `bun run typecheck` | `tsc -b --noEmit` |
| `bun run lint` | oxlint (type-aware) |
| `bun run lint:fix` | oxlint with fixes |

## Project layout

```
.
├── backend/          # Go API (cmd/api)
├── frontend/         # Vite React app
│   └── src/components/ui/   # shadcn/ui components
├── docker-compose.yaml
└── README.md
```

## Path aliases (frontend)

- TypeScript: `@/*` → `frontend/src/*` (`tsconfig.json`, `tsconfig.app.json`)
- Vite / Vitest: `@` → `src/` (`vite.config.ts`)
- shadcn: see `frontend/components.json`

Add UI components:

```bash
cd frontend
bunx shadcn@latest add button
```

## License

MIT (add a `LICENSE` file if you need one for your fork).
