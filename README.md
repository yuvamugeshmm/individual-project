# Student's Document Store System

A production-ready MERN stack web application for managing student documents with secure authentication, file upload, and role-based access control.

## Tech Stack

- **Frontend**: React.js, Tailwind CSS
- **Backend**: Node.js, Express.js
- **Database**: MongoDB
- **Authentication**: JWT with HTTP-only cookies, bcrypt
- **File Storage**: Local server storage

## Features

### Student Features
- Secure login with Student ID and Password
- Upload documents (PDF, JPG, PNG - Max 5MB)
- View own documents with pagination
- Search and filter documents by category
- Download own documents
- Delete own documents

### Admin Features
- Admin login
- View all documents from all students
- Delete any document
- Reset student passwords
- View all registered students

### Security Features
- JWT authentication with 1-hour expiry
- HTTP-only cookies
- bcrypt password hashing
- File ownership verification
- Secure file streaming
- File type and size validation
- Filename sanitization
- Executable file blocking
- Audit logging

## Project Structure

```
.
├── backend/
│   ├── models/
│   │   ├── User.js
│   │   ├── Document.js
│   │   └── AuditLog.js
│   ├── routes/
│   │   ├── auth.js
│   │   ├── documents.js
│   │   └── admin.js
│   ├── middleware/
│   │   └── auth.js
│   ├── utils/
│   │   ├── auditLogger.js
│   │   └── fileUtils.js
│   ├── uploads/
│   ├── server.js
│   ├── package.json
│   └── .env.example
├── frontend/
│   ├── src/
│   │   ├── pages/
│   │   │   ├── Login.jsx
│   │   │   ├── StudentDashboard.jsx
│   │   │   └── AdminDashboard.jsx
│   │   ├── utils/
│   │   │   └── api.js
│   │   ├── App.jsx
│   │   ├── main.jsx
│   │   └── index.css
│   ├── package.json
│   ├── vite.config.js
│   └── tailwind.config.js
└── README.md
```

## Setup Instructions

### Prerequisites
- Node.js (v14 or higher)
- MongoDB (running locally or MongoDB Atlas connection string)
- npm or yarn

### Backend Setup

1. Navigate to backend directory:
```bash
cd backend
```

2. Install dependencies:
```bash
npm install
```

3. Create `.env` file from `.env.example`:
```bash
cp .env.example .env
```

4. Edit `.env` file with your configuration:
```
PORT=5000
MONGODB_URI=mongodb://localhost:27017/student_document_store
JWT_SECRET=your_super_secret_jwt_key_change_this_in_production
NODE_ENV=development
FRONTEND_URL=http://localhost:3000
```

5. Start the backend server:
```bash
# Development mode (with nodemon)
npm run dev

# Production mode
npm start
```

The backend server will run on `http://localhost:5000`

### Frontend Setup

1. Navigate to frontend directory:
```bash
cd frontend
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

The frontend will run on `http://localhost:3000`

### Database Setup

1. Make sure MongoDB is running on your system.

2. The application will automatically create the database and collections on first run.

3. To create initial admin user, you can use MongoDB shell or a script:
```javascript
// Connect to MongoDB and run:
use student_document_store

db.users.insertOne({
  studentId: "admin",
  password: "$2a$10$YourHashedPasswordHere", // Use bcrypt to hash password
  role: "admin",
  name: "Administrator"
})
```

Or use a script to create admin (see below).

### Creating Initial Users

You can create users manually in MongoDB or use this Node.js script:

Create `backend/scripts/createUser.js`:
```javascript
const mongoose = require('mongoose');
const User = require('../models/User');
require('dotenv').config();

async function createUser() {
  await mongoose.connect(process.env.MONGODB_URI);
  
  // Create admin user
  const admin = new User({
    studentId: 'admin',
    password: 'admin123', // Will be hashed automatically
    role: 'admin',
    name: 'Administrator'
  });
  await admin.save();
  console.log('Admin user created');
  
  // Create sample student
  const student = new User({
    studentId: '714023205119',
    password: 'student123',
    role: 'student',
    name: 'John Doe',
    email: 'john@example.com'
  });
  await student.save();
  console.log('Student user created');
  
  process.exit();
}

createUser();
```

Run it:
```bash
node backend/scripts/createUser.js
```

## API Endpoints

### Authentication
- `POST /api/auth/login` - Student login
- `POST /api/auth/admin/login` - Admin login
- `POST /api/auth/logout` - Logout
- `GET /api/auth/me` - Get current user

### Documents (Student)
- `POST /api/documents/upload` - Upload document
- `GET /api/documents/my-documents` - Get own documents (with pagination, search, filter)
- `GET /api/documents/categories` - Get categories
- `GET /api/documents/download/:id` - Download document
- `DELETE /api/documents/:id` - Delete own document

### Admin
- `GET /api/admin/documents` - Get all documents
- `DELETE /api/admin/documents/:id` - Delete any document
- `POST /api/admin/reset-password` - Reset student password
- `GET /api/admin/students` - Get all students

## File Storage

Files are stored in:
```
backend/uploads/
  └── {studentId}/
      └── {category}/
          └── {randomFileName}.ext
```

Files are NOT publicly accessible. All file access requires:
1. Valid JWT token
2. Ownership verification (or admin role)

## Security Notes

- Passwords are hashed using bcrypt (10 rounds)
- JWT tokens expire after 1 hour
- HTTP-only cookies prevent XSS attacks
- File uploads are validated for type and size
- Filenames are sanitized
- Executable files are blocked
- All file downloads verify ownership
- Audit logs track all important actions

## Development Notes

- Backend uses Express.js with MongoDB (Mongoose)
- Frontend uses React with Vite
- Tailwind CSS for styling (basic layout only)
- CORS enabled for frontend-backend communication
- File uploads use Multer with memory storage

## Production Deployment

Before deploying to production:

1. Change `JWT_SECRET` to a strong random string
2. Set `NODE_ENV=production`
3. Update `FRONTEND_URL` to your production frontend URL
4. Use a production MongoDB instance (MongoDB Atlas recommended)
5. Consider using cloud storage (AWS S3, etc.) instead of local storage
6. Set up proper HTTPS
7. Configure proper CORS origins
8. Set up environment variables securely
9. Use a process manager like PM2
10. Set up proper logging and monitoring

## License

ISC
