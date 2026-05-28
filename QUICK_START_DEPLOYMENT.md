# Quick Start - Deployment

## 1️⃣ **Backend Setup** (5 minutes)

```bash
cd webnotebackend

# Install dependencies
npm install

# Create .env file
cp .env.example .env

# Edit .env with your MongoDB URI
nano .env
# MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/webnotedb
# PORT=5000
```

## 2️⃣ **Test Locally** (2 minutes)

```bash
# Terminal 1 - Backend
cd webnotebackend
npm run dev
# Should show: Server running on http://localhost:5000

# Terminal 2 - Frontend
cd mywebnote
REACT_APP_API_URL=http://localhost:5000/ npm start
# Browser opens at http://localhost:3000
```

Test the app:
- ✓ Create a note
- ✓ Save it
- ✓ Refresh page - note should persist
- ✓ Delete note

## 3️⃣ **Choose Your Platform**

### 🟣 **Heroku** (Recommended for beginners)

**Backend:**
```bash
cd webnotebackend
heroku login
heroku create your-api-name
heroku config:set MONGO_URI="mongodb+srv://..."
git push heroku main
# Note the URL: https://your-api-name.herokuapp.com
```

**Frontend:**
```bash
cd mywebnote

# Create production build with backend URL
REACT_APP_API_URL=https://your-api-name.herokuapp.com/ npm run build

# Deploy to Netlify
# Option A: Drag & drop build/ folder to Netlify
# Option B: Connect GitHub repo to Netlify
```

### 🔵 **Vercel** (Fast & modern)

**Backend:**
```bash
cd webnotebackend
npm install -g vercel
vercel --prod
# Note the URL shown at the end
```

**Frontend:**
```bash
cd mywebnote
vercel env add REACT_APP_API_URL
# Paste: https://your-backend-url.vercel.app/
vercel --prod
```

### 🟢 **DigitalOcean / AWS / VPS**

1. SSH into your server
2. Clone repository
3. Install Node.js
4. Follow instructions in `DEPLOYMENT_GUIDE.md`

### 🐳 **Docker (Any platform)**

```bash
cd webnotebackend
docker build -t webnote-api .
docker run -e MONGO_URI=... -p 5000:5000 webnote-api
```

## 4️⃣ **Post-Deployment**

- [ ] Test all endpoints
- [ ] Verify notes persist
- [ ] Check error messages
- [ ] Monitor server logs
- [ ] Set up backups

## 📌 Important Notes

1. **Environment Variables**: Keep `.env` files LOCAL. Never commit them.
2. **API URL**: Must include trailing slash: `https://api.example.com/`
3. **CORS**: Ensure backend allows requests from your frontend domain
4. **MongoDB**: Use MongoDB Atlas for managed cloud database

## ❓ Troubleshooting

| Issue | Solution |
|-------|----------|
| "Cannot fetch notes" | Check `REACT_APP_API_URL` is set correctly |
| CORS errors | Verify backend CORS config in `server.js` |
| Build fails | Delete `node_modules` and run `npm install` again |
| MongoDB connection fails | Check connection string in `.env` |

---

**Status**: ✅ Project is **ready to deploy!**
