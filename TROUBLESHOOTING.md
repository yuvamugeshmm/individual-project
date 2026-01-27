# Troubleshooting Login Issues

## Common Issues and Solutions

### 1. "Login failed" Error

**Check these in order:**

#### A. Backend Server Running?
```bash
cd backend
npm run dev
```
You should see:
- `Server running on port 5000`
- `MongoDB Connected`

#### B. MongoDB Running?
- Make sure MongoDB is running locally, OR
- Check your `.env` file has correct `MONGODB_URI`

#### C. JWT_SECRET Set?
Check `backend/.env` file has:
```
JWT_SECRET=your_super_secret_jwt_key_change_this_in_production_min_32_chars
```

#### D. Users Exist in Database?
Run:
```bash
cd backend
node scripts/checkSetup.js
```

If users don't exist:
```bash
node scripts/createUser.js
```

#### E. Check Browser Console (F12)
- Open DevTools → Console tab
- Look for any red error messages
- Check Network tab for failed requests

#### F. Check Backend Console
- Look for error messages when you try to login
- Common errors:
  - "MongoDB connection error" → MongoDB not running
  - "JWT_SECRET is not defined" → Missing .env file
  - "Invalid credentials" → Wrong password or user doesn't exist

### 2. Cookie Issues

If login succeeds but you're redirected back to login:

**Check Cookies:**
1. Open DevTools (F12)
2. Go to Application → Cookies
3. Check if `token` cookie exists at `localhost:3000`
4. If missing, check CORS settings in `backend/server.js`

**Fix Cookie Settings:**
- Make sure `withCredentials: true` in frontend API calls
- Check `sameSite` setting in cookie (should be 'lax' for development)

### 3. CORS Issues

**Symptoms:**
- Network errors in browser console
- "CORS policy" errors

**Fix:**
- Check `backend/server.js` CORS configuration
- Make sure `credentials: true` is set
- Verify frontend URL matches CORS origin

### 4. Port Mismatch

**Check:**
- Backend should run on port 5000
- Frontend should run on port 3000
- Frontend proxy in `vite.config.js` should point to `http://localhost:5000`

### 5. Reset Everything

If nothing works:

1. **Reset Users:**
   ```bash
   cd backend
   node scripts/resetUsers.js
   ```

2. **Check Backend:**
   ```bash
   cd backend
   node scripts/checkSetup.js
   ```

3. **Restart Both Servers:**
   - Stop backend (Ctrl+C)
   - Stop frontend (Ctrl+C)
   - Start backend: `npm run dev`
   - Start frontend: `npm run dev`

4. **Clear Browser Data:**
   - Clear cookies for localhost
   - Hard refresh (Ctrl+Shift+R)

### 6. Test Backend Directly

Test if backend is working:
```bash
# In browser or Postman, test:
GET http://localhost:5000/api/health
```

Should return: `{"status":"OK","message":"Server is running"}`

### 7. Verify Credentials

**Default Credentials:**
- Student: ID `714023205119`, Password `student123`
- Admin: ID `admin`, Password `admin123`

**To verify in database:**
```bash
cd backend
node -e "const mongoose = require('mongoose'); const User = require('./models/User'); require('dotenv').config(); mongoose.connect(process.env.MONGODB_URI).then(async () => { const users = await User.find(); console.log(users.map(u => ({id: u.studentId, role: u.role}))); process.exit(); });"
```

## Still Not Working?

1. Check backend console for specific error messages
2. Check browser console (F12) for errors
3. Verify all environment variables are set
4. Make sure both servers are running
5. Try incognito/private browsing mode
6. Check firewall/antivirus isn't blocking localhost connections
