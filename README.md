# 🎓 Learning Management System (LMS) Platform

A complete Learning Management System built using **Spring Boot (Java)** for the backend, **React.js** for the frontend, and **MySQL** for persistent storage. The platform supports **Admin**, **Mentor**, and **Customer** roles with role-based features like course management, purchases, and dashboards.

---

The Learning Management System or LMS platform Project using Spring Boot & React Js ensures a seamless experience for all involved. As an administrator, you can easily add the Course Categories in to the system, so that Mentors can add the Course from this Categories only. Mentor can register himself from the website. After Mentor Registration, Mentor can login to the system. After Mentors Login, Mentors can add the courses by adding the necessary details like Course Name, Description, Price, Course Chapters & Topics, Thumbnail, etc. Once Mentors has listed the Courses. All these courses will be visible in the Home page of the website. Now Customer can view all the course details and from there they can purchase the course. But, for purchasing the Course, Customer should logged into the system, Firstly Customer can register himself from the website and after login Customers can purchase the course and start the course. Now, Once courses are purchased by the Customers, Mentors can view all the purchased courses in his dashboard. In the Mentor Dashboard, Mentor will be able to see the complete details like how many courses added by him and how much sale is had generated.
And In the end, Admin will be able to see the complete details about the Course Categories, Course, Mentors, Customers, etc. in his dashboard. User Modules
The project basically has three user modules:

1. ADMINISTRATOR MODULE
2. CUSTOMER MODULE
3. MENTOR MODULE

Functional Modules 1) User Authentication Module:
User Authentication and Authorization with Spring Boot and React. The registration and Login system has been added so that only authenticated users (Admin, Mentor or Customer) can perform their functionalities.  
 2) Course Category Module:
Add Course Category, Update Category, Delete Category, View Categories.

     3) Course Module:

Add Course, Update Course, Delete Course, View Course, Search Courses.

     4) Mentor Module:

Register Mentor, Login Mentor, Delete Mentor.

     5) Course Purchase Module:

Purchase Course, View Purchased Courses.

````

## 🏗️ Step-by-Step Project Setup

### 1. Create Project Root Folder

```bash
mkdir lms-platform
cd lms-platform
````

---

### 2. Create Spring Boot Backend Folder

```bash
mkdir backend
cd backend
mkdir -p src/main/java/com/lms/config
mkdir -p src/main/java/com/lms/controller
mkdir -p src/main/java/com/lms/dto
mkdir -p src/main/java/com/lms/entity
mkdir -p src/main/java/com/lms/exception
mkdir -p src/main/java/com/lms/repository
mkdir -p src/main/java/com/lms/service
mkdir -p src/main/resources
touch src/main/resources/application.properties
touch pom.xml
```

---

### 3. Create React Frontend Folder

```bash
mkdir frontend
npx create-react-app frontend
cd frontend
mkdir -p src/components/auth
mkdir -p src/components/admin
mkdir -p src/components/mentor
mkdir -p src/components/customer
mkdir -p src/components/common
mkdir -p src/pages
mkdir -p src/assets
mkdir -p src/services
mkdir -p src/context
cd ../
```

---

### 4. Create Docker Compose File

```bash
touch docker-compose.yml
```

---

## 📁 Final Folder Structure Overview

```
lms-platform/
│
├── backend/                                               ← 🎯 Spring Boot Backend
│   ├── src/
│   │   └── main/
│   │       ├── java/com/lms/
│   │       │
│   │       ├── config/                                       ← 🔐 Security & JWT Config
│   │       │   └── SecurityConfig.java
│   │       │   └── JwtAuthenticationFilter.java
│   │       │   └── JwtUtils.java
│   │       │   └── CorsConfig.java
│   │       │
│   │       ├── controller/                                   ← 🎮 API Entry Points
│   │       │   └── AdminController.java                         ← Admin Functions
│   │       │   └── MentorController.java                        ← Mentor Registration/Login/Courses
│   │       │   └── CustomerController.java                      ← Customer Login/Purchase
│   │       │   └── AuthController.java                          ← Login/Register Common
│   │       │
│   │       ├── dto/                                          ← 📨 Request/Response DTOs
│   │       │   └── LoginRequest.java
│   │       │   └── RegisterRequest.java
│   │       │   └── CourseResponse.java
│   │       │   └── CourseResponse.java
│   │       │   └── PurchaseResponse.java
│   │       │
│   │       ├── entity/                                       ← 📦 JPA Entities
│   │       │   └── User.java                                    ← Roles: ADMIN / MENTOR / CUSTOMER
│   │       │   └── Role.java
│   │       │   └── Course.java
│   │       │   └── Category.java
│   │       │   └── Purchase.java
│   │       │
│   │       ├── mapping/                                      ← 🔄 Entity <-> DTO Mappers
│   │       │   └── CourseMapper.java                            ← Maps Course → CourseResponse
│   │       │   └── UserMapper.java                              ← Maps User → UserDTO
│   │       │   └── PurchaseMapper.java                          ← Maps Purchase → PurchaseResponse
│   │       │
│   │       ├── exception/                                    ← ❗ Custom Error Handling
│   │       │   └── GlobalExceptionHandler.java
│   │       │   └── ResourceNotFoundException.java
│   │       │
│   │       ├── repository/                                   ← 🗄️ Data Access Layer
│   │       │   └── UserRepository.java
│   │       │   └── CourseRepository.java
│   │       │   └── CategoryRepository.java
│   │       │   └── PurchaseRepository.java
│   │       │
│   │       ├── service/                                      ← ⚙️ Business Logic
│   │       │   └── AuthService.java
│   │       │   └── MentorService.java
│   │       │   └── CustomerService.java
│   │       │   └── AdminService.java
│   │       │
│   │       └── BackendApplication.java                       ← 🚀 Entry Point with @SpringBootApplication
│   │
│   └── resources/
│       └── application.properties                               ← ⚙️ DB, JWT, Mail Settings
│       └── schema.sql / data.sql                                ← 🧩 Optional: Initial Setup
│
├── pom.xml                                            ← 📦 Maven Dependencies
│
├── frontend/                                          ← ⚛️ React Frontend
│   ├── public/
│   │   └── index.html                                            ← 📄 HTML Template
│   │
│   ├── src/
│   │   ├── assets/                                               ← 🖼️ Thumbnails, logos
│   │
│   │   ├── components/
│   │   │   ├── auth/                                                 ← 🔐 Login/Register Forms
│   │   │   ├── admin/                                                ← 🛠 Admin Dashboard Views
│   │   │   ├── mentor/                                               ← 📚 Mentor Course Creation & Stats
│   │   │   ├── customer/                                             ← 🛒 Browse, Purchase Courses
│   │   │   └── common/                                               ← 🌐 Navbar, Footer, Loader
│   │
│   │   ├── context/                                              ← 📍 Auth / User Context API
│   │   ├── pages/
│   │   │   ├── HomePage.jsx
│   │   │   ├── LoginPage.jsx
│   │   │   ├── RegisterPage.jsx
│   │   │   └── NotFound.jsx
│   │
│   │   ├── services/                                             ← 📡 Axios API Handlers (e.g. authService.js)
│   │   ├── App.js                                                ← 🧭 Routing & Layout
│   │   └── index.js                                              ← 🚀 Entry point
│
│   package.json                                       ← ⚙️ NPM Dependencies
│
├── docker-compose.yml                                 ← 🐳 Docker Config for Backend, Frontend, MySQL
├── .gitignore
└── README.md

```

TO CONNECT SPRING BOOT APPLICATION TO DATABASE

🔧 Step 1: Update application.properties

Go to:
lms-backend/src/main/resources/application.properties

Add the following configuration for MySQL (adjust to your DB credentials):

# DataSource Config

spring.datasource.url=jdbc:mysql://localhost:3306/lms_db
spring.datasource.username=root
spring.datasource.password=your_password_here
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# JPA & Hibernate

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.database-platform=org.hibernate.dialect.MySQL8Dialect

# Server Port (optional)

server.port=8080

✅ Make sure:
You have a MySQL DB running on port 3306
You have created a database called lms_db
The user/password match your MySQL config

🔧 Step 2: Add MySQL Driver in pom.xml
In your lms-backend/pom.xml, make sure this dependency exists:
<dependency>
<groupId>mysql</groupId>
<artifactId>mysql-connector-j</artifactId>
<scope>runtime</scope>
</dependency>

🔧 Step 3: Create the Database (If Not Exists)
Login to MySQL and create the DB:
CREATE DATABASE lms_db;

🔄 Step 4: Restart Your Application
Now re-run your Spring Boot app:
./mvnw spring-boot:run

---

## 🧩 Backend Structure Explained (`lms-backend/`)

| Folder                       | Description                                                   |
| ---------------------------- | ------------------------------------------------------------- |
| `config/`                    | Spring Security, JWT, and CORS configuration files            |
| `controller/`                | REST controllers that handle API endpoints for each user role |
| `dto/`                       | Data Transfer Objects for request and response payloads       |
| `entity/`                    | JPA entity classes mapped to MySQL tables                     |
| `exception/`                 | Custom exceptions and global error handling                   |
| `mapping/`                   | Helper classes to convert between Entities and DTOs           |
| `repository/`                | Spring Data JPA interfaces for DB operations                  |
| `service/`                   | Core business logic and service layer                         |
| `application.properties`     | Config for DB, JWT, mail, etc.                                |
| `LmsBackendApplication.java` | Entry point of the Spring Boot app                            |

---

## ⚛️ Frontend Structure Explained (`lms-frontend/`)

| Folder                 | Description                                 |
| ---------------------- | ------------------------------------------- |
| `components/auth/`     | Login and registration forms for all users  |
| `components/admin/`    | Admin dashboard views and controls          |
| `components/mentor/`   | Mentor dashboard and course creation forms  |
| `components/customer/` | Course browsing, purchase, and my courses   |
| `components/common/`   | Navbar, footer, loading spinner, etc.       |
| `assets/`              | Static files like thumbnails or logos       |
| `context/`             | React Context API for auth/user sessions    |
| `pages/`               | Routes like Home, Login, Register, NotFound |
| `services/`            | Axios-based API service handlers            |
| `App.js`               | Route and layout configuration              |
| `index.js`             | React entry point file                      |

---

lms-platform/
├── lms-backend/
│ ├── src/main/java/com/lms/...
│ ├── src/main/resources/
│ └── pom.xml
├── lms-frontend/
│ ├── src/components/...
│ └── package.json
├── docker-compose.yml
├── README.md
└── .gitignore

---

---

## 🚀 Features

### 👨‍🏫 Mentor

- Self-registration & login
- Add/update/delete courses
- View sales and courses on dashboard

### 👩‍💻 Customer

- Register/login
- Browse and purchase courses
- View purchased courses

### 👩‍💼 Admin

- Manage course categories
- View list of mentors, customers, and courses
- System-wide analytics dashboard

---

## 🔐 Authentication & Authorization

- Role-based access control using **JWT tokens**
- Secure API access with **Spring Security**
- React context to manage frontend session state

---

## 🧱 Tech Stack

| Layer      | Tech Used                      |
| ---------- | ------------------------------ |
| Backend    | Spring Boot, Maven, JWT        |
| Frontend   | React.js, Bootstrap            |
| Database   | MySQL                          |
| Dev Tools  | IntelliJ IDEA, MySQL Workbench |
| Deployment | Docker, Docker Compose         |

---

## 🐳 Docker Setup

```bash
docker-compose up --build
```

This will:

- Run Spring Boot backend on port `8080`
- Run React frontend on port `3000`
- Run MySQL server on port `3306`

---

## 📌 How to Run Locally

1. **Clone the repository:**

   ```bash
   git clone https://github.com/your-username/lms-platform.git
   cd lms-platform
   ```

2. **Start backend:**

   ```bash
   cd backend
   ./mvnw spring-boot:run
   ```

3. **Start frontend:**

   ```bash
   cd frontend
   npm install
   npm start
   ```

4. **Visit**: [http://localhost:3000](http://localhost:3000)

---

Here’s a step-by-step guide to pushing your LMS project to GitHub using Git:

✅ 1. Initialize Git in Your Project Root
Go to your lms-platform/ root folder and run:

cd lms-platform
git init

✅ 2. Create a .gitignore File

Make sure you ignore unnecessary files (like build, log, IDE settings). Create .gitignore:
touch .gitignore
Then add typical Java, Node, and IDE ignores:

# Java

/target/
\*.log

# Node

node_modules/
build/
.env

# IDE

.idea/
.vscode/

# OS

.DS_Store

✅ 3. Add All Files to Git
git add .
. means “add everything”

✅ 4. Commit Your Changes
git commit -m "Initial commit: LMS backend and frontend setup"

✅ 5. Create a GitHub Repository
Go to https://github.com, click New, and create a repo called lms-platform (or any name).
Do not check "Initialize with README" (you already have one).

✅ 6. Connect Local Repo to GitHub Remote
Replace <your-username> with your GitHub username.
git remote add origin https://github.com/<your-username>/lms-platform.git
To verify:
git remote -v

✅ 7. Push Your Code to GitHub
First time push:
git push -u origin main
If main branch doesn't exist locally, create it first:
git checkout -b main
git push -u origin main

✅ 8. Future Changes
When you make more changes:
git add .
git commit -m "Describe your change here"
git push

---

## 📚 License

This project is licensed under the ELSHA.

---

## 👨‍💻 Author

**Elsha Negash**  
Passionate about designing powerful, educational software solutions.
