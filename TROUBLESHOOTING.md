# 🔧 Troubleshooting Guide

Common issues and their solutions when deploying the chat application.

## 🚫 Common Issues

### 1. Backend Won't Start on Render

**Symptoms:**
- Service shows "Deploy failed"
- Logs show "Cannot find module" errors
- Application crashes on startup

**Solutions:**

✅ **Check package.json location**
```bash
# Ensure render.yaml points to correct directory
buildCommand: cd server && npm install
startCommand: cd server && npm start
```

✅ **Verify all dependencies are listed**
```bash
cd server
npm install
# Check if any missing dependencies
```

✅ **Check Node.js version**
```json
// Add to server/package.json
"engines": {
  "node": ">=18.0.0"
}
```

✅ **Review Render logs**
- Go to Render dashboard
- Click on your service
- Check "Logs" tab for specific errors

### 2. MongoDB Connection Failed

**Symptoms:**
- "MongooseServerSelectionError"
- "ECONNREFUSED" errors
- Health check shows "mongodb: disconnected"

**Solutions:**

✅ **Verify connection string**
```bash
# Check MONGODB_URI format:
mongodb+srv://username:password@cluster.mongodb.net/chatapp?retryWrites=true&w=majority
```

✅ **Check MongoDB Atlas network access**
- Go to MongoDB Atlas dashboard
- Network Access → Add IP Address
- Use 0.0.0.0/0 for production (allow all)

✅ **Verify database user credentials**
- Database Access → Check username exists
- Reset password if needed
- Ensure user has read/write permissions

✅ **Test connection locally first**
```bash
cd server
# Add MONGODB_URI to .env
npm start
# Check if connection succeeds
```

### 3. Frontend Can't Connect to Backend

**Symptoms:**
- "Failed to load resource" errors
- Socket.io connection errors
- CORS errors in browser console

**Solutions:**

✅ **Verify VITE_SOCKET_URL**
```bash
# In client/.env (local)
VITE_SOCKET_URL=http://localhost:5000

# In Vercel environment variables (production)
VITE_SOCKET_URL=https://your-backend.onrender.com
```

✅ **Check backend CORS configuration**
```javascript
// server/server.js should have:
cors: {
  origin: process.env.CLIENT_URL,
  methods: ['GET', 'POST'],
  credentials: true,
}
```

✅ **Update CLIENT_URL on Render**
- Go to Render dashboard
- Environment variables
- Set CLIENT_URL to your Vercel URL
- Save and redeploy

✅ **Check if backend is running**
```bash
# Test health endpoint
curl https://your-backend.onrender.com/health
```

### 4. Vercel Build Fails

**Symptoms:**
- "Build failed" message
- "Module not found" errors
- Build timeout

**Solutions:**

✅ **Check build command**
```json
// client/package.json
"scripts": {
  "build": "vite build"
}
```

✅ **Verify all dependencies installed**
```bash
cd client
npm install
npm run build
# Test build locally first
```

✅ **Check environment variables**
- Vercel dashboard → Project → Settings → Environment Variables
- Ensure VITE_SOCKET_URL is set
- Redeploy after adding variables

✅ **Clear Vercel cache**
- Vercel dashboard → Deployments
- Click "..." → "Redeploy"
- Check "Clear cache and redeploy"

### 5. GitHub Actions Workflow Fails

**Symptoms:**
- Red X on commits
- Workflow shows failed status
- Build or test errors

**Solutions:**

✅ **Check workflow file syntax**
```bash
# Validate YAML syntax
# Use online YAML validator
```

✅ **Review workflow logs**
- GitHub repository → Actions tab
- Click on failed workflow
- Review error messages

✅ **Fix common issues**
```yaml
# Ensure correct Node version
- uses: actions/setup-node@v3
  with:
    node-version: '18'

# Ensure correct working directory
working-directory: ./server
```

✅ **Test locally before pushing**
```bash
cd server
npm ci
node -c server.js

cd ../client
npm ci
npm run build
```

### 6. Application Loads but Features Don't Work

**Symptoms:**
- Can't send messages
- Real-time updates not working
- Features work locally but not in production

**Solutions:**

✅ **Check browser console for errors**
- Press F12 → Console tab
- Look for JavaScript errors
- Check Network tab for failed requests

✅ **Verify Socket.io connection**
```javascript
// In browser console
// Should see Socket.io connection logs
```

✅ **Check backend logs**
- Render dashboard → Logs
- Look for Socket.io connection messages
- Check for errors

✅ **Verify environment variables**
- Frontend: VITE_SOCKET_URL set correctly
- Backend: CLIENT_URL set correctly
- Both should use HTTPS in production

### 7. Slow Performance

**Symptoms:**
- Messages take long to send
- Page loads slowly
- Laggy interface

**Solutions:**

✅ **Check Render free tier limitations**
- Free tier spins down after inactivity
- First request after idle takes 30-60 seconds
- Consider upgrading for better performance

✅ **Optimize frontend build**
```bash
cd client
npm run build
# Check dist/ folder size
# Should be < 5MB
```

✅ **Check MongoDB Atlas region**
- Use region close to Render server
- Check connection latency

✅ **Monitor resource usage**
- Render dashboard → Metrics
- Check CPU and memory usage
- Optimize if needed

### 8. Health Check Fails

**Symptoms:**
- `/health` endpoint returns error
- UptimeRobot shows down
- Monitoring alerts triggered

**Solutions:**

✅ **Test health endpoint directly**
```bash
curl https://your-backend.onrender.com/health
```

✅ **Check MongoDB connection**
```javascript
// Health check depends on MongoDB
// Verify MongoDB is accessible
```

✅ **Review server logs**
- Check for startup errors
- Verify all services initialized

✅ **Restart service**
- Render dashboard → Manual Deploy
- Or push a commit to trigger redeploy

## 🆘 Getting Help

### Before Asking for Help

1. **Check logs**
   - Render logs (backend)
   - Browser console (frontend)
   - MongoDB Atlas logs

2. **Verify environment variables**
   - All required variables set
   - No typos in URLs
   - Correct format

3. **Test locally**
   - Does it work on localhost?
   - Isolate the issue

4. **Review documentation**
   - DEPLOYMENT_GUIDE.md
   - Platform documentation

### Where to Get Help

- **Render Support**: https://render.com/docs
- **Vercel Support**: https://vercel.com/docs
- **MongoDB Atlas**: https://docs.atlas.mongodb.com/
- **Stack Overflow**: Tag with specific technology
- **GitHub Issues**: Check if others have same issue

## 📝 Debugging Checklist

When something goes wrong:

- [ ] Check all logs (backend, frontend, database)
- [ ] Verify all environment variables
- [ ] Test health endpoint
- [ ] Check CORS configuration
- [ ] Verify MongoDB connection
- [ ] Test locally to isolate issue
- [ ] Check platform status pages
- [ ] Review recent code changes
- [ ] Clear caches and redeploy
- [ ] Check network connectivity

## 🔍 Useful Commands

### Test Backend Locally
```bash
cd server
npm install
npm start
```

### Test Frontend Locally
```bash
cd client
npm install
npm run dev
```

### Test Production Build Locally
```bash
cd client
npm run build
npm run preview
```

### Check MongoDB Connection
```bash
# In server directory with .env configured
node -e "require('dotenv').config(); const mongoose = require('mongoose'); mongoose.connect(process.env.MONGODB_URI).then(() => console.log('Connected!')).catch(err => console.error(err));"
```

### Test Health Endpoint
```bash
curl https://your-backend.onrender.com/health
```

### View Render Logs (CLI)
```bash
render logs -s your-service-name
```

## 💡 Pro Tips

1. **Always test locally first** before deploying
2. **Use environment variables** for all configuration
3. **Check logs immediately** after deployment
4. **Monitor health endpoint** regularly
5. **Keep dependencies updated** but test before deploying
6. **Document any custom solutions** you find
7. **Use version control** - commit working code frequently

## 🎯 Prevention

Avoid issues by:
- Testing thoroughly before deployment
- Using `.env.example` files
- Documenting configuration
- Monitoring application health
- Keeping dependencies updated
- Following security best practices
- Regular backups of database

---

**Still having issues?** Review the [DEPLOYMENT_GUIDE.md](./DEPLOYMENT_GUIDE.md) for step-by-step instructions.
