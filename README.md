

[Uploading frontend…]()# 9jadating (Starter)

Free-to-host, Nigeria-focused dating web app (location-based).

## Stack
- Frontend: Next.js (React), Leaflet (OpenStreetMap), socket.io-client
- Backend: Node.js, Express, MongoDB (Atlas), JWT auth, Socket.IO, Mongo geospatial queries
- Hosting: Vercel (frontend), Render or Railway (backend), MongoDB Atlas (DB)

## Quick Start (Local)
1) Backend
```bash
cd backend
cp .env.sample .env
# fill MONGODB_URI, JWT_SECRET, ALLOWED_ORIGINS
npm install
npm run dev
```
API default: http://localhost:5000

2) Frontend
```bash
cd frontend
cp .env.local.sample .env.local
# set NEXT_PUBLIC_API_URL (e.g., http://localhost:5000 or your Render URL)
npm install
npm run dev
```
Site: http://localhost:3000

## Free Deploy
### Database (MongoDB Atlas)
- Create free cluster, network access, DB user, copy connection string.

### Backend (Render/Railway)
- Connect your GitHub repo.
- Root Directory: `backend`
- Build: `npm install`
- Start: `npm start`
- Env Vars (from .env.sample):
  - PORT (Render provides one; your code respects it)
  - JWT_SECRET
  - MONGODB_URI
  - ALLOWED_ORIGINS (comma-separated frontend URLs)

### Frontend (Vercel)
- Connect same GitHub repo.
- Root Directory: `frontend`
- Env: `NEXT_PUBLIC_API_URL` = your backend URL
- Deploy to get `https://9jadating.vercel.app` (or similar)


[package.json](https://github.com/user-attachments/files/21966984/package.json)
{
  "name": "9jadating-backend",
  "version": "1.0.0",
  "main": "server.js",
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "express": "^4.18.2",
    "mongoose": "^7.5.0",
    "cors": "^2.8.5",
    "dotenv": "^16.3.1",
    "jsonwebtoken": "^9.0.1"
  }
}[server.js](https://github.com/user-attachments/files/21966985/server.js)
const express = require('express');
const mongoose = require('mongoose');
const cors = require('cors');
require('dotenv').config();

const app = express();
app.use(cors());
app.use(express.json());

app.get('/', (req, res) => res.send('9jadating backend is running'));

const PORT = process.env.PORT || 5000;
app.listen(PORT, () => console.log(`Server running on port ${PORT}`));
