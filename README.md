# airbnb-clone-project

## 👥 Team Roles

- **Backend Developer**: Responsible for implementing API endpoints, database schemas, and business logic.
- **Database Administrator**: Manages database design, indexing, and optimizations.
- **DevOps Engineer**: Handles deployment, monitoring, and scaling of the backend services.
- **QA Engineer**: Ensures the backend functionalities are thoroughly tested and meet quality standards.

## ⚙️ Technology Stack
- **Django**
  A high-level Python web framework used for building the RESTful API.
  
- **Django REST Framework**
  Provides tools for creating and managing RESTful APIs.

- **PostgreSQL**
  A powerful relational database used for data storage.

- **GraphQL**
  Allows for flexible and efficient querying of data.

- **Celery**
  For handling asynchronous tasks such as sending notifications or processing payments.

- **Redis**
  Used for caching and session management

- **Docker**
  Containerization tool for consitent development and deployment environments

- **CI/CD Pipelines**
  Automated pipelines for testing and deploying code changes.

## 📊 Database Design
This section outlines the core entities in the database and how they relate to each other

### 🧑 Users
  Represents Users of the platform, including property owners and guests.
  
  **Key Fields:**
  - `id` (Primary Key): unique Identifier for the user
  - `name`: Full name of the user
  - `email`: User's email address (unique)
  - `password_hash`: Encrypted password
  - `role`: Defines if the user is a host or guest
    
  **Relationships**
  - A user can own multiple properties
  - A user can make multiple bookings
  - A user can write multiple reviews
  - A user can make multiple payments
    
---

### 🏡 Properties
Represents properties listed by users for booking.

**Key Fields:**
- `id` (Primary Key): Unique identifier for the property
- `owner_id` (Foreign Key -> Users): The user who owns the property
- `title`: Name or title of the property
- `description`: Detailed description of the property
- `price_per_night`: Cost to stay per night

**Relationships**:
- A property belongs to a user (owner)
- A property can have multiple bookings
- A property can have multiple reviews

---

### 📅 Bookings
Represents reservations made by users for properties

**Key Fields:**
- `id` (Primary Key): Unique identifier for the booking
- `user_id`: (Foreign Key -> Users): The guest who made the booking
- `property_id` (Foreign Key -> Properties): The property being booked
- `start_date`: Booking start date
- `end_date`: Booking end date

**Relationships**:
- A booking belongs to one user and one property
- A booking may have one associated payment

---

### ✍️ Reviews
Captures feedback left by users on properties.

**Key Fields:**
- `id`: Unique identifier for the review
- `user_id` (Forign Key -> Users): The guest who left the review
- `property_id` (Foreign Key -> Properties): The property being reviewed
- `rating`: Numerical rating (e.g., 1-5)
- `comment`: Textual feedback

**Relationships:**
- A review belongs to a user and a property

---

### 💳 Payments
Represents payment transactions for bookings.
**Key Fields:**
- `id`: Unique identifier for the payment
- `user_id` (Foreign Key -> Users): The user who made the payment
- `booking_id` (Foreign Key -> Bookings): The related booking
- `amount`: Amount paid
- `payment_date`: The date the payment was processed

**Relationships:**
- A payment belongs to a user and a booking
- 

## 🧩 Feature Breakdown

  This section outlines the core features of the project and explains how each contributes to the overall functionality.
  ### 👤 User Management
  Handles user registration, login, and profile management. This feature allows both guests and hosts to create accounts, securely log in, and manage their personal information and activity.
  
  ### 🏡 Property Management
  Enables hosts to list, update, and delete their properties. Property management includes uploading descriptions, pricing, photos, and availability to attract potential guests.
  
  ### 📅 Booking System
  Allows guests to view available properties and make bookings for specific dates.This features ensures date validation, prevents double booking, and maintains booking history for both users and hosts.
  
  ### 💳 Payment Processing
  Handles secure payments for bookings. This includes collecting payment information, processing transactions, and linking payments to specific bookings for financial tracking.
  
  ### ✍️ Review System
  Lets guests have reviews and ratings for properties they have stayed in. This helps build trust in the platform by providing feedback and helping future guests make informed decisions.

## 🔐 API Security

  This section outlines the core security measures implemented to protect the application, its users, and their data.
  
  ### 🔑 Authentication
  All API endpoints that require user interaction are secured using token-based authentication (e.g., JWT). This ensures that only verified users can access protected resources like booking a property or managing listings.
  
  **Why it matters:**
  Authentication protects user accounts and personal data by ensuring that only authorized individuals can perform sensitive operations. 
  
  ---
  
  ### 🛡️ Authorization
  Role-based access control is enforced to determine what actions a user can perform (e.g., only hosts can add properties, only admins can access platform analytics).
  
  **Why it matters:**
  Authorization prevents unauthorized actions, ensuring users can only access and modify resources they own or are permitted to use.

  ---
  
  ### 🚫 Rate Limiting
  Rate limiting is applied to prevent abuse of the API through excessive requests (e.g., brute-force login attempts or spamming endpoints).
  
  **Why it matters:**  
  Rate limiting improves platform stability and protects against denial-of-service (DoS) attacks and resource abuse.


## 🚀 CI/CD Pipeline

### What is CI/CD?

CI/CD stands for **Continuous Integration** and **Continuous Deployment/Delivery**. It is a development practice where code changes are automatically built, tested, and deployed to production. The goal is to ensure rapid and reliable delivery of new features and bug fixes.

### Why It's Important

Implementing a CI/CD pipeline improves the development workflow by:
- Automatically testing code to catch bugs early
- Speeding up the deployment process
- Ensuring consistent and repeatable builds
- Reducing human error in manual deployments

This leads to faster feature releases, higher code quality, and a more robust product.

### Tools Used
- **GitHub Actions**: Automates workflows like testing, building, and deployment directly from the GitHub repository.  
- **Docker**: Packages the application and its dependencies into containers for consistent deployment across environments.  
