# Login Flow & Dashboard Pages

## What Happens After Login

### Student Login
1. Enter Student ID: `714023205119`
2. Enter Password: `student123`
3. **DO NOT** check "Admin Login" checkbox
4. Click "Login"
5. You will be redirected to: **Student Dashboard** (`/dashboard`)

### Admin Login
1. Enter Admin ID: `admin`
2. Enter Password: `admin123`
3. **CHECK** the "Admin Login" checkbox
4. Click "Login"
5. You will be redirected to: **Admin Dashboard** (`/admin`)

---

## Dashboard Pages Overview

### Student Dashboard (`/dashboard`)
Features available:
- ✅ Upload documents (PDF, JPG, PNG - Max 5MB)
- ✅ View your own documents
- ✅ Search documents by filename or category
- ✅ Filter documents by category
- ✅ Download your documents
- ✅ Delete your documents
- ✅ Pagination for document list
- ✅ Logout button

### Admin Dashboard (`/admin`)
Features available:
- ✅ View ALL documents from all students
- ✅ Search and filter documents
- ✅ Download any document
- ✅ Delete any document
- ✅ Reset student passwords
- ✅ View all registered students
- ✅ Two tabs: "All Documents" and "Manage Students"
- ✅ Logout button

---

## Troubleshooting

### If you don't see the dashboard after login:

1. **Check Browser Console (F12)**
   - Look for any JavaScript errors
   - Check Network tab for failed requests

2. **Check Backend Console**
   - Should show: `Server running on port 5000`
   - Should show: `MongoDB Connected`
   - Look for any error messages

3. **Verify Cookie is Set**
   - Open Browser DevTools (F12)
   - Go to Application/Storage tab
   - Check Cookies for `token` cookie
   - Should be present after successful login

4. **Check URL**
   - After login, URL should change to:
     - `/dashboard` for students
     - `/admin` for admins

5. **Try Manual Navigation**
   - If login succeeds but page doesn't load, try:
     - `http://localhost:3000/dashboard` (for students)
     - `http://localhost:3000/admin` (for admins)

---

## Quick Test

1. Start backend: `cd backend && npm run dev`
2. Start frontend: `cd frontend && npm run dev`
3. Open browser: `http://localhost:3000`
4. Login with credentials above
5. You should see the appropriate dashboard!
