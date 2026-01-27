# Quick Start Guide - Fix and Run

## Step 1: Verify Setup

Run this command to check and fix setup:
```powershell
.\setup-and-run.ps1
```

Or manually:

### Check Backend .env file
Make sure `backend/.env` exists and contains:
```
PORT=5000
MONGODB_URI=mongodb://localhost:27017/student_document_store
JWT_SECRET=your_super_secret_jwt_key_change_this_in_production_min_32_chars_required
NODE_ENV=development
FRONTEND_URL=http://localhost:3000
```

### Install Dependencies (if needed)
```bash
# Backend
cd backend
npm install

# Frontend  
cd ../frontend
npm install
```

### Create Users
```bash
cd backend
node scripts/createUser.js
```

## Step 2: Start Backend

**Option A: Use PowerShell script**
```powershell
.\start-backend.ps1
```

**Option B: Manual**
```bash
cd backend
npm run dev
```

You should see:
- `Server running on port 5000`
- `MongoDB Connected`

## Step 3: Start Frontend

**Option A: Use PowerShell script (in new terminal)**
```powershell
.\start-frontend.ps1
```

**Option B: Manual (in new terminal)**
```bash
cd frontend
npm run dev
```

You should see:
- `VITE v4.x.x ready in xxx ms`
- `➜  Local:   http://localhost:3000/`

## Step 4: Access Application

Open browser: **http://localhost:3000**

Login with:
- **Student:** ID `714023205119`, Password `student123`
- **Admin:** ID `admin`, Password `admin123`

## Common Errors & Fixes

### Error: "Cannot connect to server"
- Make sure backend is running on port 5000
- Check backend console for errors

### Error: "MongoDB connection error"
- Make sure MongoDB is running
- Check MONGODB_URI in .env file

### Error: "JWT_SECRET is not configured"
- Check backend/.env file exists
- Make sure JWT_SECRET is set

### Error: "Login failed"
- Run: `cd backend && node scripts/createUser.js`
- Check backend console for specific error
- Verify credentials: 714023205119/student123 or admin/admin123

### Error: "Module not found"
- Run: `npm install` in backend and frontend folders

## Verify Everything Works

1. **Test Backend Health:**
   Open: http://localhost:5000/api/health
   Should return: `{"status":"OK","message":"Server is running"}`

2. **Test Login:**
   - Go to http://localhost:3000
   - Try logging in with credentials above
   - Should redirect to dashboard

3. **Check Console:**
   - Backend: Should show no errors
   - Frontend: Open browser DevTools (F12), check Console tab

## Still Having Issues?

1. **Check both terminals** - Backend and Frontend must both be running
2. **Check MongoDB** - Must be running locally or use MongoDB Atlas
3. **Clear browser cache** - Try incognito mode
4. **Check ports** - Make sure ports 5000 and 3000 are not in use
5. **Restart everything** - Stop both servers (Ctrl+C) and restart
