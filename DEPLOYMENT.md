# 🚀 TaskX Deployment Guide

## ✅ Pre-Deployment Checklist

Your app is ready! Here's what's been done:
- ✅ Multer security vulnerability fixed
- ✅ Production build configuration added
- ✅ Static file serving configured
- ✅ Deployment configs created (render.yaml, vercel.json)
- ✅ Code pushed to GitHub: https://github.com/Sumant3086/TaskX

## 🎯 Recommended: Deploy to Render

Render is best for your app because it fully supports WebSockets (Socket.io) for real-time features.

### Step-by-Step Render Deployment:

1. **Go to Render Dashboard**
   - Visit: https://render.com
   - Sign in with GitHub

2. **Create New Web Service**
   - Click "New +" button (top right)
   - Select "Web Service"

3. **Connect Repository**
   - Click "Connect account" if needed
   - Find and select: `Sumant3086/TaskX`
   - Click "Connect"

4. **Configure Service** (Render auto-detects render.yaml)
   - Name: `taskx` (or your choice)
   - Region: Choose closest to you
   - Branch: `main`
   - Build Command: `npm install && npm run build`
   - Start Command: `npm start`

5. **Add Environment Variables**
   Click "Advanced" → "Add Environment Variable":
   
   ```
   NODE_ENV = production
   MONGODB_URI = mongodb+srv://sumant:sumant123@taskmdb.kf0edjz.mongodb.net/?appName=TaskMDB
   JWT_SECRET = sumant_task_manager_jwt_secret_key_2024_secure
   CLIENT_URL = https://taskx.onrender.com
   ```
   
   **Important:** Replace `CLIENT_URL` with your actual Render URL after deployment

6. **Deploy**
   - Click "Create Web Service"
   - Wait 3-5 minutes for build
   - Your app will be live at: `https://taskx.onrender.com`

7. **Update CLIENT_URL**
   - After deployment, copy your Render URL
   - Go to Environment → Edit `CLIENT_URL`
   - Paste your URL (e.g., `https://taskx.onrender.com`)
   - Save changes (auto-redeploys)

### 🎉 Done! Your app is live!

---

## 🔷 Alternative: Deploy to Vercel

**Note:** Vercel has WebSocket limitations. Real-time features may not work fully.

### Step-by-Step Vercel Deployment:

1. **Go to Vercel Dashboard**
   - Visit: https://vercel.com
   - Sign in with GitHub

2. **Import Project**
   - Click "Add New..." → "Project"
   - Find and select: `Sumant3086/TaskX`
   - Click "Import"

3. **Configure Project** (Vercel auto-detects vercel.json)
   - Framework Preset: Other
   - Root Directory: `./`
   - Build Command: `npm run build`
   - Output Directory: `client/dist`

4. **Add Environment Variables**
   
   ```
   NODE_ENV = production
   MONGODB_URI = mongodb+srv://sumant:sumant123@taskmdb.kf0edjz.mongodb.net/?appName=TaskMDB
   JWT_SECRET = sumant_task_manager_jwt_secret_key_2024_secure
   CLIENT_URL = https://taskx.vercel.app
   ```

5. **Deploy**
   - Click "Deploy"
   - Wait 2-3 minutes
   - Your app will be live at: `https://taskx.vercel.app`

---

## 🔧 Post-Deployment

### Test Your Deployment:

1. **Visit your live URL**
2. **Register a new account**
3. **Create a task**
4. **Test real-time updates** (open in 2 tabs)

### Load Demo Data:

```bash
# Replace with your deployed URL
curl -X POST https://taskx.onrender.com/api/seed/demo-data
```

Or visit in browser:
```
https://taskx.onrender.com/api/seed/demo-data
```

Demo accounts:
- Admin: priya.sharma@taskx.com / demo123
- Manager: rahul.verma@taskx.com / demo123
- User: ananya.patel@taskx.com / demo123

---

## 🐛 Troubleshooting

### Build Fails
- Check environment variables are set correctly
- Verify MongoDB URI is accessible
- Check build logs for specific errors

### App Crashes
- Ensure `NODE_ENV=production` is set
- Verify MongoDB connection string
- Check server logs in Render/Vercel dashboard

### Real-time Features Not Working
- Use Render instead of Vercel
- Check Socket.io CORS settings
- Verify CLIENT_URL matches your deployment URL

---

## 📊 Monitor Your App

### Render:
- Dashboard → Your Service → Logs
- View real-time logs and metrics

### Vercel:
- Dashboard → Your Project → Deployments
- Click deployment → View Function Logs

---

## 🔄 Update Deployment

Any push to `main` branch auto-deploys:

```bash
git add .
git commit -m "Your update message"
git push origin main
```

Both Render and Vercel will automatically rebuild and redeploy.

---

**Need help?** Contact: sumantyadav3086@gmail.com
