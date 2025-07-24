# CHANGES.md

## Overview
This document outlines the critical issues identified in the legacy codebase and details the improvements made during refactoring of the User Management API.

---

## 🔍 Major Issues Identified

### 1. SQL Injection Vulnerabilities
- SQL queries were constructed using Python f-strings, which are prone to injection attacks.

### 2. Plaintext Password Storage
- User passwords were stored and compared in plaintext, which is highly insecure.

### 3. Poor API Responses
- The original endpoints returned raw strings and tuples instead of structured JSON responses.

### 4. Missing HTTP Status Codes
- API responses did not return appropriate HTTP status codes (e.g., `404` for not found, `400` for bad request).

### 5. Unsafe Global Database Connection
- A global database connection (`check_same_thread=False`) was used, leading to potential concurrency issues.

### 6. Lack of Input Validation
- Incoming requests were not validated for required fields or correct types.

---

## ✅ Changes Made

### ✅ Database Query Security
- All SQL queries now use parameterized placeholders (`?`) to prevent SQL injection.

### ✅ Secure Password Storage
- Passwords are now hashed using `werkzeug.security.generate_password_hash` before storage.
- Passwords are verified using `check_password_hash` during login.

### ✅ API Response Formatting
- All API responses are now returned as JSON using `Flask.jsonify`.

### ✅ Proper HTTP Status Codes
- Responses now include appropriate HTTP codes: `200`, `201`, `400`, `401`, `404`.

### ✅ Safe DB Connection Handling
- A helper function `get_db_connection()` is used to create per-request connections.
- `conn.row_factory = sqlite3.Row` enables dict-like access to rows.

### ✅ Input Validation
- Checks added for missing or invalid inputs on all endpoints.
- Required fields are verified before performing database operations.

### ✅ Consistent and Clean Code
- Removed redundant print statements.
- Replaced manual JSON decoding with `request.get_json()`.
- Route methods accept and return cleaner data structures.

---

## 🧪 Assumptions and Trade-Offs
- Assumed user schema includes `id`, `name`, `email`, `password`.
- Did not implement advanced validation (e.g. email regex) due to time limit.
- No pagination or sorting was added for `/users` or `/search` endpoints.
- Focused only on server-side logic, no UI or frontend changes.

---

## 🚀 If Given More Time
- Modularize code into Blueprints (`auth.py`, `users.py`, etc.)
- Add unit and integration tests using `pytest` or `unittest`
- Use environment variables for database config and secrets
- Implement rate limiting and JWT-based authentication
- Add API documentation using Swagger / OpenAPI

---

## 🤖 AI Usage Disclosure
- Used ChatGPT for code review and security guidance
- AI-generated suggestions were reviewed and adapted to fit the context manually

