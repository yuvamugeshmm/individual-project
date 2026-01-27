# How to Run in Terminal - Step by Step

## 🖥️ Windows PowerShell Commands

### Step 1: Open Terminal
- Press `Win + X` and select "Windows PowerShell" or "Terminal"
- Or press `Win + R`, type `powershell`, press Enter

### Step 2: Navigate to Project Folder
```powershell
cd "C:\Users\yuvam\OneDrive\Desktop\Individual project"
```

### Step 3: Start Backend (Terminal 1)
```powershell
cd backend
npm run dev
```

**Wait until you see:**
```
Server running on port 5000
MongoDB Connected
```

### Step 4: Start Frontend (Terminal 2 - NEW WINDOW)
**Open a NEW PowerShell window** and run:
```powershell
cd "C:\Users\yuvam\OneDrive\Desktop\Individual project\frontend"
npm run dev
```

**Wait until you see:**
```
VITE v4.x.x  ready in xxx ms
➜  Local:   http://localhost:3000/
```

### Step 5: Open Browser
Go to: **http://localhost:3000**

---

## 📋 Quick Copy-Paste Commands

### Terminal 1 (Backend):
```powershell
cd "C:\Users\yuvam\OneDrive\Desktop\Individual project\backend"
npm run dev
```

### Terminal 2 (Frontend):
```powershell
cd "C:\Users\yuvam\OneDrive\Desktop\Individual project\frontend"
npm run dev
```

---

## ✅ What You Should See

**Backend Terminal:**
```
> student-document-store-backend@1.0.0 dev
> nodemon server.js

[nodemon] starting `node server.js`
MongoDB Connected
Server running on port 5000
```

**Frontend Terminal:**
```
VITE v4.x.x  ready in 523 ms

  ➜  Local:   http://localhost:3000/
  ➜  Network: use --host to expose
```

---

## 🛑 To Stop Servers
Press `Ctrl + C` in each terminal window

---

## 🔍 Troubleshooting

**If "npm" is not recognized:**
- Install Node.js from nodejs.org
- Restart terminal after installation

**If port is already in use:**
- Close other applications using ports 5000 or 3000
- Or change ports in .env and vite.config.js

**If MongoDB connection fails:**
- Make sure MongoDB is running
- Check backend/.env file has correct MONGODB_URI
