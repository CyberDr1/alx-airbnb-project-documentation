# Backend Requirements Specification – Airbnb Clone

This document outlines the technical and functional requirements for the backend system.

---

## 1. User Authentication

### API Endpoints
- `POST /api/v1/auth/register` – Register new users
- `POST /api/v1/auth/login` – Login and return a JWT token
- `GET /api/v1/auth/profile` – Fetch authenticated user's profile

### Input / Output
- Input: JSON body with `email`, `password`, and optional `name`
- Output: JWT token on success, error messages on failure

### Validation Rules
- Email must be unique and valid
- Password must be at least 8 characters
- All inputs must be non-empty

### Performance Criteria
- Token generation must complete within 200ms
- Secure password hashing with bcrypt

---

## 2. Property Management

### API Endpoints
- `POST /api/v1/properties` – Create a new property (host only)
- `GET /api/v1/properties/:id` – View property details
- `PUT /api/v1/properties/:id` – Edit property details
- `DELETE /api/v1/properties/:id` – Delete a listing

### Input / Output
- Input: Property data (title, description, location, price, amenities)
- Output: Property object or status message

### Validation Rules
- Title must be 10–100 characters
- Price must be positive
- Location is required

### Performance Criteria
- Listing creation/edit response within 300ms
- Searchable by filters (location, price, etc.)

---

## 3. Booking System

### API Endpoints
- `POST /api/v1/bookings` – Create a booking
- `GET /api/v1/bookings/:id` – View a booking
- `DELETE /api/v1/bookings/:id` – Cancel a booking

### Input / Output
- Input: `property_id`, `check_in`, `check_out`
- Output: Booking confirmation or error

### Validation Rules
- Check-in must be before check-out
- Prevent overlapping bookings
- Only authenticated users can book

### Performance Criteria
- Booking conflict check must be under 250ms
- Confirmations sent instantly via email

---

