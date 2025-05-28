
## Team Members and Roles

* **Yusuf Molumo** – API Architect and Endpoint Designer
* **Vestine Pendo** – Documentation Specialist
* **Samuel Komaiya** – Security Designer
* **Yvette Kwizera** – User Experience Analyst

---

##  Executive Summary of Key Design Decisions

### 1. RESTful Resource-Oriented Architecture

We adopted a RESTful design for the API, using nouns to represent core resources (e.g., `/v1/users`, `/v1/jobs`, `/v1/profiles`). This ensures intuitive endpoints and predictability for developers integrating with the platform.

### 2. Clear Ownership & Lifecycle Mapping

Each resource includes explicit ownership and lifecycle rules. For example, only clients can create job postings, and only workers can apply. This enforces business logic and ensures data integrity.

### 3. Consistent and Granular CRUD Operations

All major resources support full CRUD functionality via appropriate HTTP verbs (`GET`, `POST`, `PUT`, `PATCH`, `DELETE`). This gives developers comprehensive control over resource management.

### 4. Path Parameters and Sub-resource Nesting

Nesting endpoints like `/v1/users/{id}/jobs` and `/v1/jobs/{id}/applications` improves contextual access and reflects real-world resource relationships.

### 5. Schema-Driven Validation

All request/response bodies are governed by JSON schemas under `components.schemas`, enabling strict typing, validation, and easier code generation for clients.

### 6. Descriptive Error Handling

We return meaningful HTTP status codes and human-readable messages (e.g., `404 Not Found`, `400 Invalid request body`) to improve developer experience and reduce debugging time.

### 7. Modular and Scalable Structure

The modular design supports future extensibility — for example, adding new resources like `/v1/ratings` or `/v1/notifications` without breaking the existing architecture.

---

##  Highlights of Innovative Approaches

### 1. User-Centric Design Philosophy

Endpoints follow the user's journey — onboarding, engagement, and interaction — to ensure the platform remains centered around real-world workflows.

### 2. Dual Ownership Resource Handling

For shared resources like reviews and payments, endpoints like `/users/{id}/reviews` or `/users/{id}/payments` support role-based access while maintaining shared schema consistency.

### 3. Role-Based Resource Access Modelling

Roles (clients, workers) are logically separated at the endpoint level, without hardcoding. This allows flexible access control and simplifies future RBAC integration.

### 4. Nested Data Access for Contextual Clarity

Nested routes like `/jobs/{id}/applications` reduce redundant data traversal, improve performance, and match how consumers visualize resource relationships.

### 5. PATCH vs. PUT Best Practices

The API distinguishes between `PUT` (full updates) and `PATCH` (partial updates), following REST best practices and avoiding data loss through unintended overwrites.

### 6. Lifecycle Awareness Built into Endpoints

Endpoint definitions reflect real-world workflows — e.g., deleting an application is treated as "withdrawing", aligning API operations with user expectations.

### 7. Future-Proof Schema Definitions

Schemas use optional fields, enumerations, and formats (e.g., `format: email`, `format: date-time`) to enable automated testing, client SDK generation, and robust documentation engines.

---

### API Documentation:
https://app.swaggerhub.com/apis-docs/alu-dea/Group3_JuaJobs_API/1.0.0
