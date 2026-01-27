# Application Links & URLs

## Frontend (React App)
**Main Application:**
- **Login Page:** http://localhost:3000/login
- **Student Dashboard:** http://localhost:3000/dashboard
- **Admin Dashboard:** http://localhost:3000/admin
- **Home (redirects to login):** http://localhost:3000

## Backend (Express API)
**API Endpoints:**
- **Health Check:** http://localhost:5000/api/health
- **Login:** http://localhost:5000/api/auth/login
- **Admin Login:** http://localhost:5000/api/auth/admin/login
- **Get Current User:** http://localhost:5000/api/auth/me
- **Logout:** http://localhost:5000/api/auth/logout

**Document Endpoints:**
- **Upload Document:** http://localhost:5000/api/documents/upload
- **Get My Documents:** http://localhost:5000/api/documents/my-documents
- **Get Categories:** http://localhost:5000/api/documents/categories
- **Download Document:** http://localhost:5000/api/documents/download/:id
- **Delete Document:** http://localhost:5000/api/documents/:id

**Admin Endpoints:**
- **Get All Documents:** http://localhost:5000/api/admin/documents
- **Delete Any Document:** http://localhost:5000/api/admin/documents/:id
- **Reset Password:** http://localhost:5000/api/admin/reset-password
- **Get All Students:** http://localhost:5000/api/admin/students

---

## Quick Access

### To Start the Application:

1. **Start Backend:**
   ```bash
   cd backend
   npm run dev
   ```
   Backend will run on: **http://localhost:5000**

2. **Start Frontend:**
   ```bash
   cd frontend
   npm run dev
   ```
   Frontend will run on: **http://localhost:3000**

3. **Open in Browser:**
   - Go to: **http://localhost:3000**
   - You'll be redirected to: **http://localhost:3000/login**

---

## Login Credentials

### Student Login
- **URL:** http://localhost:3000/login
- **ID:** `STU001`
- **Password:** `student123`
- **Checkbox:** Leave "Admin Login" unchecked

### Admin Login
- **URL:** http://localhost:3000/login
- **ID:** `admin`
- **Password:** `admin123`
- **Checkbox:** Check "Admin Login"

---

## Testing Backend

### Health Check (Test if backend is running):
```
http://localhost:5000/api/health
```

Expected response:
```json
{
  "status": "OK",
  "message": "Server is running"
}
```

---

## Important Notes

- Make sure **backend is running** on port 5000 before accessing frontend
- Make sure **frontend is running** on port 3000
- Backend API is accessible at: `http://localhost:5000/api/*`
- Frontend proxies API calls through Vite dev server
- All API calls from frontend go to `/api/*` which is proxied to `http://localhost:5000/api/*`
