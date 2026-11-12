# MERN Sign Up Starter

A sign-up flow built with React (Vite), Express, a REST API, MongoDB/Mongoose, bcrypt password hashing, and JWT authentication. The form is styled to match the supplied reference image.

## Requirements
- Node.js 18+ and npm
- MongoDB running locally, or a MongoDB Atlas connection string

## 1. Configure the backend
```bash
cd server
npm install
```
Copy `.env.example` to `.env` and set `MONGODB_URI` and a long random `JWT_SECRET`.

Start the API:
```bash
npm run dev
```
The API runs at `http://localhost:5000`.

## 2. Configure the frontend
Open a second terminal:
```bash
cd client
npm install
npm run dev
```
Open the Vite URL printed in the terminal (usually `http://localhost:5173`).

## REST endpoint
`POST /api/auth/signup`

Request JSON:
```json
{
  "email": "person@example.com",
  "password": "StrongPass123!"
}
```

Success response (201):
```json
{
  "message": "Account created successfully.",
  "user": { "id": "...", "email": "person@example.com" },
  "token": "..."
}
```

Possible errors include 400 for invalid/missing fields, 409 for an email already registered, and 500 for unexpected server errors. Passwords are hashed with bcrypt and are never returned by the API.

## Notes for production
- Use HTTPS and a strong, unique JWT secret stored in a secret manager.
- Consider placing JWTs in secure, HttpOnly cookies instead of browser storage.
- Add email verification, rate limiting, password reset, logging, and automated tests before production use.
- Never commit `.env` or real credentials.
