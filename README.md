# 📝 BlogVerse — Blog Platform with Comments

A full-stack blogging platform built with **Node.js**, **Express**, **MongoDB**, and **Vanilla JS**.

---

## ✅ Features Implemented

### Authentication
- User registration with validation
- JWT-based login/logout
- Protected routes (middleware)
- Password hashing with bcryptjs

### Blog Posts
- Create, Read, Update, Delete (CRUD)
- Category filtering (Technology, Lifestyle, Travel, etc.)
- Tag system
- Full-text search
- Pagination
- View count tracking
- Like/Unlike toggle
- Auto-generated slugs & excerpts

### Comments
- Add comments to posts
- Nested replies (one level)
- Edit & delete own comments
- Like comments
- Real-time comment refresh

### RESTful API
- Full REST API with proper HTTP status codes
- Input validation with express-validator
- Global error handling middleware
- CORS configured

---

## 🚀 Setup & Run

### Prerequisites
- Node.js v16+
- MongoDB (local or MongoDB Atlas)

### 1. Clone & Install
```bash
cd backend
npm install
```

### 2. Configure Environment
```bash
cp .env.example .env
# Edit .env and set your MONGODB_URI and JWT_SECRET
```

### 3. Start the Server
```bash
# Development (with auto-reload)
npm run dev

# Production
npm start
```

### 4. Open the App
Visit: **http://localhost:5000**

---

## 📡 API Endpoints

### Auth
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/register` | Register new user |
| POST | `/api/auth/login` | Login |
| GET  | `/api/auth/me` | Get current user (auth) |
| PUT  | `/api/auth/profile` | Update profile (auth) |

### Posts
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET  | `/api/posts` | Get all posts (with filters) |
| GET  | `/api/posts/:id` | Get single post |
| POST | `/api/posts` | Create post (auth) |
| PUT  | `/api/posts/:id` | Update post (auth, owner) |
| DELETE | `/api/posts/:id` | Delete post (auth, owner) |
| POST | `/api/posts/:id/like` | Toggle like (auth) |

### Comments
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET  | `/api/comments/post/:postId` | Get post comments |
| POST | `/api/comments/post/:postId` | Add comment (auth) |
| PUT  | `/api/comments/:id` | Edit comment (auth, owner) |
| DELETE | `/api/comments/:id` | Delete comment (auth, owner) |
| POST | `/api/comments/:id/like` | Like comment (auth) |

### Query Parameters (GET /api/posts)
- `page` — Page number (default: 1)
- `limit` — Posts per page (default: 10)
- `category` — Filter by category
- `search` — Full-text search
- `sort` — `latest` | `oldest` | `popular`

---

## 🗂 Project Structure
```
blog-platform/
├── backend/
│   ├── models/
│   │   ├── User.js       # User schema + bcrypt
│   │   ├── Post.js       # Post schema + virtual fields
│   │   └── Comment.js    # Comment schema with replies
│   ├── routes/
│   │   ├── auth.js       # Auth endpoints
│   │   ├── posts.js      # Post CRUD + likes
│   │   └── comments.js   # Comment CRUD + replies
│   ├── middleware/
│   │   └── auth.js       # JWT protect + optionalAuth
│   ├── server.js         # Express app + MongoDB connect
│   ├── package.json
│   └── .env.example
└── frontend/
    └── public/
        └── index.html    # Full SPA frontend
```

---

## 🔐 Auth Flow
1. User registers → password hashed → JWT returned
2. JWT stored in localStorage
3. Protected routes check `Authorization: Bearer <token>`
4. Token decoded to get `req.user`

---

## 🛠 Tech Stack
- **Backend**: Node.js, Express.js
- **Database**: MongoDB + Mongoose
- **Auth**: JWT + bcryptjs
- **Validation**: express-validator
- **Frontend**: Vanilla JS SPA (no framework)
- **Fonts**: DM Sans + DM Serif Display
