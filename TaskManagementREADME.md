# Task Management System --- API Design

## 1. Project Structure
  task-management-api/
 ├── src/
 │ ├── config/
 │ │ └── db.js
 │ ├── controllers/
 │ │ ├── auth.controller.js
 │ │ ├── user.controller.js
 │ │ ├── project.controller.js
 │ │ └── task.controller.js
 │ ├── models/
 │ │ ├── User.js
 │ │ ├── Project.js
 │ │ └── Task.js
 │ ├── routes/
 │ │ ├── auth.routes.js
 │ │ ├── user.routes.js
 │ │ ├── project.routes.js
 │ │ └── task.routes.js
 │ ├── middleware/
 │ │ ├── auth.js
 │ │ └── errorHandler.js
 │ ├── utils/
 │ │ ├── sendNotification.js
 │ │ └── validateRequest.js
 │ └── app.js
 ├── .env
 ├── package.json
 └── README.md

## 2. Required Libraries (Enumerated with Explanation)

1.  express
    -   Framework for building API routes and handling HTTP requests.
2.  mongoose
    -   Manages MongoDB connections and schema-based models.
3.  dotenv
    -   Loads environment variables to protect sensitive data.
4.  bcryptjs
    -   Hashes and secures user passwords before saving them.
5.  jsonwebtoken
    -   Generates and verifies JWT tokens for authentication.
6.  cors
    -   Enables cross-origin access between backend and frontend.
7.  morgan
    -   Logs API requests for debugging and monitoring.
8.  cookie-parser
    -   Parses cookies when storing tokens in cookies.
9.  express-validator
    -   Validates user input in request bodies.
10. nodemailer
    -   Sends email notifications for reminders or invitations
11. node-cron
    -   Automates scheduled tasks like deadline reminders.

## 3. Database Models

### 3.1 User Model

1.  name: String
2.  email: String
3.  password: String
4.  avatar: String
5.  createdAt: Date

### 3.2 Project Model

1.  name: String
2.  description: String
3.  owner: ObjectId
4.  members: Array of User ObjectId
5.  createdAt: Date

### 3.3 Task Model

1.  title: String
2.  description: String
3.  status: \["todo", "in progress", "done"\]
4.  priority: \["low", "medium", "high"\]
5.  dueDate: Date
6.  project: ObjectId (Project)
7.  assignedTo: ObjectId (User)
8.  createdBy: ObjectId (User)
9.  createdAt: Date

## 4. API Endpoints (Enumeration)

### 4.1 Auth Endpoints

1.  POST /api/auth/register\
2.  POST /api/auth/login\
3.  GET /api/auth/me

### 4.2 User Endpoints

4.  GET /api/users\
5.  GET /api/users/:id

### 4.3 Project Endpoints

6.  POST /api/projects\
7.  GET /api/projects\
8.  GET /api/projects/:projectId\
9.  POST /api/projects/:projectId/invite

### 4.4 Task Endpoints

10. POST /api/tasks\
11. GET /api/tasks\
12. GET /api/tasks/:taskId\
13. PUT /api/tasks/:taskId\
14. DELETE /api/tasks/:taskId

## 5. Middleware

1.  auth.js\
2.  errorHandler.js\
3.  validateRequest.js

## 6. Authentication Strategy (JWT)

1.  User registers → password hashed.\
2.  User logs in → JWT generated.\
3.  Token sent in Authorization header.\
4.  Protected routes verify token.\
5.  Expired tokens rejected.

## 7. Error Handling

-   400 Bad Request\
-   401 Unauthorized\
-   403 Forbidden\
-   404 Not Found\
-   500 Server Error
