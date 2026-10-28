# MERN Stack - Sign Up Feature (Task 2)

This project implements a complete, end-to-end user **Sign Up** process using:
- **Frontend**: React (Vite) styled to match the minimalist underline input design.
- **Backend**: Express.js REST API running on Node.js.
- **Database**: MongoDB with Mongoose (with password encryption via `bcryptjs`).

---

## Project Structure

```text
mern task 2/
├── backend/
│   ├── config/
│   │   └── db.js            # MongoDB connection
│   ├── controllers/
│   │   └── authController.js# Registration logic (bcrypt hashing, validation)
│   ├── models/
│   │   └── User.js          # Mongoose User schema
│   ├── routes/
│   │   └── authRoutes.js    # POST /api/auth/signup route
│   ├── .env                 # PORT and MONGO_URI
│   ├── package.json
│   └── server.js            # Express app entry point
└── frontend/
    ├── index.html
    ├── package.json
    ├── vite.config.js
    └── src/
        ├── components/
        │   ├── SignUp.jsx   # Sign Up form with React state & API fetch
        │   └── SignUp.css   # Pixel-accurate underline input styling
        ├── App.jsx
        ├── App.css
        └── main.jsx
```

---

## How to Run

### 1. Start the Backend
Open a terminal in the root directory:
```bash
cd backend
npm install
npm run dev
```
* The backend will start on `http://localhost:5000`
* It connects automatically to MongoDB (`mongodb://127.0.0.1:27017/mern_signup_db`).
* If you are using MongoDB Atlas, update `MONGO_URI` in `backend/.env`.

---

### 2. Start the Frontend (React)
Open a second terminal:
```bash
cd frontend
npm install
npm run dev
```
* The frontend will start on `http://localhost:5173`.
* Open your browser and view the Sign Up page.

---

## Testing the Flow
1. Enter an **Email** (e.g. `alex@example.com`) and a **Password** (minimum 6 characters).
2. Click **Sign Up**.
3. **Verify in MongoDB**:
   - Open MongoDB Compass or your database shell.
   - Look inside `mern_signup_db` -> `users` collection.
   - The password field will be stored as an encrypted hash (e.g., `$2a$10$...`), **never** in plain text.
4. **Test Duplicate Prevention**:
   - Try signing up again with the exact same email.
   - Notice the error alert: *"An account with this email already exists."*
