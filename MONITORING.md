# 📊 Monitoring & Maintenance Guide

## Health Check Endpoint

Your backend includes a health check endpoint at `/health`

### Response Format
```json
{
  "status": "ok",
  "timestamp": "2024-01-15T10:30:00.000Z",
  "uptime": 3600,
  "mongodb": "connected"
}
```

### Test Health Check
```bash
curl https://your-backend-url.com/health
```

## 🔍 Monitoring Tools

### 1. Render Built-in Monitoring (Free)

**What it monitors:**
- CPU usage
- Memory usage
- Response times
- Request counts
- Error rates

**How to access:**
1. Go to [Render Dashboard](https://dashboard.render.com)
2. Click on your service
3. Navigate to "Metrics" tab

### 2. UptimeRobot (Free Tier)

**Setup:**
1. Sign up at [UptimeRobot](https://uptimerobot.com)
2. Click "Add New Monitor"
3. Configure:
   - **Monitor Type**: HTTP(s)
   - **Friendly Name**: Chat App Backend
   - **URL**: `https://your-backend-url.com/health`
   - **Monitoring Interval**: 5 minutes
4. Add alert contacts (email, SMS, etc.)

**Benefits:**
- Get notified when your app goes down
- Track uptime percentage
- View response time history
- Free for up to 50 monitors

### 3. MongoDB Atlas Monitoring (Built-in)

**What it monitors:**
- Database connections
- Query performance
- Storage usage
- Network traffic

**How to access:**
1. Go to [MongoDB Atlas](https://cloud.mongodb.com)
2. Select your cluster
3. Click "Metrics" tab

### 4. Vercel Analytics (Built-in)

**What it monitors:**
- Page views
- Unique visitors
- Performance metrics
- Core Web Vitals

**How to access:**
1. Go to [Vercel Dashboard](https://vercel.com/dashboard)
2. Select your project
3. Click "Analytics" tab

## 📈 Key Metrics to Monitor

### Backend Metrics
- ✅ Response time (should be < 500ms)
- ✅ Error rate (should be < 1%)
- ✅ CPU usage (should be < 80%)
- ✅ Memory usage (should be < 80%)
- ✅ Active connections

### Frontend Metrics
- ✅ Page load time (should be < 3s)
- ✅ Time to Interactive (should be < 5s)
- ✅ First Contentful Paint (should be < 2s)

### Database Metrics
- ✅ Connection count
- ✅ Query execution time
- ✅ Storage usage

## 🚨 Alert Configuration

### Critical Alerts (Immediate Action)
- Application down (health check fails)
- Database connection lost
- Error rate > 5%
- Response time > 2s

### Warning Alerts (Monitor Closely)
- CPU usage > 80%
- Memory usage > 80%
- Error rate > 1%
- Response time > 500ms

## 🔧 Maintenance Tasks

### Daily
- [ ] Check error logs
- [ ] Monitor uptime status
- [ ] Review performance metrics

### Weekly
- [ ] Review MongoDB storage usage
- [ ] Check for security updates
- [ ] Review user feedback

### Monthly
- [ ] Update dependencies
- [ ] Review and optimize database queries
- [ ] Backup database
- [ ] Review and update documentation

## 📝 Logging

### Backend Logs (Render)
```bash
# View logs in Render dashboard
# Or use Render CLI
render logs -s your-service-name
```

### Frontend Logs
- Browser console (F12)
- Vercel deployment logs
- Vercel function logs

### MongoDB Logs
- Available in Atlas dashboard
- Under "Logs" tab in your cluster

## 🔄 Rollback Procedures

### Backend Rollback (Render)
1. Go to Render dashboard
2. Click on your service
3. Go to "Events" tab
4. Find previous successful deployment
5. Click "Rollback to this deploy"

### Frontend Rollback (Vercel)
1. Go to Vercel dashboard
2. Click on your project
3. Go to "Deployments" tab
4. Find previous deployment
5. Click "..." → "Promote to Production"

### Database Rollback
1. Use MongoDB Atlas backup
2. Go to "Backup" tab
3. Select restore point
4. Follow restore wizard

## 📊 Performance Optimization

### Backend
- Enable compression
- Implement caching
- Optimize database queries
- Use connection pooling (already configured)

### Frontend
- Code splitting (Vite does this automatically)
- Image optimization
- Lazy loading
- Service worker for offline support

### Database
- Create indexes for frequently queried fields
- Implement data archiving for old messages
- Regular database maintenance

## 🎯 Success Metrics

Track these KPIs:
- **Uptime**: Target 99.9%
- **Response Time**: Target < 500ms
- **Error Rate**: Target < 0.1%
- **User Satisfaction**: Monitor user feedback
- **Active Users**: Track daily/monthly active users

## 🆘 Emergency Contacts

Document your emergency procedures:
- [ ] Who to contact if app goes down
- [ ] Escalation procedures
- [ ] Backup administrator access
- [ ] Service provider support contacts

## 📚 Additional Resources

- [Render Status Page](https://status.render.com)
- [Vercel Status Page](https://www.vercel-status.com)
- [MongoDB Atlas Status](https://status.mongodb.com)
