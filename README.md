# PeopleDesk — Enterprise Employee Management System

> **Week-2 Assignment - 2 Submission**  
> **Author**: Rohit Satras  
> **Repository**: Full-Stack CRUD Employee Management System (MERN Stack)

[![Node.js Version](https://img.shields.io/badge/Node.js-v18+-339933?logo=node.js)](https://nodejs.org)
[![Express.js](https://img.shields.io/badge/Express.js-v4.21+-000000?logo=express)](https://expressjs.com)
[![MongoDB](https://img.shields.io/badge/MongoDB-v6.0+-47A248?logo=mongodb)](https://www.mongodb.com)
[![Mongoose](https://img.shields.io/badge/Mongoose-v8.9+-880000?logo=mongoose)](https://mongoosejs.com)
[![Vanilla JS](https://img.shields.io/badge/Frontend-HTML5%20%7C%20CSS3%20%7C%20Vanilla%20JS-F7DF1E?logo=javascript)](https://developer.mozilla.org)
[![Postman Tested](https://img.shields.io/badge/Postman-Verified%20Collection-FF6C37?logo=postman)](https://www.postman.com)

**PeopleDesk** is a modern, responsive, full-stack Human Resources Employee Management System (EMS) designed for HR administrators to manage employee lifecycle records with high-performance persistence in **MongoDB**.

Built strictly with clean **Vanilla JavaScript (ES6+)**, **HTML5**, **CSS3**, and a modular **Node.js/Express/Mongoose** backend architecture, PeopleDesk delivers a polished SaaS dashboard experience without framework overhead.

---

## ⚡ Quick Start

```bash
# 1. Enter the backend folder
cd employee-management-system/backend

# 2. Install dependencies
npm install

# 3. Configure environment file
# On Windows (PowerShell):
Copy-Item .env.example .env
# On Linux / macOS:
# cp .env.example .env

# 4. Start the server (with auto-reload)
npm run dev

# 5. Open in browser:
# Navigate to http://localhost:5000
```
*(If you do not have a local MongoDB instance installed, run `npm run dev:mem` instead for zero-setup in-memory database!)*

---

## 📸 Screenshots & Interface Showcase

### 1. SaaS Dashboard Overview
*Real-time summary statistics (Total Employees, Departments Represented, Total Monthly Payroll in INR) calculated directly via MongoDB aggregations, paired with a dynamic data table.*
![Dashboard Overview](employee-management-system/screenshots/dashboard_overview.png)

### 2. Live Debounced Search & Filter
*Case-insensitive real-time search across employee name, department, and job role with 300ms debounce and AbortController race-condition prevention.*
![Live Search](employee-management-system/screenshots/search_and_filter.png)

### 3. Add Employee Modal
*Accessible modal dialog featuring real-time client-side validation, currency formatting, department picker, and keyboard navigation.*
![Add Employee Modal](employee-management-system/screenshots/add_employee_modal.png)

### 4. Dynamic Directory Update
*Instant UI feedback with toast notifications, badge counter increment, payroll recalculation, and zero duplicate entries.*
![Employee Created](employee-management-system/screenshots/employee_created.png)

---

## 🌟 Key Features

### Complete CRUD Lifecycle
- **Create**: Add new employee records with strict validation (full name, department, job role, monthly salary, and past/present joining date).
- **Read**: View employee records in an enterprise data table with generated circular initials avatars, department badges, and formatted INR currency.
- **Update**: Edit any existing employee record using a pre-populated modal form without creating duplicate records.
- **Delete**: Safely delete employee records following explicit two-step user confirmation with safety warnings.

### Real-Time Search & Multi-Field Sorting
- **Case-Insensitive Search**: Search dynamically across `name`, `department`, and `role`.
- **Debounced Input**: Built-in 300ms debounce prevents unnecessary API flooding.
- **Race Condition Prevention**: Employs `AbortController` and search sequence counters to cancel outdated in-flight requests.
- **Multi-Field Sorting**: Sort by Recently Created, Name (A-Z / Z-A), Salary (High-Low / Low-High), Joining Date (Newest/Oldest), and Department.

### Dynamic Summary Metrics
- **Total Employees**: Count of active staff records.
- **Departments Represented**: Count of distinct active departments across the organization.
- **Total Monthly Payroll**: Real-time sum of monthly salaries formatted in Indian Rupees (`₹XX,XXX`) with Indian number grouping (`en-IN`).
- Metric cards reflect the entire database state even when table filtering is active.

### Production-Grade Backend Architecture
- Separation of concerns: Routes, Controllers, Models, Validators, and Middleware.
- Server-side input sanitization, field allowlisting, and MongoDB operator injection prevention (`$where`, `$gt`).
- Centralized error handling that returns field-specific validation errors and hides stack traces in production.
- Rate limiting (`express-rate-limit`) and security HTTP headers (`helmet`).

---

## 🛠️ Technology Stack

| Layer | Technologies Used |
|---|---|
| **Frontend** | HTML5 (Semantic), Vanilla CSS3 (Custom Design System, CSS Variables), Vanilla JavaScript (ES6+), Fetch API |
| **Icons & Fonts** | Google Fonts (Inter), Lucide Icons (CDN with inline fallback) |
| **Backend** | Node.js (v18+), Express.js (v4.21+), Mongoose ODM (v8.9+) |
| **Database** | MongoDB (Local Community Server, MongoDB Atlas, or Embedded In-Memory Runner) |
| **Testing** | Jest, Supertest, MongoDB Memory Server (19 Automated Tests) |
| **API Testing** | Postman Collection v2.1 |

---

## 📁 Project Directory Structure

```text
week-2 Assignment - 2/
├── employee-management-system/
│   ├── frontend/
│   │   ├── index.html                  # Accessible semantic dashboard UI
│   │   ├── style.css                   # Enterprise SaaS CSS3 design system
│   │   └── script.js                   # Application controller, API client, & state
│   ├── backend/
│   │   ├── models/
│   │   │   └── Employee.js             # Mongoose Employee model with schema indexes
│   │   ├── routes/
│   │   │   └── employeeRoutes.js       # Express router definitions
│   │   ├── controllers/
│   │   │   └── employeeController.js   # CRUD & aggregation business logic
│   │   ├── middleware/
│   │   │   ├── errorHandler.js         # Centralized error handler
│   │   │   └── notFound.js             # 404 handler for undefined endpoints
│   │   ├── validators/
│   │   │   └── employeeValidator.js    # Strict payload sanitization & ObjectId checks
│   │   ├── scripts/
│   │   │   └── seed.js                 # Realistic sample database seeder
│   │   ├── tests/
│   │   │   └── employee.test.js        # 19 automated API tests (Jest + Supertest)
│   │   ├── .env.example                # Safe environment variables template
│   │   ├── .gitignore                  # Backend ignore rules
│   │   ├── package.json                # Dependencies and npm run scripts
│   │   └── server.js                   # Express server entry point & DB connection
│   ├── postman/
│   │   └── Employee_API.postman_collection.json  # Complete Postman test collection
│   ├── screenshots/                    # Genuine application screenshots
│   │   ├── dashboard_overview.png
│   │   ├── search_and_filter.png
│   │   ├── add_employee_modal.png
│   │   └── employee_created.png
│   └── .gitignore                      # Subfolder gitignore rules
├── .gitignore                          # Repository gitignore rules
└── README.md                           # Master Project Documentation
```

---

## 📋 Prerequisites

Before running the project, verify that the following dependencies are installed on your machine:
- **Node.js**: `v18.0.0` or higher (`node -v`)
- **npm**: `v9.0.0` or higher (`npm -v`)
- **MongoDB**: Either local MongoDB Server (`mongod`), MongoDB Atlas connection URI, or use our zero-setup in-memory demonstration command (`npm run dev:mem`).

---

## 🚀 Installation & Setup Instructions

### Step 1: Navigate to the Backend Directory
```bash
cd employee-management-system/backend
```

### Step 2: Install Node Dependencies
```bash
npm install
```

### Step 3: Configure Environment Variables
Copy the template configuration file to `.env`:
```bash
# On Windows (PowerShell):
Copy-Item .env.example .env

# On Linux/macOS:
cp .env.example .env
```

Review and adjust `.env` variables if necessary:
```env
PORT=5000
NODE_ENV=development
MONGODB_URI=mongodb://127.0.0.1:27017/peopledesk
CLIENT_URL=http://localhost:3000
```

---

## 🗄️ Database Configuration

### Option A: Local MongoDB Installation
1. Ensure your MongoDB service is running:
   ```bash
   # Windows PowerShell (if MongoDB service installed):
   Start-Service -Name MongoDB
   # Or run manually:
   mongod --dbpath "C:\data\db"
   ```
2. Set `MONGODB_URI=mongodb://127.0.0.1:27017/peopledesk` in your `.env`.

### Option B: MongoDB Atlas (Cloud)
1. Log in to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas).
2. Create a free M0 cluster and set up a database user with password.
3. In **Network Access**, whitelist your IP address (or `0.0.0.0/0` for development).
4. Copy your connection string and update `.env`:
   ```env
   MONGODB_URI=mongodb+srv://<username>:<password>@cluster0.xxxx.mongodb.net/peopledesk?retryWrites=true&w=majority
   ```

### Option C: Instant Zero-Setup Demonstration Runner (No Local MongoDB Required)
If you do not have MongoDB installed locally, run:
```bash
npm run dev:mem
```
This automatically boots a real embedded MongoDB process in the background for zero-friction evaluation.

---

## 🖥️ Running the Application

### 1. Seed Initial Realistic Sample Data (Optional)
Populate realistic employee records across all 6 departments:
```bash
npm run seed
```

### 2. Start the Backend Server
```bash
# Standard startup (connects to MONGODB_URI in .env):
npm start

# Or with live auto-reload:
npm run dev

# Or with embedded in-memory MongoDB:
npm run dev:mem
```
The server will output:
```text
🚀 PeopleDesk Server running in DEVELOPMENT mode
📡 Base API URL: http://localhost:5000/api
🩺 Health Check: http://localhost:5000/api/health
👥 Employees API: http://localhost:5000/api/employees
💻 Frontend Client: http://localhost:5000
```

### 3. Open the Frontend Application
You can view the frontend in any of these ways:
- **Directly via the backend server**: Open [http://localhost:5000](http://localhost:5000) in your web browser.
- **Using VS Code Live Server**: Right-click `employee-management-system/frontend/index.html` and choose **Open with Live Server** (served at `http://127.0.0.1:5500`).
- **Direct file opening**: Double-click `employee-management-system/frontend/index.html` to open in your browser.

---

## 🧪 Automated Testing

A complete test suite of 19 automated tests verifies all CRUD operations, search, sorting, sanitization, and edge cases:
```bash
npm test
```

### Test Coverage Summary:
- `GET /api/health` — Verifies 200 OK and live database status.
- `POST /api/employees` — Tests successful creation (HTTP 201).
- `POST /api/employees` — Tests validation errors (missing name, invalid department, negative salary, future join date) (HTTP 400).
- `POST /api/employees` — Tests NoSQL injection prevention (stripping `$where` and operator keys).
- `GET /api/employees` — Tests retrieval and global summary metrics calculation.
- `GET /api/employees?search=...` — Tests case-insensitive search by name, role, and department.
- `GET /api/employees?sortBy=...` — Tests sorting order and rejection of unapproved sort fields.
- `GET /api/employees/:id` — Tests retrieval by ID, malformed ObjectId handling (HTTP 400), and missing ID (HTTP 404).
- `PUT /api/employees/:id` — Tests updating existing records without creating duplicates.
- `DELETE /api/employees/:id` — Tests deletion and idempotency (HTTP 404 on already deleted records).

---

## 📬 Postman API Testing

An importable collection is located at:
`employee-management-system/postman/Employee_API.postman_collection.json`

### Importing into Postman:
1. Open Postman.
2. Click **Import** in the upper left.
3. Select `employee-management-system/postman/Employee_API.postman_collection.json`.
4. The collection is pre-configured with two collection variables:
   - `baseUrl`: `http://localhost:5000/api`
   - `employeeId`: Automatically populated when running Request 2 ("Create Employee").

### Request Execution Order:
| # | Request Name | Method | URL | Expected Status |
|---|---|---|---|---|
| 1 | Health Check | `GET` | `{{baseUrl}}/health` | `200 OK` |
| 2 | Create Employee | `POST` | `{{baseUrl}}/employees` | `201 Created` |
| 3 | Get All Employees & Summary | `GET` | `{{baseUrl}}/employees` | `200 OK` |
| 4 | Search Employees | `GET` | `{{baseUrl}}/employees?search=Engineer` | `200 OK` |
| 5 | Sort Employees by Salary | `GET` | `{{baseUrl}}/employees?sortBy=salary&order=desc` | `200 OK` |
| 6 | Get Single Employee by ID | `GET` | `{{baseUrl}}/employees/{{employeeId}}` | `200 OK` |
| 7 | Update Employee | `PUT` | `{{baseUrl}}/employees/{{employeeId}}` | `200 OK` |
| 8 | Delete Employee | `DELETE` | `{{baseUrl}}/employees/{{employeeId}}` | `200 OK` |
| 9 | Invalid Payload Validation | `POST` | `{{baseUrl}}/employees` | `400 Bad Request` |
| 10 | Malformed ObjectId Validation | `GET` | `{{baseUrl}}/employees/invalid-object-id-12345` | `400 Bad Request` |
| 11 | Missing Employee Record | `GET` | `{{baseUrl}}/employees/507f1f77bcf86cd799439011` | `404 Not Found` |

---

## 📡 REST API Reference

**Base URL**: `http://localhost:5000/api`

### 1. Health Status
`GET /health`
- **Response** (`200 OK`):
  ```json
  {
    "success": true,
    "status": "UP",
    "message": "PeopleDesk API is healthy and connected to MongoDB",
    "timestamp": "2026-10-23T10:45:00.000Z",
    "uptime": "120s",
    "database": {
      "status": "Connected",
      "host": "127.0.0.1",
      "name": "peopledesk"
    }
  }
  ```

### 2. Create Employee
`POST /employees`
- **Request Body**:
  ```json
  {
    "name": "Aarav Sharma",
    "department": "IT",
    "role": "Senior Full Stack Engineer",
    "salary": 145000,
    "joinDate": "2023-01-15"
  }
  ```
- **Response** (`201 Created`):
  ```json
  {
    "success": true,
    "message": "Employee created successfully",
    "data": {
      "_id": "6adb3dffd83ebf12b2782261",
      "name": "Aarav Sharma",
      "department": "IT",
      "role": "Senior Full Stack Engineer",
      "salary": 145000,
      "joinDate": "2023-01-15T00:00:00.000Z",
      "createdAt": "2026-10-23T10:46:00.000Z",
      "updatedAt": "2026-10-23T10:46:00.000Z"
    }
  }
  ```

### 3. Get All Employees & Summary Stats
`GET /employees`
- **Query Parameters**:
  - `search`: Filter by name, department, or job role (e.g. `?search=Priya`).
  - `sortBy`: Field to sort by (`name`, `department`, `role`, `salary`, `joinDate`, `createdAt`).
  - `order`: Sort direction (`asc` or `desc`).
  - `page`: Page number (optional).
  - `limit`: Records per page (optional).
- **Response** (`200 OK`):
  ```json
  {
    "success": true,
    "message": "Employees retrieved successfully",
    "count": 6,
    "total": 6,
    "summary": {
      "totalEmployees": 6,
      "totalPayroll": 663000,
      "departmentCount": 6
    },
    "data": [...]
  }
  ```

### 4. Get Employee by ID
`GET /employees/:id`
- **Parameters**: `id` (24-character hexadecimal MongoDB ObjectId).
- **Response** (`200 OK` or `404 Not Found`).

### 5. Update Employee
`PUT /employees/:id`
- **Request Body**: Updated employee payload (all 5 fields).
- **Response** (`200 OK`):
  ```json
  {
    "success": true,
    "message": "Employee updated successfully",
    "data": { ... }
  }
  ```

### 6. Delete Employee
`DELETE /employees/:id`
- **Response** (`200 OK`):
  ```json
  {
    "success": true,
    "message": "Employee deleted successfully",
    "data": {
      "id": "6adb3dffd83ebf12b2782261",
      "name": "Aarav Sharma"
    }
  }
  ```

---

## 🔒 Security & Data Validation

- **NoSQL Injection Prevention**: Request bodies are filtered through an allowlist (`name`, `department`, `role`, `salary`, `joinDate`). Any keys starting with `$` or containing `.` are stripped before reaching Mongoose.
- **Strict Data Validation**:
  - `name`: String, 2–100 characters, trimmed, required.
  - `department`: Restricted to approved enum `['IT', 'HR', 'Finance', 'Marketing', 'Sales', 'Operations']`.
  - `role`: String, 2–100 characters, trimmed, required.
  - `salary`: Finite positive number between `0` and `100,000,000` (₹10 Crore INR).
  - `joinDate`: Valid date, not in the future (`<= today`).
- **Cross-Site Scripting (XSS) Prevention**: All client-side text insertions are sanitized through `escapeHTML()`. No untrusted input is interpolated into `innerHTML` without escaping.
- **DoS & Flooding Protection**:
  - Request body limit capped at `50kb`.
  - Rate limiting enforced at 300 requests per 15 minutes per IP.
- **Security Headers**: Express configured with `helmet` for secure header propagation.
- **Authentication Disclaimer**: The HR Administrator profile shown in the sidebar is for display and demonstration purposes. No authentication or authorization gates are implemented; all operations run in authenticated admin demo mode.

---

## 🔧 Common Errors & Troubleshooting

| Issue | Cause | Resolution |
|---|---|---|
| **MongoDB Connection Error** (`MongooseServerSelectionError`) | Local MongoDB service is not started on port 27017. | Start local MongoDB via `mongod` or run `npm run dev:mem` for zero-install embedded MongoDB. |
| **Port 5000 in use** (`EADDRINUSE`) | Another process is occupying port 5000. | Change `PORT=5001` in `.env` and update `CONFIG.API_BASE_URL` in `frontend/script.js`. |
| **CORS Blocked Error** in browser console | Frontend origin does not match `CLIENT_URL`. | Update `CLIENT_URL` in `.env` or access the app directly via `http://localhost:5000`. |
| **Validation 400 Error on Save** | Future joining date or negative salary entered. | Ensure the joining date is today or earlier, and salary is a non-negative number. |

---

## 🐙 Git and GitHub Readiness

This repository is prepared for Git and GitHub. All sensitive files (`.env`, `node_modules`, logs) are excluded by `.gitignore`.

To initialize and push this project to GitHub:
```bash
# 1. Initialize git repository (if not already initialized)
git init

# 2. Add all tracked files
git add .

# 3. Commit changes
git commit -m "feat: complete PeopleDesk Employee Management System with full CRUD and MongoDB"

# 4. Link your remote repository and push (replace with your repo URL)
git branch -M main
git remote add origin https://github.com/<your-username>/employee-management-system.git
git push -u origin main
```

---

## 🔮 Future Improvements
1. **JWT Authentication & RBAC**: Add secure login with role-based access control (Admin, HR Manager, Viewer).
2. **Employee Photo Uploads**: Support Cloudinary/AWS S3 for actual profile image uploads.
3. **CSV / Excel Export**: Enable one-click export of filtered employee lists to spreadsheet formats.
4. **Audit Log Trail**: Track user history of who created, edited, or deleted an employee record.

---

## 👤 Author
- **Developer**: Rohit Satras
- **Assignment**: Week-2 Assignment 2 — Full-Stack CRUD Employee Management System
- **Year**: 2026
