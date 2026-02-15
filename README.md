# SmartShop – Spring Boot Microservices Application

## 📖 Overview

SmartShop is a backend application built using **Microservices Architecture** with Spring Boot.  
The project shows how independent services communicate through an **API Gateway** while maintaining secure access using **JWT Authentication**.

The system allows users to authenticate and manage inventory items through secured APIs.

---

## 🏛 System Architecture

            Client Application
                    |
            API Gateway (5000)
                    |
    ------------------------------------
    |                                  |
Auth Service (5001) Inventory Service (5002)


### Key Idea
- Client requests go only through the API Gateway.
- Gateway forwards requests to appropriate services.
- JWT tokens are verified before accessing protected resources.

---

## ⚙️ Tech Stack

- Java 17
- Spring Boot
- Spring Security
- Spring Cloud Gateway
- JWT (JSON Web Token)
- Spring Data JPA
- MySQL
- Swagger UI
- Maven
- Docker (optional)

---

## 🔑 Microservices

### ✅ Auth Service

**Port:** 5001

Responsible for authentication and authorization.

**Functions**
- Register new users
- Login users
- Generate JWT token
- Validate tokens

**Endpoints**
- `POST /auth/register`
- `POST /auth/login`
- `GET /auth/validate`

---

### ✅ Inventory Service

**Port:** 5002

Handles inventory management operations.

**Functions**
- Add inventory items
- View items
- Update items
- Delete items (Admin only)

**Endpoints**
- `POST /inventory`
- `GET /inventory`
- `GET /inventory/{id}`
- `PUT /inventory/{id}`
- `DELETE /inventory/{id}`

---

### ✅ API Gateway

**Port:** 5000

Central entry point of the system.

**Responsibilities**
- Routing requests
- JWT authentication check
- Access control
- Blocking unauthorized requests

**Routing Rules**
- `/auth/**` → Auth Service
- `/inventory/**` → Inventory Service

---

## 🔐 Security Features

- Password encryption using BCrypt.
- JWT-based authentication.
- Protected APIs require valid token.
- Delete operation restricted to ADMIN users.

---

## 🚀 Running the Application

### 1. Create Databases

Create the following MySQL databases:

smartshop_auth
smartshop_inventory


---

### 2. Start Services

Run each microservice:

```bash
mvn spring-boot:run
Recommended order:

Auth Service

Inventory Service

API Gateway

🧪 Testing the APIs
Register a user using:

POST /auth/register
Login and receive JWT token:

POST /auth/login
Add token to request headers:

Authorization: Bearer <token>
Access inventory APIs through gateway.

📚 API Documentation
Swagger UI is available at:

Auth Service:

http://localhost:5001/swagger-ui/index.html
Inventory Service:

http://localhost:5002/swagger-ui/index.html
🎓 What This Project Demonstrates
Microservices design using Spring Boot

API Gateway implementation

Secure communication using JWT

Role-based authorization

REST API development

