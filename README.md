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

### 📅 Bookings
### ✍️ Reviews
### 💳 Payments
