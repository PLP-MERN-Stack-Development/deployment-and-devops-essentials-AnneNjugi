# 🚀 Deployment Guide - Real-Time Chat Application

This guide walks you through deploying the MERN stack chat application to production.

## 📋 Prerequisites

Before deploying, ensure you have accounts on:
- [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) (Database)
- [Render](https://render.com) or [Railway](https://railway.app) (Backend hosting)
- [Vercel](https://vercel.com) or [Netlify](https://netlify.com) (Frontend hosting)
- [GitHub](https://github.com) (Source control & CI/CD)

## 🗄️ Step 1: Set Up MongoDB Atlas

1. **Create a MongoDB Atlas Account**
   - Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
   - Sign up for a free account

2. **Create a Cluster**
   - Click "Build a Database"
   - Choose the FREE tier (M0)
   - Select a cloud provider and region close to your users
   - Click "Create Cluster"

3. **Configure Database Access**
   - Go to "Database Access" in the left sidebar
   - Click "Add New Database User"
   - Create a username and strong password (save these!)
   - Set privileges to "Read and write to any database"

4. **Configure Network Access**
   - Go to "Network Access" in the left sidebar
   - Click "Add IP Address"
   - Click "Allow Access from Anywhere" (0.0.0.0/0) for production
   - Click "Confirm"

5. **Get Connection String**
   - Go to "Database" and click "Connect"
   - Choose "Connect your application"
   - Copy the connection string
   - Replace `<password>` with your database user password
   - Replace `<dbname>` with `chatapp`
   - Save this connection string for later

## 🖥️ Step 2: Deploy Backend to Render

1. **Push Code to GitHub**
   ```bash
   git add .
   git commit -m "Prepare for deployment"
   git push origin main
   ```

2. **Create Render Account**
   - Go to [Render](https://render.com)
   - Sign up and connect your GitHub account

3. **Create New Web Service**
   - Click "New +" → "Web Service"
   - Connect your GitHub repository
   - Configure the service:
     - **Name**: `chat-app-backend`
     - **Region**: Choose closest to your users
     - **Branch**: `main`
     - **Root Directory**: `server`
     - **Runtime**: `Node`
     - **Build Command**: `npm install`
     - **Start Command**: `npm start`
     - **Plan**: Free

4. **Add Environment Variables**
   Click "Advanced" and add:
   - `NODE_ENV` = `production`
   - `PORT` = `10000`
   - `MONGODB_URI` = (paste your MongoDB connection string)
   - `CLIENT_URL` = (leave empty for now, will update after frontend deployment)

5. **Deploy**
   - Click "Create Web Service"
   - Wait for deployment to complete
   - Copy your backend URL (e.g., `https://chat-app-backend.onrender.com`)

## 🌐 Step 3: Deploy Frontend to Vercel

1. **Create Vercel Account**
   - Go to [Vercel](https://vercel.com)
   - Sign up and connect your GitHub account

2. **Import Project**
   - Click "Add New" → "Project"
   - Import your GitHub repository
   - Configure:
     - **Framework Preset**: Vite
     - **Root Directory**: `client`
     - **Build Command**: `npm run build`
     - **Output Directory**: `dist`

3. **Add Environment Variables**
   - Click "Environment Variables"
   - Add: `VITE_SOCKET_URL` = (your Render backend URL)
   - Example: `https://chat-app-backend.onrender.com`

4. **Deploy**
   - Click "Deploy"
   - Wait for deployment to complete
   - Copy your frontend URL (e.g., `https://chat-app.vercel.app`)

## 🔄 Step 4: Update Backend CORS

1. **Go back to Render Dashboard**
2. **Update Environment Variables**
   - Find `CLIENT_URL` variable
   - Set it to your Vercel frontend URL
   - Save changes
3. **Redeploy** (Render will auto-redeploy)

## ✅ Step 5: Test Your Deployment

1. Open your frontend URL in a browser
2. Create a username and join the chat
3. Open another browser/incognito window
4. Test sending messages between users
5. Verify real-time updates work

## 🔧 Step 6: Set Up CI/CD (Already Configured!)

The GitHub Actions workflow is already set up in `.github/workflows/ci-cd.yml`

**What it does:**
- Runs on every push to main branch
- Tests backend code
- Builds frontend
- Notifies if deployment is ready

**To enable:**
1. Push your code to GitHub
2. Go to your repository → "Actions" tab
3. Workflows will run automatically

## 📊 Step 7: Set Up Monitoring

### Health Check Endpoint
Your backend has a health check at `/health`
- Test it: `https://your-backend-url.com/health`

### Render Monitoring (Built-in)
- Go to your Render dashboard
- Click on your service
- View metrics: CPU, Memory, Response times

### UptimeRobot (Free External Monitoring)
1. Sign up at [UptimeRobot](https://uptimerobot.com)
2. Add new monitor:
   - **Type**: HTTP(s)
   - **URL**: Your backend `/health` endpoint
   - **Interval**: 5 minutes
3. Get alerts via email when your app goes down

## 🔐 Security Checklist

- ✅ HTTPS enabled (automatic on Render/Vercel)
- ✅ Helmet.js configured for security headers
- ✅ CORS properly configured
- ✅ MongoDB credentials secured in environment variables
- ✅ No sensitive data in code
- ✅ Rate limiting (consider adding for production)

## 🐛 Troubleshooting

### Backend won't start
- Check Render logs for errors
- Verify MongoDB connection string is correct
- Ensure all environment variables are set

### Frontend can't connect to backend
- Verify `VITE_SOCKET_URL` is correct
- Check CORS settings on backend
- Ensure backend is running (check health endpoint)

### Messages not persisting
- Verify MongoDB connection is successful
- Check backend logs for database errors

## 📝 Deployment URLs

After deployment, update this README with your URLs:

- **Frontend**: `https://your-app.vercel.app`
- **Backend**: `https://your-backend.onrender.com`
- **Health Check**: `https://your-backend.onrender.com/health`

## 🎉 You're Done!

Your chat application is now live and accessible to anyone on the internet!

### Next Steps:
- Share your app URL with friends
- Monitor performance and errors
- Add custom domain (optional)
- Implement additional features
