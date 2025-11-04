# Vercel Deployment Guide

## Deploy Frontend to Vercel (Free)

### Method 1: Via Vercel Dashboard (Easiest)

1. **Go to:** https://vercel.com
2. **Sign up/Login** (use GitHub)
3. **Click "New Project"**
4. **Import your GitHub repository**
5. **Project Settings:**
   - **Framework Preset:** React
   - **Root Directory:** `client`
   - **Build Command:** `npm run build`
   - **Output Directory:** `build`
   - **Install Command:** `npm install`

6. **Environment Variables:**
   - `REACT_APP_API_URL` = Your Render backend URL
     - Example: `https://doctor-appointment-api.onrender.com`

7. **Click "Deploy"**

**Your app will be live at:** `https://your-project.vercel.app`

---

### Method 2: Via Vercel CLI

```bash
# Install Vercel CLI
npm install -g vercel

# Deploy
cd client
vercel

# Follow prompts
# Set REACT_APP_API_URL when asked
```

---

## Update Your Code

Make sure your frontend uses the API URL from environment variable (already done in AuthContext.js)

---

## Custom Domain (Optional)

1. Go to Vercel project settings
2. Click "Domains"
3. Add your domain
4. Update DNS records as instructed

