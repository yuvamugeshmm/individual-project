# Deployment Guide

This project is designed to be easily deployable to platforms like **Railway** or **Render**.

## Environment Variables

To ensure the application runs correctly in production, you must set the following environment variables in your deployment platform.

### Backend

| Variable | Description | Example |
|----------|-------------|---------|
| `PORT` | The port the backend should run on. | `5001` or `10000` |
| `MONGODB_URI` | Your MongoDB connection string. | `mongodb+srv://...` |
| `JWT_SECRET` | A secret key for JWT token generation. | `your_secret_key` |
| `FRONTEND_URL` | The URL of your deployed frontend. | `https://your-frontend.vercel.app` |

### Frontend

| Variable | Description | Example |
|----------|-------------|---------|
| `VITE_API_URL` | The full URL of your deployed backend API. | `https://your-backend.railway.app/api` |

---

## Deployment Platforms

### Railway (Recommended)

1. Connect your GitHub repository to Railway.
2. Railway will automatically detect the `Dockerfile` in both `frontend` and `backend` folders if you set them up as separate services.
3. For each service, go to **Variables** and add the variables listed above.

### Render (Recommended via Blueprint)

1. Connect your GitHub repository to Render.
2. Render will detect the `render.yaml` file automatically.
3. Click "Apply" to create the Blueprint environment.
4. Manually add your `MONGODB_URI` and `JWT_SECRET` in the Render Dashboard under **Environment** if not already prompted.

### Render (Manual Setup)

1. Create a **Web Service** for the backend (Root: `backend`).
2. Create a **Static Site** for the frontend (Root: `frontend`).
3. Set the build and start commands as defined in the `render.yaml` or `package.json`.
4. In the **Environment** tab of each service, add the required variables.

---

## Troubleshooting "API Error"

If you see an "API Error" after deployment:
1. Verify that `VITE_API_URL` in the frontend starts with `https://` and ends with `/api`.
2. Verify that `FRONTEND_URL` in the backend matches your frontend's deployment URL exactly (without a trailing slash).
3. Check the backend logs for "CORS" or "MongoDB Connection" errors.
