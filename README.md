# 🎓 Edunova Frontend# Edunova Frontend



A modern, AI-powered learning platform built with React and Vite. Edunova helps students create personalized learning roadmaps, track progress, and access curated resources.React + Vite frontend for Edunova.



## ✨ FeaturesQuick start



- 🤖 **AI-Powered Chatbot** - Get instant answers using Google Gemini AI```powershell

- 🗺️ **Personalized Roadmaps** - Generate custom learning paths with AIcd C:\Users\yoges\Desktop\Projects\Edunova\EdunovaFrontend

- ✅ **Progress Tracking** - Interactive checklists to monitor your learning journeynpm install

- 💼 **Placement Preparation** - Curated resources for interview prepnpm run dev

- 📚 **Resource Recommendations** - YouTube videos and hands-on projects```

- 🔐 **User Authentication** - Secure login and signup with JWT

- 📱 **Responsive Design** - Works seamlessly on all devicesOpen http://localhost:5173 after starting the frontend.



## 🛠️ Tech Stack## Features

- React + Vite for fast development

- **React 18** - UI library- Tailwind CSS for styling

- **Vite** - Fast build tool and dev server- Calls the Node.js backend which uses Google Gemini AI to generate personalized learning roadmaps

- **React Router** - Client-side routing- Includes YouTube video recommendations and hands-on projects for each week

- **Tailwind CSS** - Utility-first CSS framework
- **Framer Motion** - Animations
- **Axios** - HTTP client
- **React Markdown** - Markdown rendering with syntax highlighting

## 🚀 Quick Start

### Prerequisites

- Node.js (v14 or higher)
- npm or yarn

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd EdunovaFrontend
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   
   Create a `.env.local` file in the root directory:
   ```env
   VITE_API_URL=http://localhost:5000
   ```

4. **Start the development server**
   ```bash
   npm run dev
   ```

5. **Open your browser**
   
   Navigate to http://localhost:5173

## 📦 Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build locally
- `npm run lint` - Run ESLint

## 🌍 Environment Variables

Create these files for different environments:

### `.env.local` (Local Development)
```env
VITE_API_URL=http://localhost:5000
```

### `.env.production` (Production)
```env
VITE_API_URL=https://edunovabackend.onrender.com
```

> **Note**: All environment variables must be prefixed with `VITE_` to be exposed to the client.

## 📁 Project Structure

```
EdunovaFrontend/
├── public/
│   ├── _redirects          # For SPA routing on Render
│   └── vite.svg
├── src/
│   ├── components/         # Reusable components
│   │   ├── ChatbotFloater.jsx
│   │   ├── Home.jsx
│   │   ├── Navbar.jsx
│   │   ├── RoadmapBlock.jsx
│   │   └── Sidebar.jsx
│   ├── pages/             # Page components
│   │   ├── Chatbot.jsx
│   │   ├── ChatHistory.jsx
│   │   ├── Checklist.jsx
│   │   ├── Home.jsx
│   │   ├── Login.jsx
│   │   ├── PlacementPrep.jsx
│   │   ├── Roadmap.jsx
│   │   ├── RoadmapHistory.jsx
│   │   ├── RoadmapView.jsx
│   │   └── Signup.jsx
│   ├── utils/             # Utility functions
│   │   └── auth.js
│   ├── App.jsx            # Main app component
│   ├── main.jsx          # Entry point
│   └── index.css         # Global styles
├── .env.example          # Environment variables template
├── .env.local            # Local environment (not committed)
├── .env.production       # Production environment
├── render.yaml           # Render deployment config
└── package.json
```

## 🚢 Deployment on Render

### Quick Deploy

1. **Push code to GitHub**

2. **Create Static Site on Render**
   - Go to [Render Dashboard](https://render.com)
   - Click "New +" → "Static Site"
   - Connect your repository
   
3. **Configure Build Settings**
   - **Build Command**: `npm install && npm run build`
   - **Publish Directory**: `dist`
   - **Root Directory**: `EdunovaFrontend` (if in monorepo)
   
4. **Add Environment Variable**
   - **Key**: `VITE_API_URL`
   - **Value**: `https://edunovabackend.onrender.com`

5. **Deploy!**
   - Click "Create Static Site"
   - Wait for deployment to complete

### Using Blueprint (Alternative)

The project includes a `render.yaml` file for automatic configuration:

1. Go to Render Dashboard
2. Click "New +" → "Blueprint"
3. Connect repository
4. Render will auto-configure from `render.yaml`
5. Review and apply

### Important: Update Backend CORS

After deploying, update your backend's CORS configuration to include your frontend URL:

```javascript
// In backend server.js
app.use(cors({
  origin: [
    'http://localhost:5173',
    'https://your-frontend-url.onrender.com'  // Add your deployed URL
  ],
  credentials: true,
}));
```

## 🔧 API Integration

The frontend connects to the backend API using the `VITE_API_URL` environment variable.

Example usage in components:
```javascript
const apiUrl = import.meta.env.VITE_API_URL || 'http://localhost:5000';

const response = await fetch(`${apiUrl}/api/chatbot/ask`, {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': `Bearer ${token}`
  },
  body: JSON.stringify(data)
});
```

## 🎨 Customization

### Tailwind Configuration

Customize theme in `tailwind.config.js`:
```javascript
export default {
  content: ['./index.html', './src/**/*.{js,jsx}'],
  theme: {
    extend: {
      colors: {
        // Add custom colors
      }
    }
  }
}
```

### Adding New Routes

1. Create component in `src/pages/`
2. Import in `App.jsx`
3. Add route:
   ```jsx
   <Route path="/new-page" element={<NewPage />} />
   ```

## 🐛 Troubleshooting

### API Connection Issues
- Verify `VITE_API_URL` is set correctly
- Check backend is running at the specified URL
- Look for CORS errors in browser console
- Ensure backend allows your frontend origin

### Build Fails
- Clear `node_modules`: `rm -rf node_modules && npm install`
- Check Node version compatibility (v14+)
- Review build logs for specific errors
- Ensure all dependencies are in `package.json`

### Routing Issues on Page Refresh
- Ensure `_redirects` file exists in `public/` folder
- Content should be: `/* /index.html 200`
- This enables client-side routing for SPAs

### Environment Variables Not Working
- Ensure variables are prefixed with `VITE_`
- Restart dev server after changing `.env` files
- Check: `console.log(import.meta.env.VITE_API_URL)`
- Clear browser cache

## 🔐 Authentication

The app uses JWT-based authentication:

1. User logs in via `/api/user/login`
2. Token is stored in `localStorage`
3. Token is sent in Authorization header for protected routes
4. Token is validated by backend middleware

## 📱 Pages Overview

- **Home** - Landing page with platform overview
- **Login/Signup** - User authentication
- **Roadmap** - Generate AI-powered learning roadmaps
- **Roadmap History** - View previously created roadmaps
- **Roadmap View** - Detailed view of a specific roadmap
- **Checklist** - Track learning progress
- **Chatbot** - AI assistant for learning queries
- **Chat History** - Previous chatbot conversations
- **Placement Prep** - Interview preparation resources

## 🌐 Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## 📄 License

This project is private and proprietary.

## 🤝 Contributing

This is a private project. For any questions or issues, please contact the development team.

## 📧 Support

For support, please open an issue in the repository or contact the maintainers.

---

**Live Demo**: [https://edunovafrontend.onrender.com](https://edunovafrontend.onrender.com)  
**Backend**: [https://edunovabackend.onrender.com](https://edunovabackend.onrender.com)

Made with ❤️ by the Edunova Team
