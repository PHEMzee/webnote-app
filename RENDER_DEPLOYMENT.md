# Render Deployment Guide - WebNote App

## 🚀 Deployment Steps

### Step 1: Push Your Code to GitHub

Render requires your code to be on GitHub. Follow these steps:

#### 1a. Create a GitHub Repository
1. Go to https://github.com/new
2. Repository name: `webnote-app`
3. Description: `A web note-taking application`
4. Choose: **Public** (Render can access it)
5. Click **Create repository**

#### 1b. Push Your Local Code
Run these commands in your terminal:

```bash
cd /home/okesanjo/Desktop/react-course26/webnote

# Add your GitHub repository as remote
git remote add origin https://github.com/YOUR_GITHUB_USERNAME/webnote-app.git

# Rename branch to main (if needed)
git branch -M main

# Push your code
git push -u origin main
```

**Replace `YOUR_GITHUB_USERNAME` with your actual GitHub username!**

---

### Step 2: Deploy Backend to Render

#### 2a. Connect to Render
1. Go to https://render.com
2. Click **Sign up** (free account)
3. Choose **GitHub** authentication
4. Authorize Render to access your GitHub repositories

#### 2b. Create Web Service
1. Go to https://dashboard.render.com
2. Click **New +** → **Web Service**
3. Select your `webnote-app` repository
4. Fill in these details:
   - **Name**: `morehope-webnote-api`
   - **Runtime**: `Node`
   - **Build Command**: `npm install`
   - **Start Command**: `npm start`
   - **Root Directory**: `webnotebackend`

#### 2c. Set Environment Variables
Add these environment variables:
- **MONGO_URI**: `mongodb+srv://MoreHope:CbDvII0JA8tq4TQU@cluster0.wagkfi6.mongodb.net/?appName=Cluster0`
- **NODE_ENV**: `production`
- **PORT**: `10000`

#### 2d. Deploy
Click **Create Web Service** and wait for deployment to complete (3-5 minutes).

**Note your Render URL**: It will be something like `https://morehope-webnote-api.onrender.com`

---

### Step 3: Deploy Frontend to Netlify

#### 3a. Build Frontend with Backend URL
After Render deployment completes, update your frontend:

```bash
cd /home/okesanjo/Desktop/react-course26/webnote/mywebnote

# Create production build with Render backend URL
REACT_APP_API_URL=https://morehope-webnote-api.onrender.com/ npm run build
```

#### 3b. Connect to Netlify
1. Go to https://app.netlify.com/
2. Click **Sign up** (use GitHub)
3. Authorize and connect GitHub

#### 3c. Deploy Frontend
1. Click **Add new site** → **Import an existing project**
2. Choose your GitHub repository
3. Fill in:
   - **Base directory**: `mywebnote`
   - **Build command**: `npm run build`
   - **Publish directory**: `mywebnote/build`
4. Add environment variable:
   - **REACT_APP_API_URL**: `https://morehope-webnote-api.onrender.com/`
5. Click **Deploy site**

**Your site URL will be**: `https://your-site-name.netlify.app`

---

## 🔗 Summary

After deployment, you'll have:

| Component | URL |
|-----------|-----|
| **Backend API** | https://morehope-webnote-api.onrender.com |
| **Frontend App** | https://your-site-name.netlify.app |

---

## ⚠️ Important Notes

1. **Render Cold Starts**: First request might take 30 seconds (free tier limitation)
2. **MongoDB**: Keep your connection string secure - never commit `.env` files
3. **CORS**: Backend CORS is already configured to accept all origins
4. **API URL**: Must have trailing slash: `https://api.onrender.com/`

---

## 🧪 Testing After Deployment

1. Go to your Netlify URL
2. Create a new note
3. Refresh the page - note should persist
4. Try updating and deleting notes

---

## ❓ Troubleshooting

| Problem | Solution |
|---------|----------|
| "Cannot fetch notes" | Check REACT_APP_API_URL includes trailing slash |
| CORS errors | Verify backend is running on Render |
| Build fails | Delete `node_modules` in mywebnote and rebuild |
| Render shows error | Check MONGO_URI is correct in environment variables |

---

## 📱 Share Your App

Once deployed, share your Netlify URL with anyone! They can:
- ✅ Create notes
- ✅ View all notes
- ✅ Edit notes
- ✅ Delete notes
- ✅ All data persists in MongoDB

