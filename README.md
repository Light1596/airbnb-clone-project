# airbnb-clone-project
## About the Project
The Airbnb Clone Project aims to replicate the development of a full-fledged booking platform similar to Airbnb, offering in-depth experience in backend systems, database architecture, API creation, and application security.
## Team Roles
- Backend Developer: Responsible for implementing API endpoints, database schemas, and business logic.
- Database Administrator: Manages database design, indexing, and optimizations.
- DevOps Engineer: Handles deployment, monitoring, and scaling of the backend services.
- QA Engineer: Ensures the backend functionalities are thoroughly tested and meet quality standards.
## Technology Stack
- Django: A high-level Python web framework used for building the RESTful API.
- Django REST Framework: Provides tools for creating and managing RESTful APIs.
- PostgreSQL: A powerful relational database used for data storage.
- GraphQL: Allows for flexible and efficient querying of data.
- Celery: For handling asynchronous tasks such as sending notifications or processing payments.
- Redis: Used for caching and session management.
- Docker: Containerization tool for consistent development and deployment environments.
- CI/CD Pipelines: Automated pipelines for testing and deploying code changes.
## Database Design
### 🧑 Users
Fields:
- id (Primary Key)
- name
- email
- password_hash
- created_at
#### Relationships:
- A user can own multiple properties.
- A user can make multiple bookings.
- A user can write multiple reviews.

### 🏠 Properties
Fields:
- id (Primary Key)
- title
- description
- location
- price_per_night
- owner_id (Foreign Key referencing Users)

#### Relationships:
- A property belongs to one user (owner).
- A property can have many bookings.
- A property can have many reviews.

### 📅 Bookings
Fields:
- id (Primary Key)
- user_id (Foreign Key referencing Users)
- property_id (Foreign Key referencing Properties)
- start_date
- end_date
- total_price
#### Relationships:

A booking belongs to one user and one property.

#### 💬 Reviews
Fields:
- id (Primary Key)
- user_id (Foreign Key referencing Users)
- property_id (Foreign Key referencing Properties)
- rating (e.g., 1–5)
- comment
- created_at

#### Relationships:

A review is written by a user for a specific property.

### 💳 Payments
Fields:
- id (Primary Key)
- booking_id (Foreign Key referencing Bookings)
- amount
- payment_method
- payment_status
- paid_at

#### Relationships:

A payment is tied to a specific booking.


## Feature Breakdown
1. API Documentation
   - OpenAPI Standard: The backend APIs are documented using the OpenAPI standard to ensure clarity and ease of integration.
   - Django REST Framework: Provides a comprehensive RESTful API for handling CRUD operations on user and property data.
   - GraphQL: Offers a flexible and efficient query mechanism for interacting with the backend.
2. User Authentication
   - Endpoints: /users/, /users/{user_id}/
   - Features: Register new users, authenticate, and manage user profiles.
3. Property Management
   - Endpoints: /properties/, /properties/{property_id}/
   - Features: Create, update, retrieve, and delete property listings.
4. Booking System
   - Endpoints: /bookings/, /bookings/{booking_id}/
   - Features: Make, update, and manage bookings, including check-in and check-out details.
5. Payment Processing
   - Endpoints: /payments/
   - Features: Handle payment transactions related to bookings.
6. Review System
   - Endpoints: /reviews/, /reviews/{review_id}/
   - Features: Post and manage reviews for properties.
## API Security
1. Authentication
    ***What it is:*** Verifies a user's identity using secure login mechanisms such as JWT (JSON Web Tokens).

   Why it matters: Ensures that only registered users can access their accounts, preventing unauthorized access to sensitive data such as profile information, bookings, and 
    saved listings.

2. Authorization
   What it is: Controls user access to specific resources and actions based on roles or ownership (e.g., only hosts can manage their listings).

   Why it matters: Prevents users from accessing or modifying data they don’t own, protecting the integrity of listings, reviews, and bookings.

3. Rate Limiting
   What it is: Restricts the number of requests a client can make to the API within a given timeframe.

   Why it matters: Prevents abuse, such as brute-force login attempts or denial-of-service attacks, which can degrade platform performance and security.

4. Input Validation & Sanitization
   What it is: Ensures all incoming data is clean and meets expected formats.

   Why it matters: Helps prevent common vulnerabilities such as SQL injection or XSS (cross-site scripting), which could compromise user data or the application itself.

5. HTTPS Enforcement
   What it is: Encrypts all traffic between the client and server.

   Why it matters: Ensures that sensitive data like login credentials, payment details, and personal information are protected during transmission.

6. Secure Payment Handling
   What it is: Integrating trusted third-party payment providers (e.g., Stripe) that handle transactions securely.

   Why it matters: Protects users’ financial data and helps meet compliance standards such as PCI-DSS.
## CI/CD Pipeline
### What is CI/CD?
Continuous Integration (CI) is the practice of frequently merging code changes into a shared repository. Each merge triggers automated tests and builds to catch bugs early.

Continuous Deployment (CD) automatically deploys changes to a staging or production environment after they pass all tests and checks.

### Why CI/CD is Important for This Project
- Faster Feedback Loop: Automated testing ensures that bugs are caught early in development, not in production.
- Consistent Deployments: Reduces human error by automating deployment steps, ensuring the application behaves the same across all environments.
- Improved Collaboration: Multiple developers can work together smoothly, as changes are tested and integrated regularly.
- Scalability: As the Airbnb clone grows, CI/CD helps maintain stability while rolling out new features quickly.

### Tools Used or Recommended
- GitHub Actions – Automates workflows for testing and deployment on each push or pull request.
- Docker – Ensures consistency across development, testing, and production environments by containerizing the application.
- Render / Railway / AWS – For automated deployment of the app once the pipeline succeeds.
