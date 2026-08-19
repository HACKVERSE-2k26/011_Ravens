

# Smart Blood Donor Discovery & Emergency Blood Request Management Platform

## Problem Statement 
BloodBridge is a smart blood donation and emergency blood request management platform that connects blood donors, patients, hospitals, blood banks, and ambulances through a centralized real-time system. It intelligently identifies and prioritizes eligible, available, and nearby blood donors based on blood-group compatibility, location, availability, donation history, and emergency priority. The platform enables hospitals to create urgent blood requests, donors to receive and respond to alerts, and administrators to monitor the complete emergency workflow. It also supports real-time tracking, family member management, email notifications, automated workflows, and future AI/n8n voice-agent integration, helping reduce the time required to find compatible blood during critical situations.

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
