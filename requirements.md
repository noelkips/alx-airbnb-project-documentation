
# 📄 Backend Feature Requirements – Airbnb Clone

This document outlines the technical and functional specifications for three core backend features: **User Authentication**, **Property Management**, and **Booking System**. Each section includes API details, input/output formats, validation rules, and performance criteria.

---

## 1️⃣ User Authentication

### 🔐 Feature Overview
Handles user registration, login, and secure session management using JWT.

### ✅ Functional Requirements
- Users must be able to register using email, password, and role (guest/host).
- Login validates credentials and returns a JWT.
- Authenticated users can access protected routes.
- OAuth via Google/Facebook (optional enhancement).

### 🔗 API Endpoints
#### POST `/api/auth/register`
- **Input:**
  ```json
  {
    "first_name": "John",
    "last_name": "Doe",
    "email": "john@example.com",
    "password": "securepassword",
    "role": "guest"
  }
  ```
- **Output:**
  ```json
  {
    "message": "User registered successfully.",
    "token": "<jwt_token>"
  }
  ```

#### POST `/api/auth/login`
- **Input:**
  ```json
  {
    "email": "john@example.com",
    "password": "securepassword"
  }
  ```
- **Output:**
  ```json
  {
    "message": "Login successful.",
    "token": "<jwt_token>"
  }
  ```

### 🧪 Validation Rules
- Email: Must be unique and valid format.
- Password: Minimum 8 characters.
- Role: Must be either `guest` or `host`.

### ⚙️ Performance Criteria
- Token generation and validation in under 100ms.
- Rate limit: 10 login attempts/hour/IP.

---

## 2️⃣ Property Management

### 🏡 Feature Overview
Allows hosts to create, update, and delete property listings.

### ✅ Functional Requirements
- Hosts can list properties with details.
- Listings include name, location, description, price, and availability.
- Only hosts can manage their own listings.

### 🔗 API Endpoints
#### POST `/api/properties`
- **Input:**
  ```json
  {
    "name": "Cozy Apartment",
    "description": "Near downtown, free WiFi.",
    "location": "New York",
    "pricepernight": 120.50
  }
  ```
- **Output:**
  ```json
  {
    "message": "Property created.",
    "property_id": "uuid"
  }
  ```

#### PUT `/api/properties/:id`
- Updates listing details.

#### DELETE `/api/properties/:id`
- Removes listing.

### 🧪 Validation Rules
- Price must be a positive number.
- Location and description must not be empty.

### ⚙️ Performance Criteria
- Property retrieval in <200ms.
- Limit 10 property creations/minute/host.

---

## 3️⃣ Booking System

### 📅 Feature Overview
Handles booking creation, validation, and status tracking.

### ✅ Functional Requirements
- Guests can book available properties.
- Bookings track dates, status, and total price.
- Prevent double-booking with date conflict checks.

### 🔗 API Endpoints
#### POST `/api/bookings`
- **Input:**
  ```json
  {
    "property_id": "uuid",
    "start_date": "2025-06-01",
    "end_date": "2025-06-05"
  }
  ```
- **Output:**
  ```json
  {
    "message": "Booking created.",
    "booking_id": "uuid",
    "status": "pending"
  }
  ```

#### GET `/api/bookings/user/:user_id`
- Returns a list of all bookings for a user.

### 🧪 Validation Rules
- Booking must not overlap with existing bookings.
- Dates must be in the future and valid.

### ⚙️ Performance Criteria
- Availability check within 150ms.
- Confirmed bookings stored instantly with unique booking_id.

---

🧾 **Note:** All endpoints require JWT authentication unless specified as public.
