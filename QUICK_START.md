# ⚡ Quick Start Guide

Get your chat app running locally in 5 minutes!

## 🚀 Fast Setup

### 1. Install Dependencies

```bash
# Install backend dependencies
cd server
npm install

# Install frontend dependencies
cd ../client
npm install
cd ..
```

### 2. Configure Environment Variables

**Backend** (`server/.env`):
```bash
cd server
cp .env.example .env
```

Edit `server/.env`:
```
PORT=5000
CLIENT_URL=http://localhost:5173
MONGODB_URI=mongodb+srv://your-connection-string
NODE_ENV=development
```

**Frontend** (`client/.env`):
```bash
cd client
cp .env.example .env
```

Edit `client/.env`:
```
VITE_SOCKET_URL=http://localhost:5000
```

### 3. Start the Application

**Terminal 1 - Backend:**
```bash
cd server
npm start
```

**Terminal 2 - Frontend:**
```bash
cd client
npm run dev
```

### 4. Open in Browser

Go to: http://localhost:5173

## 🎯 What's Next?

1. **Test locally** - Open multiple browser windows to test chat
2. **Set up MongoDB Atlas** - Follow [DEPLOYMENT_GUIDE.md](./DEPLOYMENT_GUIDE.md)
3. **Deploy to production** - Deploy backend to Render, frontend to Vercel
4. **Monitor your app** - Set up health checks and monitoring

## 🐛 Troubleshooting

**Backend won't start?**
- Check if port 5000 is available
- Verify MongoDB connection string

**Frontend can't connect?**
- Ensure backend is running on port 5000
- Check VITE_SOCKET_URL in client/.env

**Need help?**
- Check the full [DEPLOYMENT_GUIDE.md](./DEPLOYMENT_GUIDE.md)
- Review [Week7-Assignment.md](./Week7-Assignment.md)
