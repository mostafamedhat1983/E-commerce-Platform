# Modern E-commerce Platform with Docker Compose 🚀

A full-featured e-commerce platform built with AI, React, TypeScript, and modern web technologies.

<img width="1506" alt="shop" src="https://github.com/user-attachments/assets/f7a29e1f-5094-4d4d-bee6-ff1dff089a5a" />



## Features

- 🛍️ Product browsing with categories and filters
- 🔍 Advanced search functionality
- 🛒 Shopping cart management
- 💖 Wishlist functionality
- ⚖️ Product comparison
- 👤 User authentication
- 📦 Order management
- 💳 Checkout process
- 💬 Product reviews
- 🌐 Multi-currency support

## Tech Stack

- **Frontend Framework:** React 18
- **Type System:** TypeScript
- **Styling:** Tailwind CSS
- **State Management:** Zustand
- **Routing:** React Router
- **Icons:** Lucide React
- **Database:** MySQL 8.0
- **Build Tool:** Vite

# Docker Compose Configuration Explanation

## Overview
This `docker-compose.yml` file defines a multi-container Docker application with three services: `backend`, `frontend`, and `db` (MySQL database). It also sets up two networks (`frontend` and `backend`) and a persistent volume for MySQL data storage.

## Services

### Backend Service
- **Builds** from `./devops-backend` directory.
- **Exposes port** `8080` to the host machine.
- **Networks**:
  - Connected to both `frontend` and `backend` networks.
- **Depends on** the `db` service, ensuring it starts only after the database container is up.

### Frontend Service
- **Builds** from `./devops-frontend` directory.
- **Exposes port** `5174` to the host machine.
- **Depends on** the `backend` service, meaning it starts after the backend is running.
- **Connected to** the `frontend` network.

### Database (MySQL) Service
- **Uses the official MySQL 8.0 image**.
- **Container name** is set to `mysql_db`.
- **Environment Variables**:
  - `MYSQL_ROOT_PASSWORD`: Root password for MySQL.
  - `MYSQL_DATABASE`: Database name.
  - `MYSQL_USER`: Database user.
  - `MYSQL_PASSWORD`: Password for the user.
- **Exposes port** `3306`.
- **Uses a volume** (`mysql_data`) to persist MySQL data.
- **Connected to** the `backend` network with the alias `mysql`.

## Networks
- `frontend`: Used by `frontend` and `backend` services.
- `backend`: Used by `backend` and `db` services.

## Volumes
- `mysql_data`: Ensures MySQL data persistence between container restarts.

## Summary
This Docker Compose setup organizes a simple full-stack application with clear network separation and service dependencies. The MySQL service provides a persistent database, the backend interacts with the database, and the frontend connects to the backend, ensuring modular and scalable architecture.
