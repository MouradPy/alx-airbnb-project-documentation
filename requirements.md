# Backend Requirement Specifications

## 1. User Authentication

### Description
Manages user registration, login, and authentication for Guests, Hosts, and Admins.

### Functional Requirements
- Users can register using name, email, and password.
- Users can log in using email and password.
- System generates JWT tokens upon successful login.
- Passwords are encrypted using a secure hashing algorithm (e.g., bcrypt).
- Invalid credentials return appropriate error responses.

### API Endpoints
| Method | Endpoint              | Description          | Input                              | Output                                 |
|--------|-----------------------|----------------------|-------------------------------------|----------------------------------------|
| POST   | `/api/auth/register`  | Register a new user  | `{name, email, password}`           | `{message, userId}`                    |
| POST   | `/api/auth/login`     | Authenticate user    | `{email, password}`                 | `{token, userId, role}`                |

### Validation Rules
- Email must be unique and valid format.
- Password must have at least 8 characters.
- All fields required.

### Performance Criteria
- Registration or login should complete in < 2 seconds.
- Token validity: 24 hours.

---

## 2. Property Management

### Description
Allows Hosts to create, update, and manage property listings. Guests can view available properties.

### Functional Requirements
- Hosts can create, update, and delete their property listings.
- Guests can search and filter properties by location, price, and amenities.
- Admin can view or remove any listing that violates policy.

### API Endpoints
| Method | Endpoint                | Description              | Input                                | Output                           |
|--------|--------------------------|--------------------------|---------------------------------------|----------------------------------|
| POST   | `/api/properties`       | Create a new property    | `{title, description, price, images}` | `{propertyId, message}`          |
| GET    | `/api/properties`       | Get all properties       | `query params (filters)`              | `[ {propertyId, title, price} ]` |
| PUT    | `/api/properties/:id`   | Update property details  | `{title, price, description}`         | `{message}`                      |
| DELETE | `/api/properties/:id`   | Delete property          | `propertyId`                         | `{message}`                      |

### Validation Rules
- Title and description are required.
- Price must be a positive number.
- Each property must have at least one image.

### Performance Criteria
- Property fetch requests should respond in under 3 seconds.
- Database should handle up to 10,000 listings efficiently.

---

## 3. Booking System

### Description
Handles reservations made by Guests and ensures proper availability and payment linkage.

### Functional Requirements
- Guests can book available properties.
- System checks date availability before confirming.
- Hosts can view bookings for their properties.
- Admin can monitor all bookings.

### API Endpoints
| Method | Endpoint                 | Description            | Input                                       | Output                                 |
|--------|---------------------------|------------------------|----------------------------------------------|----------------------------------------|
| POST   | `/api/bookings`           | Create a booking       | `{userId, propertyId, checkIn, checkOut}`    | `{bookingId, message}`                 |
| GET    | `/api/bookings/:userId`   | Get user bookings      | `userId`                                    | `[ {bookingId, propertyId, dates} ]`  |
| DELETE | `/api/bookings/:id`       | Cancel a booking       | `bookingId`                                 | `{message}`                            |

### Validation Rules
- Check-in date must be before check-out date.
- Property must be available for the selected dates.
- User must be authenticated.

### Performance Criteria
- Booking confirmation within 3 seconds.
- Prevent double-booking using atomic database transactions.

---

## Summary

| Feature              | Key Entities        | Main Database Tables     |
|----------------------|--------------------|---------------------------|
| User Authentication  | Users              | `users`                   |
| Property Management  | Properties, Hosts  | `properties`, `hosts`     |
| Booking System       | Bookings, Payments | `bookings`, `payments`    |
