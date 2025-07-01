# REST API Example: JWT Authentication

This is a simple Node.js REST API that demonstrates user registration, login, and JWT-protected profile access. User data is stored in an in-memory SQLite database.

## Getting Started

1. Install dependencies:
   ```bash
   npm install
   ```

2. Start the server:
   ```bash
   npm start
   ```
   The server runs at http://localhost:3000

## API Endpoints

### Register
- **POST** `/register`
- **Request Body:**
  ```json
  {
    "username": "your_username",
    "password": "your_password"
  }
  ```
- **Responses:**
  - `201 Created` — User registered
  - `409 Conflict` — Username already exists

### Login
- **POST** `/login`
- **Request Body:**
  ```json
  {
    "username": "your_username",
    "password": "your_password"
  }
  ```
- **Response:**
  ```json
  {
    "token": "<JWT token>"
  }
  ```
  The token is signed with `my_rest_api_secret_jwt_key_254!` and expires in 15 minutes.

### Get Profile (Requires Auth)
- **GET** `/profile`
- **Headers:**
  - `Authorization: Bearer <JWT token>`
- **Response:**
  ```json
  {
    "user": {
      "id": 1,
      "username": "your_username"
    }
  }
  ```

## Usage

This API does not include a frontend. Use tools like Postman, curl, or connect your own frontend app.

## Important
- The JWT secret is hardcoded for demonstration.
- User data is not persistent and will be lost when the server restarts.
