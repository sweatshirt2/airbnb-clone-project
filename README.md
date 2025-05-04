# Airbnb Clone Backend

A simple backend for an Airbnb clone built with:

- **Django** and **Django REST Framework**
- **MySQL** for the database
- **GraphQL** (using Graphene-Django) and **REST API** support
- **Git** and **GitHub** for version control
- **Jenkins** for CI/CD pipeline

This project provides both RESTful and GraphQL APIs for listing properties, booking management, and user authentication.

## Technologies Used

- Django
- Django REST Framework
- GraphQL (Graphene-Django)
- MySQL
- Jenkins
- Git & GitHub

## APIs

- **REST API**: For traditional endpoints (CRUD operations)
- **GraphQL API**: For flexible queries and mutations

## CI/CD

- Code is managed on **GitHub**
- **Jenkins** automates testing and deployment

## Team Roles

A successful software development project relies on a well-structured team where each member has clear responsibilities. Below are the primary roles typically involved in such projects:

### 1. Product Owner

The Product Owner serves as the bridge between the stakeholders and the development team. They are responsible for defining the product vision, managing the product backlog, and ensuring that the team delivers value to the business.

### 2. Project Manager

The Project Manager oversees the project's execution, ensuring it stays on schedule and within budget. They coordinate between teams, manage risks, and communicate progress to stakeholders.

### 3. Business Analyst

The Business Analyst identifies business needs and translates them into technical requirements. They work closely with stakeholders to ensure the final product aligns with business objectives.

### 4. Software Architect

The Software Architect designs the overall system structure, making high-level decisions on technologies and frameworks. They ensure the system's scalability, performance, and maintainability.

### 5. Backend Developer

Backend Developers focus on server-side development, creating APIs, managing databases, and ensuring the application's logic functions correctly.

### 6. Frontend Developer

Frontend Developers build the user interface, ensuring a seamless and responsive user experience across devices.

### 7. UI/UX Designer

UI/UX Designers craft the visual elements and user experience of the application. They conduct user research, design wireframes, and ensure the product is intuitive and user-friendly.

### 8. Quality Assurance (QA) Engineer

QA Engineers test the application to identify bugs and ensure it meets quality standards. They develop test plans, execute tests, and report issues for resolution.

### 9. DevOps Engineer

DevOps Engineers manage the infrastructure and deployment processes. They automate workflows, monitor system performance, and ensure continuous integration and delivery.

### 10. Database Administrator (DBA)

DBAs are responsible for designing, implementing, and maintaining the database systems. They ensure data integrity, optimize performance, and manage backups and recovery.

## Technology Stack

Below is a list of the main technologies used in this project, along with a brief explanation of their purpose:

- **Django**: A high-level Python web framework used to build secure and maintainable web applications quickly.

- **Django REST Framework**: An extension of Django that helps build RESTful APIs easily, supporting features like authentication, serialization, and viewsets.

- **GraphQL (Graphene-Django)**: A query language for APIs that allows clients to request only the data they need. Graphene-Django integrates GraphQL into Django applications.

- **MySQL**: A relational database management system used to store and manage structured data for the application.

- **Jenkins**: An open-source automation server used to build, test, and deploy the project continuously (CI/CD pipeline).

- **Git & GitHub**: Git is a version control system used to track changes in source code. GitHub is a platform for hosting Git repositories and collaborating on code with others.

##Database Design

### 1. **User**

Represents the people using the platform, either as guests or hosts.

**Key Fields:**

- `id`: Unique identifier
- `name`: Full name of the user
- `email`: Email address
- `role`: Defines if the user is a guest or a host
- `created_at`: Registration date

**Relationships:**

- A user can list multiple properties (if host).
- A user can make multiple bookings (if guest).
- A user can write multiple reviews.

### 2. **Property**

Represents a listing available for booking.

**Key Fields:**

- `id`: Unique identifier
- `title`: Property title
- `description`: Details about the property
- `price_per_night`: Cost per night
- `host_id`: Linked to the user who owns the property

**Relationships:**

- A property belongs to one host (user).
- A property can have many bookings.
- A property can have multiple reviews.

### 3. **Booking**

Represents a reservation made by a user for a property.

**Key Fields:**

- `id`: Unique identifier
- `user_id`: The guest who made the booking
- `property_id`: The booked property
- `start_date`: Check-in date
- `end_date`: Check-out date

**Relationships:**

- A booking belongs to one user (guest).
- A booking is for one property.

### 4. **Review**

Captures feedback from a guest after a stay.

**Key Fields:**

- `id`: Unique identifier
- `user_id`: The guest who wrote the review
- `property_id`: The reviewed property
- `rating`: Numeric score (e.g., 1–5)
- `comment`: Textual feedback

**Relationships:**

- A review is written by a user.
- A review is associated with a property.

### 5. **Payment**

Tracks financial transactions related to bookings.

**Key Fields:**

- `id`: Unique identifier
- `booking_id`: Associated booking
- `amount`: Payment amount
- `status`: Payment status (e.g., pending, completed)
- `payment_date`: Date of payment

**Relationships:**

- A payment is linked to a booking.

## Feature Breakdown

This project includes several key features that work together to simulate a real-world Airbnb-like platform:

### 1. User Management

Users can register, log in, and manage their profiles. The system supports both guests and hosts, each with distinct permissions and capabilities.

### 2. Property Management

Hosts can list new properties with details like location, pricing, photos, and descriptions. They can also edit or remove listings as needed.

### 3. Booking System

Guests can browse properties, select dates, and book stays. The system ensures availability, calculates total costs, and stores booking details.

### 4. Review and Rating System

After a stay, guests can leave reviews and rate their experience. This helps other users make informed decisions and encourages quality among hosts.

### 5. Payment Integration

Secure payment processing is implemented for bookings. Users are charged based on stay duration and pricing, and transactions are tracked through a payment system.

## API Security

Securing the API is a critical part of building a reliable and trustworthy platform. Below are the key security measures implemented in this project and their importance:

### 1. Authentication

Only registered users can access protected endpoints by using secure login methods like token-based authentication (e.g., JWT). This ensures that the system knows who is making each request and protects user accounts from unauthorized access.

### 2. Authorization

Role-based access control is used to restrict what actions a user can perform (e.g., only hosts can list properties, only guests can book). This prevents users from accessing or modifying data they do not own or have permission to use.

### 3. Rate Limiting

Rate limiting is applied to prevent abuse of the API by restricting the number of requests a user can make in a short time. This helps protect the platform from spam, denial-of-service (DoS) attacks, and excessive load.

### 4. Input Validation and Sanitization

All user input is validated and sanitized to prevent common attacks like SQL injection, XSS (Cross-Site Scripting), and data corruption. This maintains data integrity and system stability.

### 5. Secure Payment Handling

Sensitive financial transactions are securely processed using encryption and third-party payment gateways. This ensures the protection of payment data and builds user trust.

By implementing these security practices, the platform ensures user privacy, data protection, and overall system reliability.

## CI/CD Pipeline

CI/CD stands for Continuous Integration and Continuous Deployment. It is a development practice where code changes are automatically tested, built, and deployed to ensure faster and more reliable software delivery. This helps reduce bugs, improve code quality, and speed up development cycles.

In this project, a CI/CD pipeline ensures that every code update is automatically tested and deployed without manual intervention. It allows the team to catch issues early, maintain consistency, and deliver new features faster.

**Tools Used:**

- **Docker**: Creates consistent development and production environments using containerization.
- **Jenkins** : Can also be used for automating build and deployment tasks if preferred over GitHub Actions.
- **GitHub Actions** _(optional)_: Automates workflows for testing, building, and deploying the application when changes are pushed to the repository.
