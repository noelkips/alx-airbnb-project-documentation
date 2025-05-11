# 🧾 User Stories – Airbnb Clone Backend

This document captures the core user stories derived from the use case diagram, reflecting how different users interact with the system.

---

### 1. 🧑‍💼 As a guest, I want to register and log in so that I can search and book properties.

- Acceptance Criteria:
  - Guest can sign up with email and password.
  - Guest can log in securely using JWT-based authentication.

---

### 2. 🏠 As a host, I want to list new properties with descriptions and availability so that guests can book them.

- Acceptance Criteria:
  - Host can create, update, or delete property listings.
  - Host can specify price, location, and amenities.

---

### 3. 📅 As a guest, I want to book a property for specific dates so that I can reserve my stay.

- Acceptance Criteria:
  - Guest can view available dates.
  - System prevents double bookings.
  - Booking status is set to pending or confirmed.

---

### 4. 💳 As a guest, I want to make payments securely so that my booking is confirmed.

- Acceptance Criteria:
  - Payment is processed via Stripe or PayPal.
  - Guest receives confirmation upon success.
  - Host is notified of successful payment.

---

### 5. 📝 As a guest, I want to leave a review and rating after my stay so that I can share my experience.

- Acceptance Criteria:
  - Guest can rate from 1 to 5 and leave comments.
  - Review is linked to a past, completed booking.
  - Host can reply to reviews.

---

