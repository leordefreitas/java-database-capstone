## Section 1: Architecture summary
This Spring Boot application uses both MVC and REST controllers. Thymeleaf templates are used to render the Admin and Doctor dashboards, while REST APIs handle all other modules. The application connects to two databases: MySQL is used for storing structured data such as patients, doctors, appointments, and admin records using JPA entities; MongoDB is used for managing flexible, document-based data such as prescriptions. All controller requests are routed through a shared service layer, which delegates operations to the appropriate repositories depending on the data source.

## Section 2: Numbered flow of data and control
1. **User Access**
    - Users interact with the system via two interfaces: Thymeleaf-based dashboards for Admin and Doctor roles, and REST API endpoints for modules like Appointments and Patient Records.

2. **Controller Routing**
    - Based on the type of request, the system routes it to either a Thymeleaf MVC controller (for rendering HTML views) or a REST controller (for handling API requests and returning JSON responses).

3. **Service Layer Execution**
    - All controllers delegate the request to the Service Layer, which contains the business logic. It handles validation, workflows (e.g., checking doctor availability), and coordinates actions between components.

4. **Repository Access**
    - The Service Layer interacts with repositories to access data. MySQL repositories (using Spring Data JPA) manage structured records like patients and appointments, while MongoDB repositories handle flexible documents like prescriptions.

5. **Database Operations**
    - The repositories communicate directly with the databases: MySQL stores core entities in relational format, and MongoDB stores document-based prescription data, allowing for schema flexibility.

6. **Model Binding**
    - Data fetched from the databases is mapped into Java model classes: JPA entities for MySQL and document objects (annotated with `@Document`) for MongoDB. These models are used across the system.

7. **Response Generation**
    - Finally, the models are used to generate responses: in the MVC flow, they are passed to Thymeleaf templates to render dynamic HTML; in the REST flow, they are serialized into JSON and returned via HTTP response.
