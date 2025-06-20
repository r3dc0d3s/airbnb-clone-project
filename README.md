# airbnb-clone-project
exciting new journey into a complex project through baby steps in order to remaster the ropes of modern full stack developpment with an accent on the back-end side for the time being


Team Roles :
Backend Developer: Responsible for implementing API endpoints, database schemas, and business logic.
Database Administrator: Manages database design, indexing, and optimizations.
DevOps Engineer: Handles deployment, monitoring, and scaling of the backend services.
QA Engineer: Ensures the backend functionalities are thoroughly tested and meet quality standards.

(i am not sure how this wil be graded, is it through regex or other means ? we will see if this test passes) 

even if the test is passed successfully i want to allocate 30 minutes reading about the topics and exploring the workflows of each team member

(the test passed successfully despite the dummy response which is fine i suppose but my goal is learning hence i will proceed as promised

Technology Stack :
> learn more about GraphQL and RestAPIs
> Learned quite a bit about the difference between REST (something something State Transfer) and GraphQL (query Language) , i will b mostly parrotting these points rather than express a deep understanding at this point but ..
- Graph QL : baiscally is granular but also costly in compute as the server is the one burdened , protocol agnostic though i have to admit i have ZERO idea what that means, some tooling like GraphQL mesh allows you to combine it with gRPC and SOAP etc ... api whatever ... frankly again i have no freaking idea what they mean, their purpose etc .. but hey they have crossed my path enough times (mostly in yt where i exist rather than in real projects 😭)

# Tech Stack Overview

This project uses a set of modern technologies to build a scalable and maintainable web application. Here's a breakdown of each component:

## **Django**
- **Purpose**: A high-level Python web framework that promotes rapid development and clean, pragmatic design.
- **Why Django?**: 
  - **Batteries-included**: Comes with built-in tools like authentication, admin interface, form handling, and more.
  - **Security**: Offers protection against common attacks like SQL injection, cross-site scripting (XSS), cross-site request forgery (CSRF), and clickjacking.
  - **Scalability**: Handles high-traffic applications with ease and is designed for easy scaling.
  - **Community & Documentation**: Django has a large, active community and extensive documentation for developers.

## **Django REST Framework (DRF)**
- **Purpose**: A powerful toolkit for building Web APIs in Django.
- **Why DRF?**
  - **Serialization**: Easily convert complex data types like querysets and model instances into JSON and vice versa.
  - **Authentication**: Supports multiple authentication methods such as token authentication and OAuth.
  - **Permissions**: Control who can access what via permission classes.
  - **Viewsets & Routers**: Simplify URL routing and view logic for handling CRUD operations.

## **PostgreSQL**
- **Purpose**: A powerful, open-source relational database system.
- **Why PostgreSQL?**
  - **ACID Compliant**: Ensures reliable and consistent transactions.
  - **Advanced Features**: Supports JSON data types, full-text search, and more.
  - **Extensibility**: You can create custom types, functions, and operators.
  - **Scalability**: Suitable for both small and large-scale applications.

## **GraphQL**
- **Purpose**: A query language for APIs that allows clients to request exactly the data they need.
- **Why GraphQL?**
  - **Flexible Queries**: Clients can request only the data they need, reducing over-fetching.
  - **Strongly Typed**: The schema defines the structure of the API, ensuring that data is returned in a predictable format.
  - **Efficient**: Reduces the number of requests by allowing clients to fetch multiple resources in a single query.

## **Celery**
- **Purpose**: An asynchronous task queue/job queue based on distributed message passing.
- **Why Celery?**
  - **Asynchronous Processing**: Offload long-running tasks such as sending emails, processing payments, or image manipulation to background workers.
  - **Distributed**: Can run multiple workers on different machines, improving scalability.
  - **Task Retry**: Allows for automatic retries of failed tasks.

## **Redis**
- **Purpose**: An in-memory data structure store used as a database, cache, and message broker.
- **Why Redis?**
  - **Caching**: Speeds up application performance by storing frequently accessed data in memory.
  - **Session Management**: Used for managing user sessions in web applications.
  - **Message Queuing**: Works with Celery to queue tasks and handle background jobs.

## **Docker**
- **Purpose**: A platform for developing, shipping, and running applications inside containers.
- **Why Docker?**
  - **Environment Consistency**: Ensures that the application runs the same way on every environment (development, staging, production).
  - **Isolation**: Containers isolate application dependencies, making it easier to avoid conflicts between different versions of libraries and services.
  - **Scalability**: Easily scale applications by running multiple containers and orchestrating them with Docker Compose or Kubernetes.

## **CI/CD Pipelines**
- **Purpose**: Continuous Integration and Continuous Deployment automate the process of testing and deploying code changes.
- **Why CI/CD?**
  - **Automated Testing**: Ensure that code changes don’t break existing functionality by running automated tests on every push.
  - **Faster Releases**: Deploy code changes faster with automated pipelines.
  - **Quality Control**: Automatically enforce quality standards such as linting, code coverage, and style checks before deploying to production.



## 🌍 Database Design

### 🧑 `User`
Represents a guest or a host in the platform.

| Field                | Type      | Description                                       |
|---------------------|-----------|---------------------------------------------------|
| `id`                | UUID      | Primary key                                       |
| `name`              | String    | Full name of the user                             |
| `check_in`          | DateTime  | Latest check-in date (if applicable)              |
| `check_out`         | DateTime  | Latest check-out date (if applicable)             |
| `reputation_score`  | Float     | Average rating received as a host                 |
| `rating_behavior`   | Float     | Average rating the user gives to properties       |

**Relationships:**
- 🔁 One-to-Many with `Booking` (as guest)
- 🔁 One-to-Many with `Review` (as reviewer)

---

### 🏡 `Property`
Represents a property listed on the platform.

| Field         | Type      | Description                           |
|--------------|-----------|---------------------------------------|
| `id`         | UUID      | Primary key                           |
| `name`       | String    | Name of the property                  |
| `description`| Text      | Full description                      |
| `n_rooms`    | Integer   | Number of rooms                       |
| `capacity`   | Integer   | Max number of guests                  |
| `amenities`  | JSON/Array| List of amenities                     |
| `price`      | Decimal   | Price per night                       |
| `availability`| JSON     | Available date ranges                 |
| `rating`     | Float     | Average rating based on reviews       |

**Relationships:**
- 🔁 One-to-Many with `Booking`
- 🔁 One-to-Many with `Review`

---

### 📅 `Booking`
Links users to properties over a date range.

| Field            | Type      | Description                                 |
|------------------|-----------|---------------------------------------------|
| `id`             | UUID      | Primary key                                 |
| `user_id`        | UUID      | FK to `User`                                |
| `property_id`    | UUID      | FK to `Property`                            |
| `check_in`       | Date      | Start date of booking                       |
| `check_out`      | Date      | End date of booking                         |
| `reviewed`       | Boolean   | Whether a review was submitted              |
| `review_id`      | UUID?     | FK to `Review` if applicable                |
| `status`         | Enum      | {future, present, past}                     |
| `payment_option` | Enum      | {card, paypal, crypto, ...}                 |
| `payment_ts`     | Timestamp | When payment was processed                  |

**Relationships:**
- 🔁 Many-to-One with `User`
- 🔁 Many-to-One with `Property`
- 🔁 Optional One-to-One with `Review`

---

### ✍️ `Review`
Feedback left by users after a stay.

| Field       | Type      | Description                       |
|-------------|-----------|-----------------------------------|
| `id`        | UUID      | Primary key                       |
| `user_id`   | UUID      | FK to `User` (reviewer)           |
| `property_id`| UUID     | FK to `Property`                  |
| `rating`    | Integer   | Rating from 1 to 5                |
| `content`   | Text      | Written feedback                  |
| `timestamp` | DateTime  | When the review was submitted     |

**Relationships:**
- 🔁 Many-to-One with `User`
- 🔁 Many-to-One with `Property`
- 🔁 Optional link to `Booking`

---

## 🔗 ERD Relationship Summary


User 1 ────< Booking >──── 1 Property
  │                        │
  └────< Review >──────────┘


## 🧩 Database Schema Overview

This project models a full-stack booking platform, focusing on both users and property management. The database schema is designed to track interactions between hosts and guests, including property listings, bookings, reviews, and payments. Each table is relationally connected to ensure efficient data management and scalability for future features.

---

## 🔍 Feature Breakdown

### 1. 🧑‍💼 User Management
- **Description:** The User Management system handles the registration, authentication, and management of user profiles. Users can register via email, log in, update their profile information, and manage their preferences. This ensures a personalized experience and allows users to track bookings, make reviews, and manage account details.
- **Endpoints:** `/users/`, `/users/{user_id}/`

### 2. 🏠 Property Management
- **Description:** The Property Management system allows property owners (hosts) to list, update, and remove their properties. The system captures essential property details such as name, description, number of rooms, capacity, amenities, price, and availability. This feature is essential for creating a marketplace of properties for guests to browse and book.
- **Endpoints:** `/properties/`, `/properties/{property_id}/`

### 3. 📅 Booking System
- **Description:** The Booking system allows guests to reserve properties for a specific period, capturing check-in and check-out details. Bookings are tracked with a status (future, present, past) and allow hosts to manage availability. The system also supports reviewing a booking once completed.
- **Endpoints:** `/bookings/`, `/bookings/{booking_id}/`

### 4. 💳 Payment Processing
- **Description:** This feature handles the processing of payments made for bookings. It supports multiple payment methods and records transaction timestamps to ensure transparency and track the status of payments for each booking.
- **Endpoints:** `/payments/`

### 5. ⭐ Review System
- **Description:** The Review system enables guests to leave ratings and written feedback for properties they've stayed in. These reviews help future guests make informed decisions and impact the property's average rating. Reviews are also a valuable resource for property owners to improve their services.
- **Endpoints:** `/reviews/`, `/reviews/{review_id}/`

### 6. 📖 API Documentation
- **Description:** The project uses OpenAPI standards to document the backend APIs, providing clear and structured documentation for developers. The APIs are built using Django REST Framework for the RESTful endpoints and GraphQL for more flexible querying. This ensures easy integration and allows for detailed error handling and user-friendly API usage.
- **Standards:** OpenAPI, Django REST Framework, GraphQL

### 7. 🚀 Performance Optimizations
- **Description:** To ensure high performance, the database uses indexing on frequently accessed fields (such as `user_id` and `property_id`) to speed up query responses. Additionally, caching mechanisms are implemented for high-traffic endpoints to reduce database load, improving response times and scalability.
- **Optimizations:** Indexing, Caching



## API Security

Ensuring the security of the API is critical for maintaining user trust, protecting sensitive data, and ensuring the integrity of the booking platform. The following key security measures will be implemented:

### 🔐 Authentication
**Description**: Only authenticated users can access protected endpoints using secure token-based authentication (JWT or OAuth2).
**Why it matters**: Prevents unauthorized access to user data and functionality, especially in operations involving personal info, bookings, or payments.

### 🛡️ Authorization
**Description**: Role-based access control (RBAC) ensures that users (e.g., guests, hosts, admins) can only perform actions they are permitted to.
**Why it matters**: Protects data boundaries (e.g., a user shouldn’t access another user’s booking history or modify another’s property listing).

### 🚦 Rate Limiting & Throttling
**Description**: Limits the number of API requests per user/IP over time.
**Why it matters**: Prevents abuse, brute-force login attempts, and denial-of-service (DoS) attacks that could cripple the platform.

### 🧊 Input Validation & Sanitization
**Description**: All user inputs are validated and sanitized to prevent injection attacks (e.g., SQL, XSS).
**Why it matters**: Protects backend systems and data integrity from malicious input.

### 🔒 Secure Payment Handling
**Description**: Payments are processed through a secure, PCI-compliant provider. Sensitive data is never stored in raw form.
**Why it matters**: Protects financial information and builds user trust.

### 🔁 HTTPS Enforcement
**Description**: All traffic is encrypted using HTTPS, with redirection from HTTP.
**Why it matters**: Prevents man-in-the-middle attacks and ensures data is transmitted securely between client and server.

### 🧠 Logging & Monitoring
**Description**: All security-critical events are logged and monitored in real time.
**Why it matters**: Enables fast detection and response to suspicious activity or breaches.

By combining these measures, the platform ensures a robust and secure environment for all users, from registration to booking and beyond.


