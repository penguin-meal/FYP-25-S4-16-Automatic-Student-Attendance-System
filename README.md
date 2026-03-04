# 🎓 Attendify – Automatic Attendance System with Facial Recognition

Attendify is a **Final Year Project (FYP)** that delivers a modern, secure, and scalable **automatic school attendance system** using **facial recognition**. The system is designed to eliminate manual attendance taking, reduce proxy attendance, and provide administrators with centralized control over academic and attendance data.

The project adopts a **mobile-first, API-driven architecture**, consisting of a **React Native mobile application** for students, a **Django REST backend** for administration and system logic, and a **web-based admin panel** for management.

---

## 🚀 Key Features

### 🧠 Facial Recognition–Based Attendance

* Automated attendance recording using facial recognition
* Eliminates manual roll calls and proxy attendance
* Real-time verification via backend API

### 🔐 Secure Authentication

* **Django Token Authentication** (NOT JWT)
* Header-based authentication:

  ```
  Authorization: Token <token_string>
  ```
* Role-based user handling (Admin / Lecturer / Student)

### 🏫 Academic & Attendance Management

* Student enrollment into modules
* Class session scheduling
* Attendance tracking per session
* Leave requests and appeal handling

### 📢 Communication System

* Targeted notifications (per user ID)
* News and event announcements

---

## 🧩 Repository Structure

```
root-repo/
├── mobile-app/            # React Native (Expo) mobile application
├── web-app/               # Web admin panel (Vite / React)
├── attendify-backend/     # Django + DRF backend API
└── README.md              # Project documentation
```

---

## 🏗️ System Architecture Overview

Attendify follows a **strict client–server architecture**:

* The **mobile application** and **web application** communicate exclusively with backend APIs
* The **backend** handles authentication, facial recognition logic, business rules, and database operations
* The **database is never accessed directly by the frontend**

```
[ React Native App ]      [ Web Admin Panel ]
          │                         │
          └──────── HTTP / JSON ────┘
                     │
                     ▼
            [ Django REST API ] ───► [ PostgreSQL ]
```

---

## 🛠️ Tech Stack

### Frontend (Mobile)

![React Native](https://img.shields.io/badge/React%20Native-20232A?style=for-the-badge\&logo=react\&logoColor=61DAFB)
![Expo](https://img.shields.io/badge/Expo-000020?style=for-the-badge\&logo=expo\&logoColor=white)
![Axios](https://img.shields.io/badge/Axios-5A29E4?style=for-the-badge)

### Frontend (Web Admin)

![React](https://img.shields.io/badge/React-20232A?style=for-the-badge\&logo=react\&logoColor=61DAFB)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge\&logo=vite\&logoColor=white)

### Backend

![Django](https://img.shields.io/badge/Django-092E20?style=for-the-badge\&logo=django\&logoColor=white)
![Django REST](https://img.shields.io/badge/DRF-ff1709?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge\&logo=python\&logoColor=white)

### Database

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge\&logo=postgresql\&logoColor=white)

---

## 🔗 API Documentation

### 🔑 Authentication

* **Login Endpoint**

  ```
  POST /api/auth/login/
  ```
* Uses **Token Authentication** (NOT JWT)

---

### 🧠 Admin Universal CRUD Base Path

```
/api/admin/crud/
```

### 📦 Available Resources

| Resource           | Endpoint                         |
| ------------------ | -------------------------------- |
| Users              | `/api/admin/crud/users/`         |
| Students           | `/api/admin/crud/students/`      |
| Lecturers          | `/api/admin/crud/lecturers/`     |
| Admins             | `/api/admin/crud/admins/`        |
| Semesters          | `/api/admin/crud/semesters/`     |
| Modules            | `/api/admin/crud/modules/`       |
| Class Sessions     | `/api/admin/crud/sessions/`      |
| Attendance Records | `/api/admin/crud/attendance/`    |
| Notifications      | `/api/admin/crud/notifications/` |
| News               | `/api/admin/crud/news/`          |
| Events             | `/api/admin/crud/events/`        |
| Leave Requests     | `/api/admin/crud/leaves/`        |
| Appeals            | `/api/admin/crud/appeals/`       |

All endpoints support:

* `GET` (List / Retrieve)
* `POST` (Create)
* `PATCH` (Partial Update)
* `DELETE` (Remove)

---

## 🧬 Database Design & Relationships

### 👤 User System

* Custom user model extending Django `AbstractUser`
* Role-based access:

  * Admin
  * Lecturer
  * Student

### 🎓 Academic Structure

* **Module** ↔ **Student** (Many-to-Many enrollment)
* **ClassSession** → linked to Module
* **AttendanceRecord** → tracks attendance status per session per student

### 📬 Communication Entities

* **Notification** → targeted to specific user IDs
* **News** → global announcements
* **Event** → scheduled institutional events

---

## 📦 Serialization Strategy

* Uses **nested serializers** for clean and informative API responses
* Example:

  * `StudentSerializer` returns a nested `user` object
* `AdminUserSerializer`:

  * Excludes sensitive fields (e.g. passwords)
  * Includes:

    * `role_type`
    * `phone_number`
    * `address`
    * `status`

---

## ⚙️ Installation & Setup

### Prerequisites

* Python 3.x
* Node.js & npm
* PostgreSQL
* Git

---

### Backend Setup (`attendify-backend`)

```bash
cd attendify-backend
python -m venv venv

# Activate virtual environment
# Windows
venv\Scripts\activate
# macOS / Linux
source venv/bin/activate

pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

Backend runs at:

```
http://127.0.0.1:8000/
```

---

### Mobile App Setup (`mobile-app`)

```bash
cd mobile-app
npm install
npm start
```

Run on:

* Android Emulator
* iOS Simulator
* Physical device via Expo

---

### Web App Setup (`web-app`)

```bash
cd web-app
npm install --registry=https://registry.npmmirror.com
npm run dev
```

---

**Attendify Project**
Final Year Project – Automatic Attendance System with Facial Recognition

### Documentations
https://drive.google.com/drive/folders/197gxfKtsvSv8vBMceO46nJFM20nGvVAj
