# 🚀 Real-Time Chat Application - Deployment & DevOps

A full-stack MERN (MongoDB, Express, React, Node.js) real-time chat application with Socket.io, deployed to production with CI/CD pipeline.

## 📱 Live Application

- **Frontend URL**: https://client-eoybrofsf-annes-projects-191d800f.vercel.app
- **Backend URL**: https://chat-app-backend-jnw3.onrender.com
- **Health Check**: https://chat-app-backend-jnw3.onrender.com/health

## ✨ Features

- Real-time messaging with Socket.io
- Multiple chat rooms
- Private messaging
- Typing indicators
- Message reactions
- File sharing
- User status (online/away/busy)
- Message search
- Read receipts
- Unread message counts

## 🏗️ Architecture

### Frontend (React + Vite)
- Deployed on: Vercel
- Real-time updates via Socket.io client
- Responsive design
- Environment-based configuration

### Backend (Node.js + Express)
- Deployed on: Render
- Socket.io server for real-time communication
- RESTful API endpoints
- Security with Helmet.js
- Health check endpoint

### Database (MongoDB)
- Hosted on: MongoDB Atlas
- Message persistence
- User data storage
- Connection pooling

## 🛠️ Tech Stack

**Frontend:**
- React 18
- Socket.io Client
- Vite
- CSS3

**Backend:**
- Node.js
- Express.js
- Socket.io
- Mongoose
- Helmet (security)
- CORS

**Database:**
- MongoDB Atlas

**DevOps:**
- GitHub Actions (CI/CD)
- Render (Backend hosting)
- Vercel (Frontend hosting)
- Git (Version control)

## 📦 Installation & Local Development

### Prerequisites
- Node.js 18+ installed
- MongoDB Atlas account (or local MongoDB)
- Git

### 1. Clone the repository
```bash
git clone <your-repo-url>
cd deployment-and-devops-essentials-AnneNjugi
```

### 2. Set up Backend
```bash
cd server
npm install
cp .env.example .env
# Edit .env with your MongoDB URI and settings
npm start
```

### 3. Set up Frontend
```bash
cd client
npm install
cp .env.example .env
# Edit .env with your backend URL
npm run dev
```

### 4. Access the application
- Frontend: http://localhost:5173
- Backend: http://localhost:5000

## 🚀 Deployment

See [DEPLOYMENT_GUIDE.md](./DEPLOYMENT_GUIDE.md) for detailed deployment instructions.

### Quick Deployment Steps:
1. Set up MongoDB Atlas cluster
2. Deploy backend to Render
3. Deploy frontend to Vercel
4. Configure environment variables
5. Test the deployment

## 🔄 CI/CD Pipeline

GitHub Actions workflow automatically:
- ✅ Tests backend code on every push
- ✅ Builds frontend application
- ✅ Validates code syntax
- ✅ Notifies deployment readiness

View workflow: `.github/workflows/ci-cd.yml`

## 📊 Monitoring & Maintenance

### Health Check
- Endpoint: `/health`
- Returns: Server status, uptime, MongoDB connection status

### Monitoring Tools
- Render built-in metrics (CPU, Memory, Response time)
- UptimeRobot for uptime monitoring
- MongoDB Atlas monitoring

### Logs
- Backend logs available in Render dashboard
- Frontend logs in browser console
- MongoDB logs in Atlas dashboard

## 🔐 Environment Variables

### Backend (.env)
```
PORT=5000
CLIENT_URL=http://localhost:5173
MONGODB_URI=mongodb+srv://...
NODE_ENV=development
```

### Frontend (.env)
```
VITE_SOCKET_URL=http://localhost:5000
```

## 📸 Screenshots

[Add screenshots of your deployed application here]

### CI/CD Pipeline
[Add screenshot of GitHub Actions workflow]

### Monitoring Dashboard
[Add screenshot of Render/monitoring dashboard]

## 🧪 Testing

### Manual Testing
1. Open application in two browser windows
2. Create different usernames
3. Test sending messages
4. Verify real-time updates
5. Test room switching
6. Test file uploads
7. Test reactions and typing indicators

### Health Check Test
```bash
curl https://your-backend-url.com/health
```

## 📝 Assignment Completion

### ✅ Task 1: Application Preparation
- [x] Optimized React build process
- [x] Configured environment variables
- [x] Implemented error handling
- [x] Set up secure HTTP headers (Helmet)
- [x] Configured MongoDB Atlas
- [x] Implemented connection pooling

### ✅ Task 2: Backend Deployment
- [x] Deployed to Render
- [x] Configured environment variables
- [x] Set up continuous deployment
- [x] Implemented HTTPS
- [x] Set up health check endpoint

### ✅ Task 3: Frontend Deployment
- [x] Deployed to Vercel
- [x] Configured build settings
- [x] Set up environment variables
- [x] Configured continuous deployment
- [x] Implemented HTTPS

### ✅ Task 4: CI/CD Pipeline
- [x] GitHub Actions workflow created
- [x] Automated testing on push
- [x] Build validation
- [x] Deployment notifications

### ✅ Task 5: Monitoring
- [x] Health check endpoint
- [x] Server monitoring (Render)
- [x] Error tracking capability
- [x] Documentation of procedures

## 🤝 Contributing

This is an assignment project. For educational purposes only.

## 📄 License

ISC

## 👤 Author

Anne Njugi

## 🙏 Acknowledgments

- PLP Academy - MERN Stack Development Course
- Week 7: Deployment and DevOps Essentials

---

**Note**: Remember to update this README with your actual deployment URLs and screenshots after deploying!
