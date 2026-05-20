# 👥 User Management Application

A full-stack web application designed for managing user profiles. Built with a modern, responsive frontend (React, Vite, and Tailwind CSS v4) and a robust backend API (Node.js, Express, MongoDB, and Mongoose).

## 🚀 Project Overview

This project provides a clean interface and backend service for:
- **Creating new users** with built-in validations (name, unique email, date of birth, and optional mobile number).
- **Listing all active users** in a responsive grid layout.
- **Viewing individual user profiles** dynamically.
- **Soft-deleting users** (hiding them from the active list without permanent deletion) and reactivating them.

---

## 📁 Repository Structure

```text
USER-MANAGEMENT-APP/
├── backend/                # Express API & Database models
│   ├── APIs/               # Express routing layers
│   │   └── UserAPI.js      # User CRUD endpoints
│   ├── models/             # Mongoose schemas
│   │   └── UserModel.js    # User schema & validations
│   ├── .env                # Backend environment configuration
│   ├── server.js           # Server entry point
│   ├── package.json        # Backend dependencies & scripts
│   └── req.http            # HTTP request samples (for REST Client)
│
├── frontend/               # React client app
│   ├── public/             # Static public assets
│   ├── src/                # React source files
│   │   ├── components/     # UI Components (AddUser, UsersList, User, Header, etc.)
│   │   ├── App.jsx         # App router setup (React Router v7)
│   │   ├── main.jsx        # Client entry point
│   │   └── index.css       # Tailwind CSS v4 imports
│   ├── package.json        # Frontend dependencies & scripts
│   └── vite.config.js      # Vite compilation configurations
│
└── README.md               # Overall project documentation (this file)
```

---

## ⚡ Quick Start Guide

To run this application locally, you will need **Node.js** and a running **MongoDB** instance installed on your system.

### Step 1: Clone the Repository
```bash
git clone https://github.com/Poojitha0908/User-Management-App.git
cd User-Management-App
```

### Step 2: Set Up the Backend
1. Navigate to the backend folder:
   ```bash
   cd backend
   ```
2. Install the backend dependencies:
   ```bash
   npm install
   ```
3. Configure the environment variables. Ensure you have a `.env` file in the `backend` folder:
   ```env
   DB_URL=mongodb://localhost:27017/users-db
   PORT=4000
   ```
4. Start the backend server:
   ```bash
   # Run with nodemon for hot-reloads:
   npx nodemon server.js
   
   # Or run with node directly:
   node server.js
   ```
   The backend will be running at [http://localhost:4000](http://localhost:4000).

### Step 3: Set Up the Frontend
1. Open a new terminal and navigate to the frontend folder:
   ```bash
   cd/d c:\Users\ppooj\OneDrive\Desktop\ATP-SUNTEK\USER-MANAGEMENT-APP\frontend
   ```
2. Install the frontend dependencies:
   ```bash
   npm install
   ```
3. Start the Vite development server:
   ```bash
   npm run dev
   ```
   The frontend will be running at [http://localhost:5173](http://localhost:5173).

---

## 🛠️ Technology Stack

### Frontend
- **React 19**: A powerful JS library for building user interfaces.
- **Vite 7**: A blazing-fast frontend build tool.
- **Tailwind CSS v4**: Utility-first CSS framework for clean, modern design.
- **React Router v7**: Declarative routing for single-page applications.
- **React Hook Form**: Performant and flexible form validations.

### Backend
- **Node.js**: JavaScript runtime environment.
- **Express 5**: Fast, unopinionated, minimalist web framework.
- **Mongoose 9**: Elegant MongoDB object modeling for Node.js.
- **MongoDB**: NoSQL database for flexible user data storage.
- **dotenv**: Zero-dependency module that loads environment variables from a `.env` file.

---

## 📚 Component Overview

For detailed documentation, please check the individual module READMEs:
- 📖 [Frontend README](./frontend/README.md) - Learn about React components, routing, and form validation.
- 📖 [Backend README](./backend/README.md) - Learn about API routes, MongoDB schema, and request verification.
