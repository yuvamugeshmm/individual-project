# Quick Setup Guide

## Step 1: Backend Setup

1. Navigate to backend folder:
```bash
cd backend
```

2. Install dependencies:
```bash
npm install
```

3. Create `.env` file in the `backend` folder with the following content:
```
PORT=5000
MONGODB_URI=mongodb://localhost:27017/student_document_store
JWT_SECRET=your_super_secret_jwt_key_change_this_in_production_min_32_chars
NODE_ENV=development
FRONTEND_URL=http://localhost:3000
```

**Important**: Change `JWT_SECRET` to a strong random string (at least 32 characters) for production use.

4. Start MongoDB (if running locally):
```bash
# Windows (if MongoDB is installed as service, it should start automatically)
# Or use MongoDB Compass or MongoDB Atlas

# Linux/Mac
mongod
```

5. Create initial users:
```bash
node scripts/createUser.js
```

This will create:
- Admin user: ID `admin`, Password `admin123`
- Sample student: ID `714023205119`, Password `student123`

6. Start the backend server:
```bash
npm run dev
```

Backend will run on `http://localhost:5000`

## Step 2: Frontend Setup

1. Open a new terminal and navigate to frontend folder:
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

Frontend will run on `http://localhost:3000`

## Step 3: Access the Application

1. Open browser and go to `http://localhost:3000`
2. Login with:
   - **Admin**: ID `admin`, Password `admin123`
   - **Student**: ID `714023205119`, Password `student123`

## Troubleshooting

### MongoDB Connection Issues
- Make sure MongoDB is running
- Check if the connection string in `.env` is correct
- For MongoDB Atlas, use the connection string provided

### Port Already in Use
- Change `PORT` in backend `.env` file
- Update `FRONTEND_URL` accordingly
- Update Vite proxy in `frontend/vite.config.js`

### CORS Issues
- Make sure `FRONTEND_URL` in backend `.env` matches your frontend URL
- Check that both servers are running

### File Upload Issues
- Make sure `uploads` folder is created (will be auto-created on first upload)
- Check file permissions on the uploads directory

## Production Deployment Notes

Before deploying:
1. Change all default passwords
2. Use a strong `JWT_SECRET` (generate with: `openssl rand -base64 32`)
3. Set `NODE_ENV=production`
4. Use a production MongoDB instance
5. Configure proper CORS origins
6. Set up HTTPS
7. Consider using cloud storage for files
8. Set up proper logging and monitoring
