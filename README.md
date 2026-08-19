

# Smart Blood Donor Discovery & Emergency Blood Request Management Platform

## Problem Statement 
BloodBridge is a smart blood donation and emergency blood request management platform that connects blood donors, patients, hospitals, blood banks, and ambulances through a centralized real-time system. It intelligently identifies and prioritizes eligible, available, and nearby blood donors based on blood-group compatibility, location, availability, donation history, and emergency priority. The platform enables hospitals to create urgent blood requests, donors to receive and respond to alerts, and administrators to monitor the complete emergency workflow. It also supports real-time tracking, family member management, email notifications, automated workflows, and future AI/n8n voice-agent integration, helping reduce the time required to find compatible blood during critical situations.

## Proposed Solution
BloodBridge proposes a centralized, real-time digital platform that connects blood donors, patients, hospitals, blood banks, and ambulance services to streamline emergency blood discovery and management.

The platform uses a smart donor-matching system to identify and prioritize eligible donors based on blood-group compatibility, availability, location, donation history, reliability, and emergency priority. Hospitals can create and track blood requests, while compatible donors receive real-time notifications and can accept or decline requests.

The solution also provides blood-bank inventory management, emergency SOS requests, family member management with email confirmation, request tracking, admin monitoring, and automated workflows using n8n and AI voice-agent integration. This creates a coordinated end-to-end emergency workflow that can reduce delays in finding compatible blood and improve emergency response efficiency.

> Backend-first prototype. See `docs/ARCHITECTURE.md` for phase-by-phase
> status — this is being built incrementally, not all at once.

## Technologies Used

- **Backend:** Node.js, Express, TypeScript, MySQL (`mysql2`), Socket.IO (Phase 9), JWT auth
- **Frontend:** React + Vite + Tailwind (Phase 15, not started)
- **Database:** MySQL — full schema in `database/schema.sql`

## System Architecture

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
## Features
1.User Registration & Secure Login – JWT-based authentication with secure password hashing.
2.Smart Donor Discovery – Finds compatible donors based on blood group, location, availability, eligibility, and donation history.
3.Real-Time Donor Sorting – Prioritizes donors who are currently willing and ready to donate.
4.Emergency Blood Requests – Hospitals can create Critical, Urgent, or Normal blood requests.
5.Emergency SOS – Quickly initiate a high-priority blood request during emergencies.
6.Hospital Management – Manage patients, blood requests, donor responses, and request status.
7.Blood Bank Management – Track blood-group inventory, available units, and emergency requirements.
8.Ambulance Integration – Connect emergency incidents and preliminary patient requirements with hospitals.
9.Real-Time Notifications – Notify eligible donors about urgent blood requirements.
10.Donor Accept/Decline – Donors can respond to requests and update their availability.

## Installation


Make sure the following are installed:

Node.js v18 or above
MySQL Server
Git
Visual Studio Code
1. Clone the Repository

```
clone https://github.com/your-team/BloodBridge.git
cd BloodBridge 
```

3. Install Frontend Dependencies
```
cd frontend
npm install
```
5. Install Backend Dependencies
```
cd ../backend
npm install
```
7. Configure Environment Variables

Create a .env file inside the backend folder:

```
PORT=5000


DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=bloodbridge


JWT_SECRET=your_jwt_secret


FRONTEND_URL=http://localhost:5173
```
Note: Never commit your .env file or database credentials to GitHub.

5. Set Up the Database

Create the MySQL database:
```
CREATE DATABASE bloodbridge;
```
Configure the database credentials in the backend .env file.

6. Start the Backend

Open a terminal:
```
cd backend
npm run dev
```
The backend will run on:
```
http://localhost:5000
```
7. Start the Frontend

Open another terminal:
```
cd frontend
npm run dev
```
The frontend will run on:
```
http://localhost:5173
```
8. Open the Application

Visit:
```
http://localhost:5173
```
The BloodBridge – Smart Blood Donor Discovery & Emergency Blood Request Management Platform is now ready for development and testing.



## How to run

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

## Demo
Live URL:https://bloodbridge.ai.studio/<br>

Demo Video:https://drive.google.com/file/d/1ytkBcrBqQMq4Nfx1BSiXcZeE_tEJm96H/view?usp=sharing<br>

## Deployment


BloodBridge was built completely from scratch using Visual Studio Code, with separate frontend and backend components.



The frontend was developed using React.js, Vite, JavaScript, HTML, CSS, and Tailwind CSS. The backend was developed using Node.js and Express.js, with MySQL used for data storage and REST APIs used for communication between the frontend and backend.
```
VS Code
   │
   ├── Frontend
   │   └── React + Vite
   │
   ├── Backend
   │   └── Node.js + Express
   │
   └── Database
       └── MySQL
```

## Screenshots

## What's built so far

- Full 23-table MySQL schema (users through audit_logs — see `docs/ARCHITECTURE.md` for the full table)
- Backend project scaffold with the folder structure specified for the whole project
- Working `register` / `login` against real MySQL, with bcrypt password hashing and JWT issuance
- Centralized blood compatibility service (single source of truth for all future matching logic)
- Consistent error format, global error handler, auth + role middleware, zod validation

## Future Enhancements

See **"Next recommended phase"** in `docs/ARCHITECTURE.md`. Short version:
family-member invitation flow (register → invite → email → accept → verified)
is the natural next step, since it's fully specified and self-contained.

## This is a prototype

BloodBridge coordinates resources; it does not make clinical decisions.
Blood compatibility/eligibility rules here should be verified against
appropriate medical guidance before any real-world deployment.
