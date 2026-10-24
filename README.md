# VendorBridge — Foundation & Vendor Management

A full-stack vendor management starter project built with React, Vite, Node.js, Express, and MongoDB.

## Features
- JWT authentication (register/login)
- Role-aware users (`admin`, `vendor`)
- Vendor directory with search and status filtering
- Create, view, update, and delete vendor records
- Vendor approval workflow (`pending`, `approved`, `rejected`)
- Contract tracking (contract start/end dates)
- Dashboard statistics
- Responsive interface
- API validation and centralized error handling

> This is a portfolio/demo starter. Before production use, add rate limiting, email verification, password reset, audit logging, stronger authorization policies, automated tests, and deployment secrets management.

## Requirements
- Node.js 18+
- npm
- MongoDB local instance or MongoDB Atlas database

## 1. Configure the backend
```bash
cd backend
cp .env.example .env
npm install
```
Edit `backend/.env` and set `MONGO_URI` and a long random `JWT_SECRET`.

Start the API:
```bash
npm run dev
```
API runs at `http://localhost:5000`. Health check: `http://localhost:5000/api/health`.

## 2. Configure the frontend
Open a second terminal:
```bash
cd frontend
npm install
npm run dev
```
Open the Vite URL printed in the terminal (normally `http://localhost:5173`).

## 3. Create an account
Use the Register tab in the app. The first account is a normal user. To use admin-only approval/deletion actions, change a user's `role` to `admin` in MongoDB for your demo database. Never expose an admin-registration switch in a public deployment.

## API endpoints
Base URL: `/api`

| Method | Endpoint | Access | Purpose |
|---|---|---|---|
| GET | `/health` | Public | API health |
| POST | `/auth/register` | Public | Create account |
| POST | `/auth/login` | Public | Login |
| GET | `/auth/me` | Authenticated | Current user |
| GET | `/vendors` | Authenticated | List/search vendors |
| GET | `/vendors/:id` | Authenticated | Get vendor |
| POST | `/vendors` | Authenticated | Create vendor |
| PUT | `/vendors/:id` | Authenticated | Update vendor |
| PATCH | `/vendors/:id/status` | Admin | Approve/reject vendor |
| DELETE | `/vendors/:id` | Admin | Delete vendor |
| GET | `/dashboard/stats` | Authenticated | Dashboard totals |

## GitHub upload
1. Create a new empty repository on GitHub.
2. Extract this ZIP.
3. From the extracted `VendorBridge` folder run:
```bash
git init
git add .
git commit -m "Initial VendorBridge project"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
git push -u origin main
```
Replace the remote URL with your own repository URL. Do not commit `.env` files or real secrets.

## Project structure
```text
VendorBridge/
├── backend/
│   ├── config/db.js
│   ├── controllers/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   ├── .env.example
│   ├── package.json
│   └── server.js
└── frontend/
    ├── src/
    │   ├── components/
    │   ├── context/
    │   ├── pages/
    │   ├── services/
    │   ├── App.jsx
    │   ├── main.jsx
    │   └── styles.css
    ├── index.html
    └── package.json
```
