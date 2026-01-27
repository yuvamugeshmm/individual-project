# How to Run the Application - Step by Step

## ✅ Pre-Flight Checks

Your setup is verified:
- ✓ MongoDB connected
- ✓ Admin user exists (admin/admin123)
- ✓ Student user exists (714023205119/student123)
- ✓ Dependencies installed
- ✓ Code has no errors

## 🚀 Running the Application

### Method 1: Using PowerShell Scripts (Easiest)

**Terminal 1 - Start Backend:**
```powershell
.\start-backend.ps1
```
Wait until you see: `Server running on port 5000` and `MongoDB Connected`

**Terminal 2 - Start Frontend:**
```powershell
.\start-frontend.ps1
```
Wait until you see: `Local: http://localhost:3000/`

**Then open browser:** http://localhost:3000

---

### Method 2: Manual Commands

**Terminal 1 - Backend:**
```bash
cd backend
npm run dev
```
✅ You should see:
```
Server running on port 5000
MongoDB Connected
```

**Terminal 2 - Frontend (NEW TERMINAL):**
```bash
cd frontend
npm run dev
```
✅ You should see:
```
VITE v4.x.x  ready in xxx ms
➜  Local:   http://localhost:3000/
```

**Then open browser:** http://localhost:3000

---

## 🔐 Login Credentials

### Student Login:
- **URL:** http://localhost:3000/login
- **ID:** `714023205119`
- **Password:** `student123`
- **Checkbox:** Leave "Admin Login" **UNCHECKED**

### Admin Login:
- **URL:** http://localhost:3000/login
- **ID:** `admin`
- **Password:** `admin123`
- **Checkbox:** Check "Admin Login"

---

## 🐛 Troubleshooting

### Problem: "Cannot connect to server"
**Solution:**
1. Make sure backend is running (check Terminal 1)
2. Look for: `Server running on port 5000`
3. If not running, start it: `cd backend && npm run dev`

### Problem: "MongoDB connection error"
**Solution:**
1. Make sure MongoDB is running
2. Check `backend/.env` has correct `MONGODB_URI`
3. For local MongoDB: Make sure MongoDB service is started

### Problem: "Login failed"
**Solution:**
1. Check backend console for error messages
2. Verify users exist: `cd backend && node scripts/checkSetup.js`
3. If users missing: `cd backend && node scripts/createUser.js`
4. Check browser console (F12) for errors

### Problem: Page shows "Loading..." forever
**Solution:**
1. Check backend is running
2. Check browser console (F12) for errors
3. Try hard refresh: Ctrl+Shift+R
4. Clear browser cache

### Problem: Port already in use
**Solution:**
- Backend (5000): Change `PORT` in `backend/.env`
- Frontend (3000): Change port in `frontend/vite.config.js`

---

## ✅ Verification Steps

1. **Backend Health Check:**
   Open: http://localhost:5000/api/health
   Should show: `{"status":"OK","message":"Server is running"}`

2. **Frontend Loads:**
   Open: http://localhost:3000
   Should show login page

3. **Login Works:**
   - Enter credentials
   - Click Login
   - Should redirect to dashboard

4. **Dashboard Shows:**
   - Student: Should see "Student Dashboard" with upload form
   - Admin: Should see "Admin Dashboard" with tabs

---

## 📝 Quick Reference

| Component | Port | Command | URL |
|-----------|------|---------|-----|
| Backend | 5000 | `cd backend && npm run dev` | http://localhost:5000 |
| Frontend | 3000 | `cd frontend && npm run dev` | http://localhost:3000 |
| Login | - | - | http://localhost:3000/login |

---

## 🎯 Expected Behavior

1. **After starting backend:** You'll see MongoDB connection message
2. **After starting frontend:** Browser will open or you can manually go to localhost:3000
3. **After login:** You'll be redirected to:
   - `/dashboard` for students
   - `/admin` for admins
4. **Dashboard features:**
   - Upload documents
   - View documents
   - Search and filter
   - Download/Delete

---

## ⚠️ Important Notes

- **Both servers must run simultaneously** (backend + frontend)
- **MongoDB must be running** before starting backend
- **Use correct credentials** (case-sensitive)
- **Check both terminals** for error messages
- **Browser console (F12)** shows frontend errors

---

## 🆘 Still Not Working?

1. **Check both terminals** - Are both servers running?
2. **Check MongoDB** - Is it running?
3. **Check .env file** - Does it exist in `backend/.env`?
4. **Restart everything:**
   - Stop both servers (Ctrl+C)
   - Restart backend
   - Restart frontend
5. **Clear browser data:**
   - Clear cookies for localhost
   - Try incognito mode

---

**Need help?** Check the error messages in:
- Backend terminal
- Frontend terminal  
- Browser console (F12)
