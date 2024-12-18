# Fullstack Todo App - Node.JS Express.JS Prisma PostgreSQL & Docker

This is a full-stack project using Node.js, Express.js, PostgreSQL, Prisma, and Docker

## **Overview**

This is an Dockerized and authentication-protected Todo App using Node.js, Express.js, bcrypt, JWT authentication, Prisma and PostgreSQL.

The app allows users to:

- register: create a new account,
- login: authenticate and receive a JWT token,
- manage list of todos: perform auth protected CRUD operations on their own todo tasks after logging in.

## Explanation of key directories and files

- **`prisma/`**: contains Prisma's schema (`schema.prisma`) and migration files. After each schema change, migration files are generated here to apply database changes.
- **`public/`**: contains the frontend HTML file. This file interacts with the backend API for user registration, login and todo management.
- **`src/`**: the core backend code.
  - **`middlewares/`**: contains middleware for handling JWT-based authentication, protecting routes that require authentication.
  - **`routes/`**: contains API routes for handling authentication and CRUD operations for todos.
  - **`prismaClient.js`**: sets up the Prisma client for database interaction.
  - **`server.js`**: the entry point for the Express.js application, which configures the app, routes and middleware.
- **`.env`**: stores environment variables like `DATABASE_URL` and `JWT_SECRET`. These variables are used to configure Prisma, JWT, and database connections.
- **`Dockerfile`**: the Dockerfile for building the Node.js application in a containerized environment.
- **`docker-compose.yaml`**: configuration for Docker Compose, which sets up both the Node.js app and PostgreSQL in separate containers.
- **`package.json`**: defines the Node.js dependencies and scripts used to run the application (e.g., `npm start`).
- **`README.md`**: project documentation, including setup instructions and directory structure.

## Run the application

1. Install Docker Desktop

2. Clone the repository:

```bash
git clone
cd
```

3. Generate the Prisma Client:

`npx prisma generate`

4. Build your docker images:

`docker compose build`

5. Create PostgreSQL migrations and apply them:

`docker compose run app npx prisma migrate dev --name init`

_Also_ - to run/apply migrations if necessary:

`docker-compose run app npx prisma migrate deploy`

6. Boot up docker containers:

`docker compose up`

## Browse database in Docker

```bash
docker exec -it postgres-db psql -U postgres -d todoapp
```
