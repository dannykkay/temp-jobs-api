# Jobs API

A RESTful API for managing job listings, built with Node.js, Express, and MongoDB. Supports user authentication via JWT and full CRUD operations on job entries.

---

## Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [Environment Variables](#environment-variables)
- [API Reference](#api-reference)
  - [Authentication](#authentication)
  - [Jobs](#jobs)
- [Project Structure](#project-structure)
- [Live Demo](#live-demo)

---

## Features

- User registration and login with JWT authentication
- Create, read, update, and delete job listings
- Each user only manages their own jobs
- Swagger/OpenAPI documentation
- Error handling middleware
- Deployable via Procfile (e.g. Heroku, Render)

---

## Tech Stack

- **Runtime:** Node.js
- **Framework:** Express.js
- **Database:** MongoDB (via Mongoose)
- **Authentication:** JSON Web Tokens (JWT)
- **API Docs:** Swagger UI (OpenAPI 3.0)

---

## Getting Started

### Prerequisites

- Node.js (v14+)
- A MongoDB instance (local or cloud, e.g. MongoDB Atlas)

### Installation

1. Clone the repository:

```bash
git clone https://github.com/dannykkay/temp-jobs-api.git
cd temp-jobs-api
```

2. Create a `.env` file in the root directory with the following variables:

```env
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
```

3. Install dependencies and start the server:

```bash
npm install && npm start
```

The server will start and connect to MongoDB. By default it runs on `http://localhost:3000`.

---

## Environment Variables

| Variable    | Description                          |
|-------------|--------------------------------------|
| `MONGO_URI` | MongoDB connection string            |
| `JWT_SECRET`| Secret key used to sign JWT tokens   |

---

## API Reference

Base URL: `https://temp-jobs-api-1-i2ch.onrender.com/api/v1`

All **Jobs** endpoints require a Bearer token in the `Authorization` header:

```
Authorization: Bearer <your_token>
```

---

### Authentication

#### Register User

```
POST /auth/register
```

**Request Body:**

```json
{
  "name": "bob",
  "email": "bob@gmail.com",
  "password": "secret"
}
```

---

#### Login User

```
POST /auth/login
```

**Request Body:**

```json
{
  "email": "bob@gmail.com",
  "password": "secret"
}
```

**Response:** Returns a JWT token to use for authenticated requests.

---

### Jobs

#### Get All Jobs

```
GET /jobs
```

Returns all jobs belonging to the authenticated user.

---

#### Create Job

```
POST /jobs
```

**Request Body:**

```json
{
  "company": "Google",
  "position": "Front-End Developer"
}
```

---

#### Get Single Job

```
GET /jobs/:id
```

Returns a single job by its ID.

---

#### Update Job

```
PATCH /jobs/:id
```

**Request Body:**

```json
{
  "company": "Random Corp",
  "position": "Intern"
}
```

---

#### Delete Job

```
DELETE /jobs/:id
```

Deletes the job with the given ID.

---

## Project Structure

```
temp-jobs-api/
├── controllers/      # Route handler logic
├── db/               # Database connection setup
├── errors/           # Custom error classes
├── middleware/       # Auth and error-handling middleware
├── models/           # Mongoose schemas
├── routes/           # Express route definitions
├── app.js            # App entry point
├── swagger.yaml      # OpenAPI 3.0 spec
├── Procfile          # Deployment process file
└── package.json
```

---

## Live Demo

The API is deployed on Render:

**Base URL:** `https://temp-jobs-api-1-i2ch.onrender.com/api/v1`

Swagger documentation is available via the `/api-docs` endpoint (if configured in the app).
