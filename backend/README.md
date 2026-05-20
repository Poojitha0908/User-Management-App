# ⚙️ User Management Backend API

A robust RESTful API built using Node.js, Express, and MongoDB/Mongoose. This backend handles user data management, ensures data validation constraints, and implements soft-deleting workflows.

---

## 🛠️ Technology Stack
- **Node.js**: Server environment.
- **Express.js (v5)**: Fast web framework for backend routing.
- **MongoDB**: NoSQL database for flexible storage.
- **Mongoose (v9)**: Schema-based object modeling.
- **dotenv**: Environment variable manager.
- **cors**: Cross-Origin Resource Sharing middleware enabling safe cross-domain requests from the Vite frontend.
- **nodemon**: Dev tool for auto-restarting the server on file changes.

---

## ⚙️ Environment Configuration

The backend reads configuration from a `.env` file at the root of the `/backend` directory.

Create a `.env` file with:
```env
DB_URL=mongodb://localhost:27017/users-db
PORT=4000
```
- `DB_URL`: The connection string for your MongoDB instance.
- `PORT`: The local port number on which the server will listen (defaults to `4000` in standard setup).

---

## 📊 Database Schema (Mongoose)

### UserModel (`user` collection)
Defined in [UserModel.js](file:///c:/Users/ppooj/OneDrive/Desktop/ATP-SUNTEK/USER-MANAGEMENT-APP/backend/models/UserModel.js) with standard validations:

| Field Name | Data Type | Required | Unique | Default Value | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **name** | `String` | Yes | No | - | Error message: "Name is required" |
| **email** | `String` | Yes | Yes | - | Error message: "Email is required" / unique check |
| **dateOfBirth** | `Date` | Yes | No | - | Error message: "Date of Birth required" |
| **mobileNumber** | `Number` | No | No | - | Optional field |
| **status** | `Boolean` | No | No | `true` | Used for soft deletion (e.g., `false` = deleted) |

*Additional configurations: `timestamps: true` (auto manages `createdAt` and `updatedAt`), `versionKey: false` (removes `__v`), and `strict: "throw"` (strict validation).*

---

## 📡 API Reference

All routes are prefixed with `/user-api` and defined in [UserAPI.js](file:///c:/Users/ppooj/OneDrive/Desktop/ATP-SUNTEK/USER-MANAGEMENT-APP/backend/APIs/UserAPI.js).

### Endpoints Map

| HTTP Method | Route Endpoint | Request Body | Success Code | Description |
| :--- | :--- | :--- | :--- | :--- |
| **POST** | `/user-api/users` | JSON User Object | `201 Created` | Creates a new user in the database. |
| **GET** | `/user-api/users` | None | `200 OK` | Fetches all active users (`status: true`). |
| **GET** | `/user-api/users/:id` | None | `200 OK` | Retrieves a single active user by their MongoDB `_id`. |
| **DELETE** | `/user-api/users/:id` | None | `200 OK` | Soft-deletes a user by updating `status` to `false`. |
| **PATCH** | `/user-api/users/:id` | None | `200 OK` | Reactivates a user by updating `status` to `true`. |

---

## ⚠️ Error Handling Middleware

The API features an Express-level centralized error-handling middleware that catches and handles asynchronous database/server errors gracefully:
1. **Mongoose ValidationError (`400 Bad Request`)**: Triggered when required fields are missing or data types fail constraints.
2. **Mongoose CastError (`400 Bad Request`)**: Triggered when a malformed MongoDB ObjectID is supplied in the URL params.
3. **Duplicate Key `11000` (`409 Conflict`)**: Triggered when an attempt is made to insert an email that already exists.
4. **General Errors (`500 Internal Server Error`)**: Catch-all for uncaught application faults.

---

## 🧪 Testing with REST Client

A request collection file [req.http](file:///c:/Users/ppooj/OneDrive/Desktop/ATP-SUNTEK/USER-MANAGEMENT-APP/backend/req.http) is included in the directory. You can use VS Code's **REST Client** extension to fire requests directly against the local server.

Example request from `req.http`:
```http
### Create User
POST http://localhost:4000/user-api/users
Content-Type: application/json

{
    "name":"ravi",
    "email":"ravi@mail.com",
    "dateOfBirth":"09-08-2222",
    "mobileNumber":"9999999999"
}
```

---

## 🚀 Running the Server

1. Navigate to the backend folder:
   ```bash
   cd backend
   ```
2. Install npm packages:
   ```bash
   npm install
   ```
3. Run the development server (auto-reloading):
   ```bash
   npx nodemon server.js
   ```
4. Run the production server:
   ```bash
   node server.js
   ```
