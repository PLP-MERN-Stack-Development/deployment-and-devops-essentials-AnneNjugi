# ✅ Deployment Checklist

Use this checklist to ensure you complete all deployment steps correctly.

## 📋 Pre-Deployment

### Code Preparation
- [ ] All code committed to GitHub
- [ ] No sensitive data in code (passwords, API keys)
- [ ] `.env.example` files created for both client and server
- [ ] `.gitignore` properly configured
- [ ] Dependencies up to date

### Testing
- [ ] Application runs locally without errors
- [ ] All features tested locally
- [ ] Health check endpoint works (`/health`)
- [ ] Environment variables tested

## 🗄️ MongoDB Atlas Setup

- [ ] MongoDB Atlas account created
- [ ] Free tier cluster created
- [ ] Database user created with strong password
- [ ] Network access configured (0.0.0.0/0 for production)
- [ ] Connection string obtained
- [ ] Connection string tested locally

## 🖥️ Backend Deployment (Render)

### Account Setup
- [ ] Render account created
- [ ] GitHub account connected to Render

### Service Configuration
- [ ] New Web Service created
- [ ] GitHub repository connected
- [ ] Service name set: `chat-app-backend`
- [ ] Root directory set to: `server`
- [ ] Build command: `npm install`
- [ ] Start command: `npm start`
- [ ] Free plan selected

### Environment Variables
- [ ] `NODE_ENV` = `production`
- [ ] `PORT` = `10000`
- [ ] `MONGODB_URI` = [your MongoDB connection string]
- [ ] `CLIENT_URL` = [will update after frontend deployment]

### Deployment
- [ ] Service deployed successfully
- [ ] Backend URL obtained and saved
- [ ] Health check endpoint tested: `https://your-backend.onrender.com/health`
- [ ] Logs checked for errors

## 🌐 Frontend Deployment (Vercel)

### Account Setup
- [ ] Vercel account created
- [ ] GitHub account connected to Vercel

### Project Configuration
- [ ] New project created
- [ ] GitHub repository imported
- [ ] Framework preset: Vite
- [ ] Root directory: `client`
- [ ] Build command: `npm run build`
- [ ] Output directory: `dist`

### Environment Variables
- [ ] `VITE_SOCKET_URL` = [your Render backend URL]

### Deployment
- [ ] Project deployed successfully
- [ ] Frontend URL obtained and saved
- [ ] Application loads in browser
- [ ] No console errors

## 🔄 Post-Deployment Configuration

### Update Backend CORS
- [ ] Go back to Render dashboard
- [ ] Update `CLIENT_URL` environment variable with Vercel URL
- [ ] Service redeployed automatically
- [ ] CORS working (no CORS errors in browser console)

### Test Full Application
- [ ] Frontend loads successfully
- [ ] Can create username and join chat
- [ ] Can send messages
- [ ] Real-time updates work
- [ ] Can switch rooms
- [ ] Can send files
- [ ] Reactions work
- [ ] Typing indicators work
- [ ] Private messages work

## 🔄 CI/CD Setup

### GitHub Actions
- [ ] `.github/workflows/ci-cd.yml` file exists
- [ ] Workflow runs on push to main/master
- [ ] Backend tests pass
- [ ] Frontend builds successfully
- [ ] No workflow errors

### Continuous Deployment
- [ ] Render auto-deploys on GitHub push
- [ ] Vercel auto-deploys on GitHub push
- [ ] Deployment notifications working

## 📊 Monitoring Setup

### Health Checks
- [ ] Health endpoint accessible: `/health`
- [ ] Returns correct status information
- [ ] MongoDB connection status shown

### UptimeRobot (Optional but Recommended)
- [ ] UptimeRobot account created
- [ ] Monitor added for backend health endpoint
- [ ] Alert contacts configured
- [ ] Test alert sent

### Platform Monitoring
- [ ] Render metrics dashboard reviewed
- [ ] Vercel analytics enabled
- [ ] MongoDB Atlas monitoring reviewed

## 📝 Documentation

### README Updates
- [ ] Frontend URL added to README
- [ ] Backend URL added to README
- [ ] Health check URL added
- [ ] Screenshots added (application, CI/CD, monitoring)
- [ ] All placeholders replaced with actual information

### Repository
- [ ] All code pushed to GitHub
- [ ] Commit messages are clear
- [ ] No sensitive data in repository
- [ ] All documentation files included

## 🎯 Final Verification

### Functionality
- [ ] Application accessible from any device
- [ ] Multiple users can chat simultaneously
- [ ] All features work in production
- [ ] No errors in browser console
- [ ] No errors in server logs

### Performance
- [ ] Page loads in < 3 seconds
- [ ] Messages send/receive instantly
- [ ] No lag or delays
- [ ] Health check responds quickly

### Security
- [ ] HTTPS enabled on both frontend and backend
- [ ] No sensitive data exposed
- [ ] CORS properly configured
- [ ] Security headers present (Helmet.js)

## 📸 Screenshots Required

- [ ] Screenshot of deployed frontend application
- [ ] Screenshot of GitHub Actions workflow (successful run)
- [ ] Screenshot of Render dashboard (metrics)
- [ ] Screenshot of health check response
- [ ] Screenshot of MongoDB Atlas cluster

## 📤 Submission

- [ ] All code committed and pushed to GitHub
- [ ] README updated with live URLs
- [ ] Screenshots added to repository
- [ ] ASSIGNMENT_SUMMARY.md reviewed
- [ ] All documentation complete
- [ ] Assignment submitted on time

## 🎉 Congratulations!

If all items are checked, your application is successfully deployed!

### Your Live URLs:
- **Frontend**: ___________________________
- **Backend**: ___________________________
- **Health Check**: ___________________________

### Share Your Success:
- [ ] Share app URL with friends
- [ ] Add to portfolio
- [ ] Document lessons learned

---

**Deployment Date**: _______________
**Deployed By**: Anne Njugi
