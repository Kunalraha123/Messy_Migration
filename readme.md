# User Management API - Refactored

This is a refactored version of a legacy User Management API. It provides RESTful endpoints for user CRUD operations, login, and search functionality.

---

## 🚀 Getting Started

### ✅ Prerequisites
- Python 3.8+
- `pip` installed

### 📦 Installation
```bash
# Clone the repository
https://github.com/your-username/user-management-api.git
cd user-management-api

# Install dependencies
pip install -r requirements.txt
```

### 🛠️ Setup the Database
```bash
# You must have a SQLite database named 'users.db'
# Use init_db.py or any preferred method to create it with the required schema
```

### ▶️ Running the App
```bash
python app.py
```
The app will start on `http://localhost:5009`

---

## 📌 Available API Endpoints

| Method | Endpoint             | Description                   |
|--------|----------------------|-------------------------------|
| GET    | `/`                  | Health check                  |
| GET    | `/users`             | Fetch all users               |
| GET    | `/user/<id>`         | Fetch specific user by ID     |
| POST   | `/users`             | Create new user               |
| PUT    | `/user/<id>`         | Update user by ID             |
| DELETE | `/user/<id>`         | Delete user by ID             |
| GET    | `/search?name=`      | Search users by name          |
| POST   | `/login`             | Authenticate user login       |

All responses are returned in JSON format with proper HTTP status codes.

---

## 🔐 Security Improvements
- All SQL queries are parameterized
- Passwords are hashed before storage
- Plaintext passwords are never returned or stored

---

## 📄 Documentation
See `CHANGES.md` for a summary of refactoring decisions, improvements, and assumptions.

---

## 🤖 AI Disclosure
- Used ChatGPT to assist with refactoring guidance, code optimization, and documentation clarity.

---

## 📬 Questions?
Please contact [your email or GitHub handle here].

