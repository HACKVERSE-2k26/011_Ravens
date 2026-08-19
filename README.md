# BloodBridge

**Smart Blood Donor Discovery & Emergency Blood Request Management Platform**

> Backend-first prototype. See `docs/ARCHITECTURE.md` for phase-by-phase
> status — this is being built incrementally, not all at once.

## Stack

- **Backend:** Node.js, Express, TypeScript, MySQL (`mysql2`), Socket.IO (Phase 9), JWT auth
- **Frontend:** React + Vite + Tailwind (Phase 15, not started)
- **Database:** MySQL — full schema in `database/schema.sql`

## Project structure

```
bloodbridge/
├── backend/          Express API (TypeScript)
├── frontend/          React app (scaffolded, empty — Phase 15)
├── database/
│   └── schema.sql     Full normalized schema — run this first
├── n8n/workflows/     Future n8n workflow exports
└── docs/
    └── ARCHITECTURE.md  Phase status + what's real vs. stubbed
```

## Getting started (backend)

1. Create a MySQL database and load the schema:
   ```bash
   mysql -u root -p -e "CREATE DATABASE bloodbridge"
   mysql -u root -p bloodbridge < database/schema.sql
   ```
2. Copy the env template and fill in your DB credentials:
   ```bash
   cp .env.example backend/.env
   ```
3. Install and run:
   ```bash
   cd backend
   npm install
   npm run dev
   ```
4. Health check: `GET http://localhost:4000/health`

## Try the auth endpoints

```bash
curl -X POST http://localhost:4000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"fullName":"Test User","email":"test@example.com","phone":"9876543210","password":"password123"}'

curl -X POST http://localhost:4000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"test@example.com","password":"password123"}'
```

## What's built so far

- Full 23-table MySQL schema (users through audit_logs — see `docs/ARCHITECTURE.md` for the full table)
- Backend project scaffold with the folder structure specified for the whole project
- Working `register` / `login` against real MySQL, with bcrypt password hashing and JWT issuance
- Centralized blood compatibility service (single source of truth for all future matching logic)
- Consistent error format, global error handler, auth + role middleware, zod validation

## What's next

See **"Next recommended phase"** in `docs/ARCHITECTURE.md`. Short version:
family-member invitation flow (register → invite → email → accept → verified)
is the natural next step, since it's fully specified and self-contained.

## This is a prototype

BloodBridge coordinates resources; it does not make clinical decisions.
Blood compatibility/eligibility rules here should be verified against
appropriate medical guidance before any real-world deployment.
