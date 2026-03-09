# AI-Powered Real Estate Web Application

A full-stack real estate platform built with React, Express.js, Prisma, and MongoDB — featuring AI-powered property descriptions, conversational search, real-time chat, and interactive maps.

## Features

- **MERN + Prisma Stack** — React frontend, Express.js backend, MongoDB with Prisma ORM
- **JWT Cookie Authentication** — Secure login, registration, protected routes, and Express middleware for authorization
- **Real-Time Chat** — Bidirectional messaging between buyers and sellers using Socket.IO with auto-scroll and Zustand state management
- **Interactive Maps** — Property locations displayed on React Leaflet maps
- **Image Uploads** — Cloudinary-based image upload widget for property listings
- **AI Property Description Generator** — Converts structured property inputs (bedrooms, location, price) into polished listing descriptions using an LLM API
- **AI Conversational Search Assistant** — Natural language search that converts user queries like "3BHK under 50L in Pune" into database filters and returns matching properties

## Tech Stack

**Frontend:** React, React Router DOM, SCSS, React Leaflet, Zustand, Cloudinary Upload Widget

**Backend:** Express.js, Prisma ORM, MongoDB, Socket.IO

**Auth:** JWT, Cookie-based sessions, Express middleware

**AI:** LLM API integration for property descriptions and conversational search

**Deployment:** Vercel (frontend), Render (backend)

## Project Structure

```
├── client/                  # React frontend
│   ├── src/
│   │   ├── components/      # Reusable UI — Navbar, Card, Chat, Map, Filter, Slider, SearchBar
│   │   ├── routes/          # Pages — Home, List, Single, Profile, Login, Register, NewPost
│   │   ├── context/         # Auth and Socket context providers
│   │   └── lib/             # API requests, loaders, notification store
│   └── public/              # Static assets
├── api/                     # Express backend
│   ├── controllers/         # Auth, Post, User, Chat, Message controllers
│   ├── routes/              # REST API route definitions
│   ├── middleware/           # JWT verification middleware
│   ├── prisma/              # Prisma schema and MongoDB models
│   └── lib/                 # Prisma client instance
└── socket/                  # Socket.IO server for real-time chat
```

## Setup

**Prerequisites:** Node.js, MongoDB, Cloudinary account

**Backend:**
```bash
cd api
npm install
# Create .env with DATABASE_URL, JWT_SECRET, CLIENT_URL
npx prisma db push
node app.js
```

**Socket Server:**
```bash
cd socket
npm install
node app.js
```

**Frontend:**
```bash
cd client
npm install
npm run dev
```

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/register` | User registration |
| POST | `/api/auth/login` | User login (sets JWT cookie) |
| POST | `/api/auth/logout` | Logout (clears cookie) |
| GET | `/api/posts` | Get posts with query filters |
| GET | `/api/posts/:id` | Get single post details |
| POST | `/api/posts` | Create new listing (protected) |
| PUT | `/api/posts/:id` | Update listing (protected) |
| DELETE | `/api/posts/:id` | Delete listing (protected) |
| POST | `/api/posts/save` | Save/unsave a post (protected) |
| GET | `/api/users/profilePosts` | Get user's listings and saved posts |
| PUT | `/api/users/:id` | Update user profile (protected) |
| GET | `/api/chats` | Get user's chat conversations |
| GET | `/api/chats/:id` | Get single chat with messages |
| POST | `/api/chats` | Create a new chat |
| POST | `/api/messages/:chatId` | Send a message in a chat |

## AI Features

- **Property Description Generator** — Enter property details (type, bedrooms, bathrooms, area, location, price, amenities) and the AI generates a professional listing description ready to publish
- **Conversational Search** — Type natural language queries instead of using filters. The AI parses intent, maps it to database query parameters, and returns matching results
