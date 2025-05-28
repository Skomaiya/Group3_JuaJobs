Yusuf Molumo - API Architect and Endpoint Designer
Vestine Pendo - Documentation Specialist
Samuel Komaiya - Security Designer
Yvette Kwizera - User Experience Analyst


Executive Summary of Key Design Decisions

1. RESTful Resource-Oriented Architecture
    We adopted a RESTful design for the API, using nouns to represent core resources (e.g., /v1/users, /v1/jobs, /v1/profiles). This ensures intuitive endpoints and predictability for developers integrating with the platform.

2. Clear Ownership & Lifecycle Mapping
    Each resource was designed with explicit ownership and lifecycle considerations. This guided endpoint behaviour (e.g., only clients can create job postings, and only workers can apply) ensures tight control over business logic and data integrity.

3. Consistent and Granular CRUD Operations
    Full CRUD (Create, Read, Update, Delete) capabilities were implemented for all major resources using appropriate HTTP verbs (GET, POST, PUT, PATCH, DELETE), giving API consumers complete control over data.

4. Path Parameters and Sub-resource Nesting
    Nested endpoints such as /v1/users/{id}/jobs or /v1/jobs/{id}/applications provide contextual access to sub-resources, improving usability and aligning with real-world relationships.

5. Schema-Driven Validation
    Each request and response body is governed by JSON schemas defined under components. schemas, ensuring strong typing, validation, and ease of client-side code generation.

6. Descriptive Error Handling
    All endpoints return meaningful HTTP status codes and human-readable error messages (e.g., 404 Not Found, 400 Invalid request body), improving developer experience and reducing debugging time.

7. Modular and Scalable Structure
    The API is modular, allowing future extension (e.g., adding /v1/ratings, /v1/notifications) without architectural redesign.


Highlights of Innovative Approaches

1. User-Centric Design Philosophy
    Endpoints were grouped around the user's journey — from onboarding (signing up), engaging (creating jobs or applying), to interaction (messaging, reviewing), ensuring the platform’s design remains centred around real user workflows.

2. Dual Ownership Resource Handling
    For reviews and payments, which can be owned by multiple user roles (clients and workers), the API allows filtered access via /users/{id}/reviews or /users/{id}/payments, supporting role-based visibility while using shared schemas.

3. Role-Based Resource Access Modelling
    The API design integrates a logical separation of roles (clients vs. workers) at the endpoint level without hardcoding user roles, enabling flexible access control and easy RBAC implementation in future.

4. Nested Data Access for Contextual Clarity
    By providing nested endpoints (e.g., /jobs/{id}/applications), we reduce unnecessary data traversal, speed up response times for relational queries, and align with how consumers typically visualise relationships in a job marketplace.

5. Patch vs. Put Best Practices
    The API differentiates between full resource updates (PUT) and partial updates (PATCH), promoting best REST practices and avoiding unintended data overwrites.

6. Lifecycle Awareness Built into Endpoints
    Resource lifecycle considerations influenced endpoint definitions — for instance, deletion endpoints mirror real-world actions like "withdrawing an application" or "deactivating a listing", reflecting business context in the API behaviour.

7. Future-Proof Schema Definitions
    JSON schemas include optional fields, enums, and proper formatting (e.g., format: email, format: date-time), which sets the foundation for automated testing, client SDK generation, and documentation engines.
