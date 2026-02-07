# 📋 Student Document Store: The Ultimate Complete Prompt

Use the following mega-prompt to give any AI assistant full control and context over the entire project.

---

## 🚀 THE ULTIMATE MASTER PROMPT
> **Instruction:** Copy the entire block below into your AI assistant.

"Act as a Senior Lead Developer. I am building the **Student Document Store System**, a secure, production-ready MERN stack application. 

### 1. Project Core Objective
A centralized platform for educational institutions where **Students** can upload/manage their documents (Certificates, Marksheets, IDs) and **Admins** can perform oversight, bulk onboarding, and security management.

### 2. Technology Stack
- **Frontend:** React (Vite) + Tailwind CSS + Framer Motion. Axios for API.
- **Backend:** Node.js + Express + Mongoose.
- **Authentication:** JWT with HTTP-only, Secure, SameSite cookies. Role-based (Student/Admin).
- **File System:** Multer for storage; files stored at `backend/uploads/{studentId}/{category}/`.
- **Deployment:** Dockerized for Railway or Render.

### 3. Key Feature Specifications
- **Dual Login:** Student ID-based login for students; distinct Admin login.
- **Document CRUD:** Students can Upload (Max 5MB), Search, Filter (Category/Date), View, Download, and Delete their own docs.
- **Admin Oversight:** Global document view, student directory with partial ID matching, and remote password resets.
- **Bulk Onboarding:** Script-based user creation (e.g., seeding range `714023205119` to `714023205174`).
- **Profile Management:** Profile photo uploads and personal info updates.

### 4. Primary API Endpoints
- **Auth:** `POST /api/auth/login`, `POST /api/auth/admin/login`, `GET /api/auth/me`, `POST /api/auth/logout`.
- **Documents:** `POST /api/documents/upload`, `GET /api/documents/my-documents`, `GET /api/documents/download/:id`, `DELETE /api/documents/:id`.
- **Admin:** `GET /api/admin/documents`, `POST /api/admin/reset-password`, `GET /api/admin/students`, `POST /api/admin/students`.
- **Profile:** `GET /api/profile`, `PUT /api/profile`, `POST /api/profile/photo`.

### 5. Data Models (Schemas)
- **User Schema:** `studentId` (Unique), `password` (Hashed), `role` (student/admin), `name`, `email`, `department`, `year`, `profilePhoto`.
- **Document Schema:** `userId`, `studentId`, `title`, `filename`, `category` (marksheet/certificate/id), `filePath`, `fileSize`, `uploadDate`.

### 6. Security Standards
- **Middleware:** `auth.js` verifies tokens and resource ownership (Ownership checks: `doc.studentId === req.user.studentId`).
- **Validation:** Multer file type/size filters; path sanitization; executable file blocking.
- **Auditing:** `AuditLog` schema to track every login, upload, and deletion.

### 7. Design UI/UX Guidelines
Prioritize a **Sleek Dark Theme** with **Glassmorphism** effects. Use **Framer Motion** for smooth page transitions and micro-animations on buttons/hover states. Ensure full responsiveness for mobile and desktop."

---

## 🛠️ Implementation & Developer Guidelines
- **Project Structure:** Modular routes in `backend/routes`, Mongoose models in `backend/models`, and centralized API client in `frontend/src/utils/api.js`.
- **Error Handling:** Use a global error handler in `server.js` and consistent try-catch blocks in controllers.
- **State Management:** React `useState` and `useEffect` with dedicated `AuthContext` for user state.

