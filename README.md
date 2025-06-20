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

```plaintext
User 1 ────< Booking >──── 1 Property
  │                        │
  └────< Review >──────────┘

