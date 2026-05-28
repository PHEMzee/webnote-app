# WebNote - A Full-Stack Note-Taking Application

A modern, responsive web application for creating, managing, and organizing notes with an intuitive user interface. Built with **React** and **Node.js/Express**, powered by **MongoDB**.

## 🌟 Features

- **Create Notes**: Quickly add new notes with title and content
- **Edit & Delete**: Modify or remove notes easily
- **Image Support**: Attach and manage images in your notes
- **Export Options**: Print or download notes as images
- **Responsive Design**: Beautiful Material-UI interface that works on all devices
- **Persistent Storage**: All notes are saved to MongoDB
- **RESTful API**: Clean API endpoints for note management

## 🛠️ Tech Stack

### Frontend
- **React 19** - UI library
- **Material-UI (MUI)** - Component library for styling
- **Axios** - HTTP client for API calls
- **React-to-Print** - Print note functionality
- **HTML2Canvas** - Export notes as images

### Backend
- **Node.js** - JavaScript runtime
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - ODM for MongoDB
- **CORS** - Cross-origin resource sharing
- **dotenv** - Environment variables management

## 📁 Project Structure

```
webnote/
├── mywebnote/                 # Frontend (React app)
│   ├── public/
│   │   ├── index.html
│   │   └── styles.css
│   ├── src/
│   │   ├── components/        # React components
│   │   │   ├── App.jsx
│   │   │   ├── Header.jsx
│   │   │   ├── CreateArea.jsx
│   │   │   ├── Note.jsx
│   │   │   └── ...
│   │   ├── api/               # API integration
│   │   │   └── notesApi.js
│   │   ├── App.css
│   │   └── index.js
│   ├── build/                 # Production build
│   └── package.json
│
├── webnotebackend/            # Backend (Express server)
│   ├── models/
│   │   └── Note.js            # Note schema
│   ├── routes/
│   │   └── noteRoutes.js      # API routes
│   ├── utils/
│   │   └── noteUtils.js       # Utility functions
│   ├── server.js              # Express server setup
│   ├── package.json
│   ├── Dockerfile             # Docker configuration
│   ├── docker-compose.yml     # Docker Compose setup
│   └── Procfile               # Deployment configuration
│
└── README.md                  # This file
```

## 🚀 Quick Start

### Prerequisites
- Node.js (v14 or higher)
- npm or yarn
- MongoDB (local or MongoDB Atlas)

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd webnote
   ```

2. **Setup Backend**
   ```bash
   cd webnotebackend
   npm install
   ```
   
   Create a `.env` file in the `webnotebackend` directory:
   ```
   PORT=5000
   MONGO_URI=mongodb://your-mongodb-uri
   ```

3. **Setup Frontend**
   ```bash
   cd ../mywebnote
   npm install
   ```
   
   Create a `.env` file in the `mywebnote` directory (if needed for API configuration):
   ```
   REACT_APP_API_URL=http://localhost:5000
   ```

### Running Locally

**Terminal 1 - Backend:**
```bash
cd webnotebackend
npm run dev  # Uses nodemon for auto-reload
```
Backend will be available at `http://localhost:5000`

**Terminal 2 - Frontend:**
```bash
cd mywebnote
npm start
```
Frontend will open at `http://localhost:3000`

## 📖 Available Scripts

### Frontend (`mywebnote/`)
- `npm start` - Runs development server
- `npm run build` - Creates production build
- `npm test` - Runs test suite

### Backend (`webnotebackend/`)
- `npm start` - Runs server with Node
- `npm run dev` - Runs server with Nodemon (auto-reload on changes)

## 🔗 API Endpoints

### Notes API (`/notes`)
- `GET /notes` - Get all notes
- `GET /notes/:id` - Get a specific note
- `POST /notes` - Create a new note
- `PUT /notes/:id` - Update a note
- `DELETE /notes/:id` - Delete a note

## 🐳 Docker Setup

Run the application using Docker:

```bash
cd webnotebackend
docker-compose up --build
```

The application will be available at `http://localhost:3000`

## 📦 Building for Production

1. **Build Frontend**
   ```bash
   cd mywebnote
   npm run build
   ```
   This creates an optimized production build in the `build/` folder.

2. **Prepare Backend**
   Ensure all environment variables are set on your hosting platform.

3. **Deploy**
   See deployment guides:
   - [Render Deployment](./RENDER_DEPLOYMENT.md)
   - [General Deployment Guide](./DEPLOYMENT_GUIDE.md)
   - [Quick Start Deployment](./QUICK_START_DEPLOYMENT.md)

## 📝 Environment Variables

### Backend (`webnotebackend/.env`)
```
PORT=5000
MONGO_URI=mongodb+srv://user:password@cluster.mongodb.net/webnote
```

### Frontend (`mywebnote/.env`)
```
REACT_APP_API_URL=http://localhost:5000
```

## 🧪 Testing

Run tests for the frontend:
```bash
cd mywebnote
npm test
```

## 🤝 Contributing

Contributions are welcome! Please feel free to:
1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

## 📄 License

This project is licensed under the ISC License.

## 🆘 Troubleshooting

### Frontend won't connect to backend
- Ensure the backend is running on port 5000
- Check CORS is enabled in `server.js`
- Verify the API URL in frontend environment variables

### MongoDB connection error
- Verify MongoDB URI in `.env`
- Check network connectivity to MongoDB Atlas (if cloud)
- Ensure IP whitelist includes your machine

### Port already in use
- Change the port in `.env` or use: `PORT=3001 npm start`

## 📚 Resources

- [React Documentation](https://react.dev)
- [Express.js Guide](https://expressjs.com)
- [MongoDB Documentation](https://docs.mongodb.com)
- [Material-UI Docs](https://mui.com)

## ✨ Highlights

- Full-stack MERN-style application
- Modern React with functional components
- Beautiful Material Design UI
- RESTful API architecture
- Docker-ready for containerization
- Cloud deployment ready (Render, Vercel, etc.)

---

**Built with ❤️ for efficient note-taking**
