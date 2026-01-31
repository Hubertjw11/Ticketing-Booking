# 🎫 Ticketing Booking

This repository contains a **full-stack ticketing and booking application**. It features a high-performance Go backend and a sleek React Native mobile application designed for both event managers and attendees.

---

## 🛠 Tech Stack

| Component | Technologies |
| :--- | :--- |
| **Backend** | 🐹 `Go` · 🚀 `Fiber` · 🗄️ `GORM` · 🐘 `PostgreSQL` · 🔐 `JWT` · 🐳 `Docker` |
| **Frontend** | 📱 `React Native` · 🌌 `Expo` · 📘 `TypeScript` · 🔗 `Axios` |

---

## ✨ Features

* 🔐 **User Authentication**: Secure registration and login using **JWT** tokens.
* ⚖️ **Role-Based Access Control (RBAC)**:
    * 👨‍💼 **Manager**: Complete CRUD control over events and ticket validation.
    * 🎟️ **Attendee**: Browse events, purchase tickets, and manage their collection.
* 📅 **Event Management**: Full lifecycle management for events (Create, Read, Update, Delete).
* 🛒 **Ticket Purchasing**: Integrated flow for attendees to secure spots instantly.
* 🖼️ **QR Code Tickets**: Unique QR generation for every purchase to prevent fraud.
* 🔍 **Scanning & Validation**: In-app scanner for Managers to check-in attendees in real-time.

---

## 📁 Project Structure

The project is organized as a **monorepo** for easier development and deployment:

* 📂 `backend/`: The Go API engine. Handles business logic, database migrations, and security.
* 📂 `mobile/`: The cross-platform UI. A single codebase for both iOS and Android.

---

## 🚀 Getting Started

### 📋 Prerequisites

Before you begin, ensure you have the following installed:
* 🐳 **Docker & Docker Compose**
* 🟢 **Node.js (LTS) & npm**
* 📱 **Expo CLI** (`npm install -g expo-cli`)

### ⚙️ Backend Setup

1.  **Navigate to the backend directory**:
    ```bash
    cd backend
    ```

2.  **Configure Environment**:
    Create a `.env` file in the `backend` folder. The defaults are optimized for the Docker setup:
    ```env
    SERVER_PORT=3000
    DB_HOST=db
    DB_NAME=postgres
    DB_USER=postgres
    DB_PASSWORD=postgres
    JWT_SECRET=your_super_secret_key
    ```

3.  **Fire it up**: 🚀
    ```bash
    make start
    ```
    *The API will be live at `http://localhost:3000`*

### 📱 Mobile App Setup

1.  **Navigate to the mobile directory**:
    ```bash
    cd mobile
    ```

2.  **Install dependencies**: 📦
    ```bash
    npm install
    ```

3.  **Point to your API**: 🔗 
    Update `mobile/services/api.ts` with your computer's local IP address so your physical device can communicate with the server:
    ```typescript
    const url = "[http://192.168.1.](http://192.168.1.)XX:3000" // Replace XX with your IP
    ```

4.  **Launch Expo**: 🏎️
    ```bash
    npx expo start
    ```

---

## API Endpoints

All routes are prefixed with `/api`.

### 🔑 Authentication
| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/auth/login` | 🔓 Authenticate user |
| `POST` | `/auth/register` | ✨ Create new account |

### 📅 Events (Manager Role Required)
| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/event` | 📋 List all events |
| `POST` | `/event` | 🆕 Create new event |
| `GET` | `/event/:id` | 🔍 View event details |
| `PUT` | `/event/:id` | 📝 Update details |
| `DELETE` | `/event/:id` | 🗑️ Remove event |

### 🎟️ Tickets
| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/ticket` | 🎒 View my tickets |
| `POST` | `/ticket` | 💳 Buy a ticket |
| `GET` | `/ticket/:id` | 🖼️ View ticket & QR code |
| `POST` | `/ticket/validate`| ✅ Scan/Verify (Manager Only) |

---
