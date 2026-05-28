# 🚀 WebNote Deployment - Quick Reference

## Your Project Details

```
📦 GitHub Repository: webnote-app
🔗 Backend (Render): morehope-webnote-api
🔗 Frontend (Netlify): [to be deployed]
🗄️ Database (MongoDB Atlas): MoreHope cluster
```

## 3-Step Deployment Process

### ✅ Step 1: Push to GitHub (5 min)
```bash
cd /home/okesanjo/Desktop/react-course26/webnote
git remote add origin https://github.com/YOUR_USERNAME/webnote-app.git
git branch -M main
git push -u origin main
```

### ✅ Step 2: Deploy Backend to Render (10 min)
1. Go to https://render.com → Sign up with GitHub
2. Click "New Web Service"
3. Select your `webnote-app` repository
4. **Root Directory**: `webnotebackend`
5. **Name**: `morehope-webnote-api`
6. Add environment variables (see RENDER_DEPLOYMENT.md)
7. Deploy!

**Backend URL**: `https://morehope-webnote-api.onrender.com`

### ✅ Step 3: Deploy Frontend to Netlify (10 min)
1. Go to https://app.netlify.com → Sign up with GitHub
2. Click "Import existing project"
3. Select your `webnote-app` repository
4. **Base directory**: `mywebnote`
5. **Build command**: `npm run build`
6. **Publish directory**: `mywebnote/build`
7. Add env var: `REACT_APP_API_URL=https://morehope-webnote-api.onrender.com/`
8. Deploy!

**Frontend URL**: `https://your-site-name.netlify.app`

---

## MongoDB Connection

```
Host: cluster0.wagkfi6.mongodb.net
User: MoreHope
Password: CbDvII0JA8tq4TQU
Database: webnotedb
```

---

## Environment Variables

### Backend (Render)
```
MONGO_URI=mongodb+srv://MoreHope:CbDvII0JA8tq4TQU@cluster0.wagkfi6.mongodb.net/?appName=Cluster0
NODE_ENV=production
PORT=10000
```

### Frontend (Netlify)
```
REACT_APP_API_URL=https://morehope-webnote-api.onrender.com/
```

---

## ✨ Features

- ✅ Create notes with title, content, keypoints, summary
- ✅ Edit existing notes
- ✅ Delete notes
- ✅ All data persists in MongoDB
- ✅ Modern Material-UI design
- ✅ Responsive layout

---

## 📞 Need Help?

See `RENDER_DEPLOYMENT.md` for detailed step-by-step instructions with screenshots.
