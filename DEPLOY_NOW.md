# Doctor Appointment System - Deployment Guide

## Quick Deploy Options

### Option 1: Vercel (Frontend) + Render/Railway (Backend) - RECOMMENDED

#### Deploy Frontend to Vercel (Free)

1. **Install Vercel CLI:**
   ```bash
   npm install -g vercel
   ```

2. **Deploy:**
   ```bash
   cd client
   vercel
   ```

3. **Set Environment Variables in Vercel Dashboard:**
   - `REACT_APP_API_URL` = Your backend URL

#### Deploy Backend to Render (Free)

1. **Go to:** https://render.com
2. **Create New Web Service**
3. **Connect GitHub repository** (or upload code)
4. **Settings:**
   - Build Command: `npm install`
   - Start Command: `node server/server.js`
   - Environment Variables:
     - `MONGODB_URI` = Your MongoDB Atlas connection string
     - `JWT_SECRET` = Your secret key
     - `PORT` = 5000

---

### Option 2: Netlify (Frontend) + Railway (Backend)

#### Deploy Frontend to Netlify

1. **Go to:** https://netlify.com
2. **Drag and drop** the `client/build` folder after running `npm run build`
3. **Or connect GitHub** and set build command: `cd client && npm install && npm run build`

#### Deploy Backend to Railway

1. **Go to:** https://railway.app
2. **New Project** → **Deploy from GitHub**
3. **Add Environment Variables:**
   - `MONGODB_URI`
   - `JWT_SECRET`
   - `PORT`

---

### Option 3: Heroku (Both Frontend & Backend)

#### Deploy to Heroku

1. **Install Heroku CLI:**
   ```bash
   npm install -g heroku
   ```

2. **Login:**
   ```bash
   heroku login
   ```

3. **Create App:**
   ```bash
   heroku create doctor-appointment-api
   ```

4. **Set Environment Variables:**
   ```bash
   heroku config:set MONGODB_URI=your_mongodb_uri
   heroku config:set JWT_SECRET=your_secret_key
   heroku config:set NODE_ENV=production
   ```

5. **Deploy:**
   ```bash
   git push heroku main
   ```

---

## Step-by-Step: Deploy to Vercel + Render (Easiest)

### Part 1: Deploy Backend to Render

1. **Sign up:** https://render.com (free)

2. **Create MongoDB Atlas Database:**
   - Go to https://mongodb.com/cloud/atlas
   - Create free cluster (M0)
   - Get connection string
   - Add your IP to Network Access

3. **Create Web Service on Render:**
   - Click "New +" → "Web Service"
   - Connect your GitHub repo OR upload code
   - Settings:
     - **Name:** doctor-appointment-api
     - **Region:** Choose closest
     - **Branch:** main
     - **Root Directory:** (leave empty)
     - **Environment:** Node
     - **Build Command:** `npm install`
     - **Start Command:** `node server/server.js`
   
4. **Add Environment Variables:**
   - `MONGODB_URI` = Your Atlas connection string
   - `JWT_SECRET` = Random secret key (use `openssl rand -base64 32`)
   - `PORT` = 10000 (Render default)

5. **Click "Create Web Service"**

6. **Copy your backend URL** (e.g., `https://doctor-appointment-api.onrender.com`)

### Part 2: Deploy Frontend to Vercel

1. **Sign up:** https://vercel.com (free)

2. **Build Frontend:**
   ```bash
   cd client
   npm run build
   ```

3. **Deploy:**
   - Go to Vercel dashboard
   - Click "New Project"
   - Import your repository OR drag `client/build` folder
   - Settings:
     - **Framework Preset:** React
     - **Root Directory:** client
     - **Build Command:** `npm run build`
     - **Output Directory:** build

4. **Add Environment Variable:**
   - `REACT_APP_API_URL` = Your Render backend URL (e.g., `https://doctor-appointment-api.onrender.com`)

5. **Update API calls in client:**
   - Change `axios.get('/api/...')` to `axios.get(process.env.REACT_APP_API_URL + '/api/...')`

6. **Deploy!**

---

## Quick Fix: Update Client to Use Environment Variable

Update `client/src/context/AuthContext.js` and all API calls to use:

```javascript
const API_URL = process.env.REACT_APP_API_URL || 'http://localhost:5000';
axios.get(`${API_URL}/api/...`)
```

---

## Alternative: Single Platform Deployment

### Deploy Everything to Railway

1. **Go to:** https://railway.app
2. **New Project** → **Deploy from GitHub**
3. **Add MongoDB service** (Railway provides MongoDB)
4. **Add Web Service** for backend
5. **Add Static Site** for frontend build

---

## Post-Deployment

1. **Update CORS** in `server/server.js` to allow your frontend domain
2. **Test all endpoints**
3. **Create admin user** using the script
4. **Set up custom domain** (optional)

---

**Need help? Let me know which platform you want to use!**

