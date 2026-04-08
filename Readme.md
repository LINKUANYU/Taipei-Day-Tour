# Taipei Day Tour

A travel e-commerce platform built on a decoupled architecture, featuring a comprehensive shopping and checkout flow.

[Live Demo](https://taipeidaytour.linkuankuan.com/) | [API Documentation](https://taipeidaytour.linkuankuan.com/docs)

## 🌟 Features

* **Database Design:** Designed a relational **MySQL** database schema for shopping cart and order management, and implemented a **Connection Pool** to efficiently manage database connections.
* **API Architecture Design:** Developed a RESTful backend API using **FastAPI** to handle core business logic within a decoupled (frontend/backend) architecture.
* **Payment Gateway Integration:** Integrated **TapPay API** to implement online credit card payments, ensuring secure transaction authorization and deduction processes.
* **Security & Authorization:** Built an independent user authentication system using **JWT (JSON Web Tokens)** for stateless login and API access control, alongside secure password hashing.

## 🛠️ Tech Stack

* **Backend:** Python, FastAPI
* **Database:** MySQL, Connection Pool
* **Frontend:** JavaScript, HTML, CSS
* **Infrastructure:** Docker, AWS (EC2 / RDS), Nginx
* **Third-Party API:** TapPay API

## ERD

```mermaid

erDiagram
    MEMBERS ||--o| BOOKING : "has 1 cart"
    MEMBERS ||--o{ ORDERS : "creates"
    SPOT ||--o{ BOOKING : "is added to"
    SPOT ||--o{ ORDERS : "is included in"
    ORDERS ||--o{ PAYMENT : "paid via"

    MEMBERS {
        INT id PK
        VARCHAR email UK
        VARCHAR name
    }
    
    SPOT {
        INT id PK
        VARCHAR name
        VARCHAR category
    }
    
    BOOKING {
        INT id PK
        INT member_id FK "UK"
        INT spot_id FK
        DATE booking_date
    }
    
    ORDERS {
        INT id PK
        VARCHAR order_no UK
        INT member_id FK
        INT spot_id FK
        ENUM status
    }
    
    PAYMENT {
        INT id PK
        INT order_id FK
        VARCHAR provider
        ENUM status
    }

```

## 🔌 API Endpoints

| Method | Endpoint | Description  | Authentication |
| ------ | -------- | ---------------------- | --------------------- |
| POST   | `/api/user` | Register a new user  | None |
| GET    | `/api/attractions` | Get attraction list with pagination | None |
| POST   | `/api/booking` | Add an attraction to the shopping cart | JWT Required |
| POST   | `/api/orders` | Create a new order and initialize payment | JWT Required |

## Screenshots
* **Homepage**
<img width="1139" height="986" alt="Screenshot 2026-04-08 at 8 19 24 PM" src="https://github.com/user-attachments/assets/97ad6746-ec41-49a4-9aa8-d3a363b2346c" />
<hr>

* **History Order page**
<img width="1098" height="654" alt="Screenshot 2026-04-08 at 8 18 54 PM" src="https://github.com/user-attachments/assets/d07b493f-ce70-4074-b57b-c628a8eb0c82" />
<hr>

* **Booking page**
<img width="1896" height="989" alt="Screenshot 2026-04-08 at 8 17 35 PM" src="https://github.com/user-attachments/assets/214e3195-ea36-4dd7-8cb8-25e40560e090" />
<hr>

 test account

| Account | Password | 
| ------ | ------ |
| test@mail.com | !Q12345678 |
