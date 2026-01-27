# How to Run the Student Document Store System

## 📋 Prerequisites

Make sure you have installed:
- ✅ Node.js (v14 or higher) - [Download](https://nodejs.org/)
- ✅ MongoDB (running locally or MongoDB Atlas)
- ✅ npm (comes with Node.js)

---

## 🚀 Step-by-Step Instructions

### Step 1: Open Terminal/PowerShell

**Windows:**
- Press `Win + X` and select "Windows PowerShell" or "Terminal"
- Or press `Win + R`, type `powershell`, press Enter

### Step 2: Navigate to Project Folder

```powershell
cd "C:\Users\yuvam\OneDrive\Desktop\Individual project"
```

### Step 3: Install Backend Dependencies (First Time Only)

```powershell
cd backend
npm install
```

Wait for installation to complete. You should see:
```
added XXX packages
```

### Step 4: Install Frontend Dependencies (First Time Only)

Open a **NEW** PowerShell window and run:

```powershell
cd "C:\Users\yuvam\OneDrive\Desktop\Individual project\frontend"
npm install
```

Wait for installation to complete.

---

## 🎯 Running the Application

### Option 1: Using Two Terminal Windows (Recommended)

#### Terminal 1 - Start Backend Server:

```powershell
cd "C:\Users\yuvam\OneDrive\Desktop\Individual project\backend"
npm run dev
```

**You should see:**
```
> student-document-store-backend@1.0.0 dev
> nodemon server.js

[nodemon] starting `node server.js`
MongoDB Connected
Server running on port 5000
```

✅ **Keep this terminal open!**

#### Terminal 2 - Start Frontend Server:

Open a **NEW** PowerShell window and run:

```powershell
cd "C:\Users\yuvam\OneDrive\Desktop\Individual project\frontend"
npm run dev
```

**You should see:**
```
VITE v4.x.x  ready in 523 ms

  ➜  Local:   http://localhost:3000/
  ➜  Network: use --host to expose
```

✅ **Keep this terminal open too!**

#### Step 5: Open Browser

Open your web browser and go to:
```
http://localhost:3000
```

You'll be redirected to the login page.

---

### Option 2: Using PowerShell Scripts

#### Start Backend:
```powershell
.\start-backend.ps1
```

#### Start Frontend (in new window):
```powershell
.\start-frontend.ps1
```

---

## 🔐 Login Credentials

### Student Login:
- **ID:** `714023205119`
- **Password:** `student123`
- **Checkbox:** Leave "Admin Login" **UNCHECKED**

### Admin Login:
- **ID:** `admin`
- **Password:** `admin123`
- **Checkbox:** Check "Admin Login"

---

## ✅ Verification Checklist

### Backend is Running:
- [ ] Terminal shows: `Server running on port 5000`
- [ ] Terminal shows: `MongoDB Connected`
- [ ] No error messages in terminal

### Frontend is Running:
- [ ] Terminal shows: `Local: http://localhost:3000/`
- [ ] No error messages in terminal

### Browser:
- [ ] Can access: http://localhost:3000
- [ ] Login page loads correctly
- [ ] Can login with credentials above

---

## 🐛 Troubleshooting

### Problem: "npm is not recognized"
**Solution:** Install Node.js from [nodejs.org](https://nodejs.org/)

### Problem: "MongoDB connection error"
**Solution:**
1. Make sure MongoDB is running
2. Check `backend/.env` file has correct `MONGODB_URI`
3. For local MongoDB: Start MongoDB service

### Problem: "Port 5000 already in use"
**Solution:**
1. Close other applications using port 5000
2. Or change `PORT` in `backend/.env` file

### Problem: "Port 3000 already in use"
**Solution:**
1. Close other applications using port 3000
2. Or change port in `frontend/vite.config.js`

### Problem: "Cannot find module"
**Solution:**
1. Make sure you ran `npm install` in both backend and frontend folders
2. Check that `node_modules` folder exists

### Problem: "Login failed"
**Solution:**
1. Make sure backend is running (check Terminal 1)
2. Check backend console for error messages
3. Verify users exist: `cd backend && node scripts/createUser.js`

---

## 🛑 To Stop the Servers

Press `Ctrl + C` in each terminal window to stop the servers.

---

## 📝 Quick Reference

| Component | Port | Command | Status Check |
|-----------|------|---------|--------------|
| Backend | 5000 | `cd backend && npm run dev` | http://localhost:5000/api/health |
| Frontend | 3000 | `cd frontend && npm run dev` | http://localhost:3000 |

---

## 🎯 Expected Flow

1. ✅ Start backend → See "Server running on port 5000"
2. ✅ Start frontend → See "Local: http://localhost:3000/"
3. ✅ Open browser → Go to http://localhost:3000
4. ✅ Login page appears
5. ✅ Enter credentials → Click Login
6. ✅ Redirected to dashboard

---

## 💡 Pro Tips

1. **Keep both terminals visible** - Easier to see errors
2. **Check terminal for errors** - Red text indicates problems
3. **Use browser DevTools (F12)** - Check console for frontend errors
4. **Test backend health** - Visit http://localhost:5000/api/health
5. **Clear browser cache** - If styles look broken, press Ctrl+Shift+R

---

## 🆘 Still Having Issues?

1. **Check both terminals** - Are both servers running?
2. **Check MongoDB** - Is it running?
3. **Check .env file** - Does `backend/.env` exist?
4. **Restart everything:**
   - Stop both servers (Ctrl+C)
   - Restart backend
   - Restart frontend
5. **Check error messages** - Read what the terminals say

---

**You're all set! Happy coding! 🚀**
