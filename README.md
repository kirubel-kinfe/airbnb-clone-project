# 🏡 Airbnb Clone Backend

## 🚀 Objective
This project serves as the backend for an **Airbnb Clone**, offering a robust, scalable, and secure system that supports core functionalities like user interaction, property listings, bookings, and payment processing. It is designed to closely mirror Airbnb’s essential features, providing a seamless experience for both users and hosts.

---

## 🏆 Project Goals

- **User Management**: Secure registration, authentication, and profile management.
- **Property Management**: Create, update, retrieve, and delete property listings.
- **Booking System**: Book properties, manage check-in/check-out, and reservation history.
- **Payment Processing**: Secure transaction handling and recording.
- **Review System**: User-submitted reviews and ratings for properties.
- **Data Optimization**: Fast and efficient data operations via indexing and caching.

---

## 🛠️ Features Overview

### 1. API Documentation
- **OpenAPI Standard**: APIs follow the OpenAPI standard for clarity and integration ease.
- **Django REST Framework**: Supports robust CRUD operations.
- **GraphQL Support**: Flexible, performant queries for frontend needs.

### 2. User Authentication
- **Endpoints**: 
  - `GET /users/` - List users  
  - `POST /users/` - Register user  
  - `GET /users/{user_id}/` - Retrieve user profile  
  - `PUT /users/{user_id}/` - Update profile  
  - `DELETE /users/{user_id}/` - Delete user

### 3. Property Management
- **Endpoints**:
  - `GET /properties/` - List properties  
  - `POST /properties/` - Add new property  
  - `GET /properties/{property_id}/` - View property  
  - `PUT /properties/{property_id}/` - Edit property  
  - `DELETE /properties/{property_id}/` - Delete property

### 4. Booking System
- **Endpoints**:
  - `GET /bookings/` - View bookings  
  - `POST /bookings/` - Make a booking  
  - `GET /bookings/{booking_id}/` - View specific booking  
  - `PUT /bookings/{booking_id}/` - Modify booking  
  - `DELETE /bookings/{booking_id}/` - Cancel booking

### 5. Payment Processing
- **Endpoint**:
  - `POST /payments/` - Process payments related to bookings

### 6. Review System
- **Endpoints**:
  - `GET /reviews/` - View all reviews  
  - `POST /reviews/` - Add review  
  - `GET /reviews/{review_id}/` - View review  
  - `PUT /reviews/{review_id}/` - Edit review  
  - `DELETE /reviews/{review_id}/` - Remove review

### 7. Database Optimizations
- **Indexing**: Improves lookup speeds on frequently queried fields.
- **Caching**: Implements Redis for faster access and reduced DB load.

---

## ⚙️ Technology Stack

| Component        | Technology           |
|------------------|----------------------|
| Backend Framework| Django               |
| API Layer        | Django REST Framework / GraphQL |
| Database         | PostgreSQL           |
| Asynchronous Tasks | Celery             |
| Caching & Sessions | Redis              |
| Containerization | Docker               |
| DevOps & CI/CD   | GitHub Actions, Docker Compose, etc. |

---

## 👥 Team Roles

- **Backend Developer**: Implements APIs, business logic, and data models.
- **Database Administrator**: Optimizes queries, manages schema and indexes.
- **DevOps Engineer**: Handles deployments, scaling, and monitoring.
- **QA Engineer**: Writes tests, ensures stability and code quality.

---

## 📈 API Documentation Overview

### REST API
Fully documented using OpenAPI (Swagger) covering endpoints for:
- Users
- Properties
- Bookings
- Payments
- Reviews

### GraphQL API
- Allows clients to query only the data they need.
- Reduces over-fetching and under-fetching problems common in REST.

---

## 📌 Endpoint Summary

### 🔐 Users
```http
GET /users/
POST /users/
GET /users/{user_id}/
PUT /users/{user_id}/
DELETE /users/{user_id}/

🏠 Properties
GET /properties/
POST /properties/
GET /properties/{property_id}/
PUT /properties/{property_id}/
DELETE /properties/{property_id}/

📅 Bookings
GET /bookings/
POST /bookings/
GET /bookings/{booking_id}/
PUT /bookings/{booking_id}/
DELETE /bookings/{booking_id}/

💳 Payments
POST /payments/

⭐ Reviews
GET /reviews/
POST /reviews/
GET /reviews/{review_id}/
PUT /reviews/{review_id}/
DELETE /reviews/{review_id}/


🗃️ Database Design
This section describes the core entities in the Airbnb Clone backend and how they relate to each other.

1. User
Represents guests and hosts.

Key Fields:

id: Unique identifier

username: Display name or login name

email: Unique user email address

password: Encrypted password

role: Either "host" or "guest"

Relationships:

A user can own multiple properties (if they are a host).

A user can create multiple bookings (if they are a guest).

A user can write multiple reviews.

2. Property
Represents a listing that users can book.

Key Fields:

id: Unique identifier

title: Name or short description of the property

description: Detailed information about the property

location: Address or city

price_per_night: Cost per night

Relationships:

A property is owned by one user (host).

A property can have multiple bookings.

A property can have multiple reviews.

3. Booking
Represents a reservation made by a guest.

Key Fields:

id: Unique identifier

user_id: Reference to the guest

property_id: Reference to the booked property

check_in_date: Start of stay

check_out_date: End of stay

Relationships:

A booking is made by one user.

A booking is for one property.

A booking has one payment.

4. Payment
Represents the transaction for a booking.

Key Fields:

id: Unique identifier

booking_id: Reference to the booking

amount: Total payment amount

status: Payment status (e.g., "pending", "completed")

payment_date: Timestamp of the transaction

Relationships:

A payment is linked to one booking.

5. Review
Represents feedback left by guests.

Key Fields:

id: Unique identifier

user_id: Reference to the reviewer (guest)

property_id: Reference to the reviewed property

rating: Star rating (1–5)

comment: Textual review

Relationships:

A review is written by one user.

A review is for one property.

🔄 Entity Relationship Summary
One User ↔️ Many Properties

One User ↔️ Many Bookings

One User ↔️ Many Reviews

One Property ↔️ Many Bookings

One Property ↔️ Many Reviews

One Booking ↔️ One Payment




