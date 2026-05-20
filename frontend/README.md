# 🎨 User Management Frontend

A sleek, responsive single-page web client built using React, Vite, Tailwind CSS v4, and React Router v7.

---

## 🛠️ Technology Stack
- **React (v19)**: Component-based UI library.
- **Vite (v7)**: Blazing-fast development server and bundle tool.
- **Tailwind CSS (v4)**: Modern, highly customizable utility CSS engine.
- **React Router (v7)**: Handles routing, navigation state, and deep linking.
- **React Hook Form (v7)**: Easy-to-use form registration, state tracking, and validations.

---

## 📂 Source Code structure

```text
frontend/src/
├── components/
│   ├── RootLayout.jsx  # Primary app layout wrapper with Header and Footer
│   ├── Header.jsx      # Navigation bar with active-link styles
│   ├── Footer.jsx      # Simple copyright footer
│   ├── Home.jsx        # Landing page layout
│   ├── AddUser.jsx     # Form component to create a new user profile
│   ├── UsersList.jsx   # Grid view rendering list of active users
│   └── User.jsx        # Detailed profile page for a selected user
├── App.jsx             # React Router v7 browser router configuration
├── main.jsx            # Main app launcher
├── index.css           # Tailwind v4 import directives
└── App.css             # Component-level styles
```

---

## 🔗 Route Map

React Router v7 orchestrates pages in a child routing structure inside [App.jsx](file:///c:/Users/ppooj/OneDrive/Desktop/ATP-SUNTEK/USER-MANAGEMENT-APP/frontend/src/App.jsx):

| Relative Path | Routed Component | Description |
| :--- | :--- | :--- |
| `/` | `Home` | Landing dashboard/welcome page. |
| `/add-user` | `AddUser` | Form to register/validate user records. |
| `/users-list` | `UsersList` | Grid representation of active database users. |
| `/user` | `User` | Selected profile view, utilizing route location state. |

---

## 🚀 Key Features

### 1. Simple Form Submission & Validation (`AddUser.jsx`)
- Uses **React Hook Form** to register form elements (`name`, `email`, `dateOfBirth`, `mobileNumber`).
- Posts validated payloads as JSON to the backend API (`POST http://localhost:4000/user-api/users`).
- Handles async `loading` and `error` states gracefully.
- Programmatically redirects to `/users-list` upon successful profile creation.

### 2. Active User Directory (`UsersList.jsx`)
- Performs an asynchronous `GET` call to the server when loaded.
- Maps user payloads to responsive cards using a CSS Grid container (`grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4`).
- Implements state transition to `/user` utilizing React Router state props when clicking user cards.

### 3. Deep Profile Detail Display (`User.jsx`)
- Receives rich model state safely from `useLocation()`.
- Dynamically prints details of the user: Name, Email, Date of Birth, and Mobile Number.

### 4. Dynamic Header (`Header.jsx`)
- Highlights active states on links cleanly using React Router's dynamic CSS callback:
  ```jsx
  className={({ isActive }) => (isActive ? "bg-lime-500 text-lime-50 rounded-2xl p-2" : "")}
  ```

---

## ⚙️ Running Locally

Follow these steps to spin up the local development server:

1. Navigate to the frontend directory:
   ```bash
   cd frontend
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Run the hot-reloading development server:
   ```bash
   npm run dev
   ```
   Open [http://localhost:5173](http://localhost:5173) in your browser.

4. Build production files:
   ```bash
   npm run build
   ```
   The production-optimized static files will be placed in the `dist/` folder.
