# WebNote Deployment Guide

## Project Structure
- **Frontend**: React app in `mywebnote/` (builds to `mywebnote/build/`)
- **Backend**: Node.js/Express server in `webnotebackend/`

## Prerequisites
- Node.js (v14+)
- MongoDB Atlas account or local MongoDB
- npm/yarn

## Local Development Setup

### Backend Setup
1. Navigate to `webnotebackend/`
2. Install dependencies:
   ```bash
   npm install
   ```
3. Create `.env` file from `.env.example`:
   ```bash
   cp .env.example .env
   ```
4. Update `.env` with your MongoDB URI:
   ```
   MONGO_URI=mongodb+srv://user:password@cluster.mongodb.net/webnotedb
   PORT=5000
   ```
5. Start development server:
   ```bash
   npm run dev
   ```

### Frontend Setup
1. Navigate to `mywebnote/`
2. Install dependencies:
   ```bash
   npm install
   ```
3. Create `.env` file:
   ```bash
   cp .env.example .env
   ```
4. For development, update `.env`:
   ```
   REACT_APP_API_URL=http://localhost:5000/
   ```
5. Start development server:
   ```bash
   npm start
   ```

## Production Deployment

### Option 1: Deploy to Heroku

#### Backend (Heroku)
1. Install Heroku CLI
2. In `webnotebackend/` directory:
   ```bash
   heroku login
   heroku create your-app-name-api
   heroku config:set MONGO_URI=mongodb+srv://...
   git push heroku main
   ```

#### Frontend (Netlify/Vercel)
1. Update `mywebnote/.env.production`:
   ```
   REACT_APP_API_URL=https://your-app-name-api.herokuapp.com/
   ```
2. Build the app:
   ```bash
   npm run build
   ```
3. Deploy to Netlify/Vercel from the `build/` folder

### Option 2: Deploy to a VPS (DigitalOcean, AWS, etc.)

#### Backend
1. SSH into your server
2. Clone the repository
3. Install Node.js and npm
4. Install dependencies: `npm install`
5. Create `.env` with production values
6. Use PM2 for process management:
   ```bash
   npm install -g pm2
   pm2 start server.js --name "webnote-api"
   pm2 startup
   pm2 save
   ```

#### Frontend
1. Build the React app:
   ```bash
   npm run build
   ```
2. Serve with Nginx:
   ```nginx
   server {
       listen 80;
       server_name yourdomain.com;
       
       root /path/to/mywebnote/build;
       index index.html;
       
       location / {
           try_files $uri $uri/ /index.html;
       }
       
       location /notes {
           proxy_pass http://localhost:5000;
       }
   }
   ```

### Option 3: Docker Deployment

Create `Dockerfile` in backend:
```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 5000
CMD ["npm", "start"]
```

Create `Dockerfile` in frontend:
```dockerfile
FROM node:18-alpine as build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

## Environment Variables Checklist

### Backend (.env)
- [ ] MONGO_URI - MongoDB connection string
- [ ] PORT - Server port (default: 5000)
- [ ] NODE_ENV - Set to 'production'

### Frontend (.env.production)
- [ ] REACT_APP_API_URL - Backend API URL (with trailing slash)

## Pre-Deployment Checklist

- [ ] Test frontend and backend locally
- [ ] Run tests: `npm test`
- [ ] Build frontend: `npm run build`
- [ ] Verify build folder has no errors
- [ ] Remove console.log statements (optional)
- [ ] Test API endpoints with Postman
- [ ] Verify MongoDB connection
- [ ] Check CORS configuration in backend
- [ ] Set up environment variables on hosting platform

## Troubleshooting

### API Connection Issues
- Ensure CORS is enabled in `server.js`
- Verify REACT_APP_API_URL matches backend URL
- Check MongoDB connection string

### Build Errors
- Clear `node_modules` and `package-lock.json`
- Reinstall: `npm install`
- Check Node version compatibility

### Database Issues
- Verify MongoDB Atlas IP whitelist
- Check MongoDB URI format
- Ensure database user has proper permissions

## Monitoring

After deployment:
- Set up error logging (e.g., Sentry)
- Monitor server performance
- Set up automated backups for MongoDB
- Use PM2 for process management on VPS
