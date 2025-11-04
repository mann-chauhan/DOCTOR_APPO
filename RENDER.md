# Render.com Deployment Guide

## Quick Deploy to Render (Backend)

1. **Go to:** https://render.com
2. **Sign up** (free account)
3. **Click "New +" → "Web Service"**
4. **Connect your GitHub repository** (or upload code)
5. **Settings:**
   - **Name:** doctor-appointment-api
   - **Environment:** Node
   - **Region:** Choose closest to you
   - **Branch:** main
   - **Root Directory:** (leave empty)
   - **Build Command:** `npm install`
   - **Start Command:** `node server/server.js`

6. **Add Environment Variables:**
   - `MONGODB_URI` = Your MongoDB Atlas connection string
   - `JWT_SECRET` = Generate with: `openssl rand -base64 32`
   - `PORT` = 10000
   - `NODE_ENV` = production
   - `FRONTEND_URL` = Your frontend URL (after deploying)

7. **Click "Create Web Service"**

**Your backend will be live at:** `https://doctor-appointment-api.onrender.com`

---

## MongoDB Atlas Setup (Free)

1. Go to https://mongodb.com/cloud/atlas
2. Create free account
3. Create free cluster (M0)
4. Click "Connect" → "Connect your application"
5. Copy connection string
6. Replace `<password>` with your database password
7. Add your IP to Network Access (or use 0.0.0.0/0 for all IPs)

---

## Next: Deploy Frontend

After backend is deployed, deploy frontend to Vercel (see VERCEL.md)

