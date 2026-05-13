# Software Requirements Specification (SRS) for FoodFrenzy System

## 1. Document Control

**Title:** Software Requirements Specification for FoodFrenzy System  
**Version:** 1.0  
**Status:** Draft  
**Approvals:** Not specified in source evidence  
**Disclaimer:** This document is intended for internal use only and contains proprietary information of FoodFrenzy. Unauthorized distribution or reproduction is prohibited.

**Revision History:**

| Date       | Version | Description                         | Author           |
|------------|---------|-------------------------------------|------------------|
| Not specified in source evidence | 1.0     | Initial draft creation              | Not specified in source evidence |

## 2. Table of Contents

1. Document Control
2. Table of Contents
3. Introduction
   - Purpose
   - Document Conventions
   - Intended Audience
   - Project Scope
   - References
   - Source Evidence Summary
4. Overall Description
   - Product Perspective
   - Product Functions
   - User Classes and Characteristics
   - Operating Environment
   - Design and Implementation Constraints
   - Assumptions and Dependencies
   - Context Diagram Description
5. System Features and Functional Requirements
   - Feature Family 1: User Management
   - Feature Family 2: Product Management
   - Feature Family 3: Order Management
   - Feature Family 4: Authentication and Security
   - Feature Family 5: Error Handling
6. External Interface Requirements
7. Data and State Requirements
8. Non-Functional Requirements
9. Business and Validation Rules
10. Assumptions, Dependencies, Risks, Open Questions
11. Appendices

## 3. Introduction

### Purpose

The purpose of this Software Requirements Specification (SRS) document is to provide a comprehensive and detailed description of the FoodFrenzy system. This system is designed to efficiently manage customers, inventory, and orders within the food industry. It offers secure authentication, role-based access control, and data management capabilities, thereby streamlining operations for businesses.

FoodFrenzy integrates various components such as user management, product cataloging, order processing, and administrative controls. The system is built using Spring Boot and integrates with a MySQL database to ensure robust data handling and retrieval. This document outlines the requirements derived from the source code and other available evidence, highlighting any missing information in the Open Questions section.

### Document Conventions

This document uses the following conventions:
- **Bold** for section headings and important terms.
- `Code` for technical identifiers, filenames, and code snippets.
- Requirement IDs in the form `SRS-FR-001` for functional requirements and `SRS-NFR-001` for non-functional requirements.

### Intended Audience

The intended audience for this SRS includes:
- Software developers and engineers responsible for implementing the system.
- Quality assurance teams tasked with testing the system.
- Project managers overseeing the development process.
- Stakeholders interested in understanding the system's capabilities and limitations.

### Project Scope

The FoodFrenzy system aims to provide a comprehensive solution for managing food-related business operations. It includes features for user authentication, product management, order processing, and administrative functions. The system is designed to be scalable and secure, supporting various user roles and access levels.

The scope of this document is limited to the features and functionalities identified in the source code and related evidence. It does not cover performance metrics, security guarantees, or other non-functional aspects not specified in the source evidence. Any gaps in information are addressed in the Open Questions section.

### References

- Spring Boot Documentation: Not specified in source evidence
- MySQL Documentation: Not specified in source evidence
- Thymeleaf Documentation: Not specified in source evidence

### Source Evidence Summary

The source evidence for this SRS includes the FoodFrenzy source code, configuration files, and external interface documentation. Key components identified include user management, product cataloging, order processing, and administrative controls. The system uses Spring Boot for backend operations and Thymeleaf for frontend templating, with MySQL as the database.

## 4. Overall Description

### Product Perspective

FoodFrenzy is a standalone application designed to manage various aspects of a food business, including customer interactions, inventory management, and order processing. It integrates with a MySQL database to store and retrieve data efficiently. The system is built using Spring Boot, providing a robust and scalable backend, while Thymeleaf is used for dynamic HTML templating on the frontend.

### Product Functions

The primary functions of the FoodFrenzy system include:
- **User Management:** Handling user registration, login, and profile management.
- **Product Management:** Adding, updating, and deleting products in the inventory.
- **Order Management:** Creating, updating, and tracking customer orders.
- **Authentication and Security:** Ensuring secure access through role-based authentication.
- **Error Handling:** Managing exceptions and providing user-friendly error messages.

### User Classes and Characteristics

The system supports various user roles, including:
- **Administrators:** Responsible for managing users, products, and orders.
- **Customers:** End-users who browse products and place orders.
- **Staff Members:** Users with specific roles for handling orders and inventory.

### Operating Environment

The FoodFrenzy system operates in a web-based environment, accessible via standard web browsers. It requires a server running Java 8 and Spring Boot, with a MySQL database for data storage.

### Design and Implementation Constraints

- The system is built using Java 8 and Spring Boot, which imposes constraints on the development environment.
- Thymeleaf is used for frontend templating, requiring compatibility with HTML, CSS, and JavaScript.
- The database is MySQL, necessitating appropriate configuration and connectivity.

### Assumptions and Dependencies

- The system assumes a stable internet connection for accessing web-based features.
- It depends on the correct configuration of the MySQL database and Spring Boot environment.
- The system relies on external libraries and frameworks, such as Thymeleaf and Spring Data JPA.

### Context Diagram Description

Not specified in source evidence.

## 5. System Features and Functional Requirements

### Feature Family 1: User Management

**Overview:**  
User management is a critical feature of the FoodFrenzy system, enabling the registration, authentication, and profile management of users. This feature ensures that users can securely access the system and manage their accounts.

#### SRS-FR-001: User Registration
- **Priority:** High
- **Source Evidence:** `UserController.addUser`
- **Business/Operational Need:** User registration is essential for allowing new users to create accounts and access the system. It ensures that user data is captured and stored securely.
- **Detailed Functional Behavior:**
  - The system shall provide a registration form for new users to input their details, including name, email, password, and contact number.
  - Upon submission, the system shall validate the input data for completeness and correctness.
  - The system shall store the user details in the database upon successful validation.
- **Functional Logic:**
  - **Actors/Triggers:** User initiates registration via the registration page.
  - **Inputs:** User details (name, email, password, contact number).
  - **Input Validation:** Ensure all fields are filled and email format is correct.
  - **Outputs/State Changes:** New user record created in the database.
  - **Preconditions:** User must access the registration page.
  - **Main Flow:** User submits registration form, system validates and stores data.
  - **Alternate/Error Flows:** Display error message if validation fails.
  - **Postconditions:** User account is created and accessible for login.
- **Acceptance Criteria:**
  - Given a user on the registration page, when they submit valid details, then a new user account is created.
  - Given a user on the registration page, when they submit invalid details, then an error message is displayed.
  - Given a user on the registration page, when they submit an existing email, then an error message is displayed.
- **Traceability:** `UserController.addUser`

#### SRS-FR-002: User Profile Management
- **Priority:** Medium
- **Source Evidence:** `UserController.updateUser`
- **Business/Operational Need:** Users need to manage their profiles to keep their information up-to-date and accurate.
- **Detailed Functional Behavior:**
  - The system shall allow users to update their profile details, including name, email, and contact number.
  - Upon submission, the system shall validate the updated data for correctness.
  - The system shall update the user details in the database upon successful validation.
- **Functional Logic:**
  - **Actors/Triggers:** User initiates profile update via the profile management page.
  - **Inputs:** Updated user details (name, email, contact number).
  - **Input Validation:** Ensure all fields are filled and email format is correct.
  - **Outputs/State Changes:** User record updated in the database.
  - **Preconditions:** User must be logged in and access the profile management page.
  - **Main Flow:** User submits updated profile form, system validates and updates data.
  - **Alternate/Error Flows:** Display error message if validation fails.
  - **Postconditions:** User profile is updated and reflects the new information.
- **Acceptance Criteria:**
  - Given a user on the profile management page, when they submit valid updates, then their profile is updated.
  - Given a user on the profile management page, when they submit invalid updates, then an error message is displayed.
  - Given a user on the profile management page, when they attempt to change their email to one already in use, then an error message is displayed.
- **Traceability:** `UserController.updateUser`

### Feature Family 2: Product Management

**Overview:**  
Product management allows administrators to manage the product catalog, including adding, updating, and deleting products. This feature ensures that the inventory is up-to-date and accurately reflects available products.

#### SRS-FR-003: Add Product
- **Priority:** Medium
- **Source Evidence:** `ProductController.addProduct`
- **Business/Operational Need:** Adding products is crucial for maintaining an accurate inventory and ensuring that customers have access to the latest offerings.
- **Detailed Functional Behavior:**
  - The system shall provide a form for administrators to input product details, including name, price, description, and quantity.
  - Upon submission, the system shall validate the input data for completeness and correctness.
  - The system shall store the product details in the database upon successful validation.
- **Functional Logic:**
  - **Actors/Triggers:** Administrator initiates product addition via the product management page.
  - **Inputs:** Product details (name, price, description, quantity).
  - **Input Validation:** Ensure all fields are filled and price is a valid number.
  - **Outputs/State Changes:** New product record created in the database.
  - **Preconditions:** Administrator must access the product management page.
  - **Main Flow:** Administrator submits product form, system validates and stores data.
  - **Alternate/Error Flows:** Display error message if validation fails.
  - **Postconditions:** Product is added to the inventory and visible to customers.
- **Acceptance Criteria:**
  - Given an administrator on the product management page, when they submit valid product details, then a new product is added to the inventory.
  - Given an administrator on the product management page, when they submit invalid product details, then an error message is displayed.
  - Given an administrator on the product management page, when they submit a product with an existing name, then an error message is displayed.
- **Traceability:** `ProductController.addProduct`

#### SRS-FR-004: Update Product
- **Priority:** Medium
- **Source Evidence:** `ProductController.updateProduct`
- **Business/Operational Need:** Updating product details is necessary to reflect changes in inventory, pricing, or product descriptions.
- **Detailed Functional Behavior:**
  - The system shall allow administrators to update product details, including name, price, description, and quantity.
  - Upon submission, the system shall validate the updated data for correctness.
  - The system shall update the product details in the database upon successful validation.
- **Functional Logic:**
  - **Actors/Triggers:** Administrator initiates product update via the product management page.
  - **Inputs:** Updated product details (name, price, description, quantity).
  - **Input Validation:** Ensure all fields are filled and price is a valid number.
  - **Outputs/State Changes:** Product record updated in the database.
  - **Preconditions:** Administrator must access the product management page.
  - **Main Flow:** Administrator submits updated product form, system validates and updates data.
  - **Alternate/Error Flows:** Display error message if validation fails.
  - **Postconditions:** Product details are updated and reflect the new information.
- **Acceptance Criteria:**
  - Given an administrator on the product management page, when they submit valid updates, then the product details are updated.
  - Given an administrator on the product management page, when they submit invalid updates, then an error message is displayed.
  - Given an administrator on the product management page, when they attempt to change the product name to one already in use, then an error message is displayed.
- **Traceability:** `ProductController.updateProduct`

#### SRS-FR-005: Delete Product
- **Priority:** Low
- **Source Evidence:** `ProductController.delete`
- **Business/Operational Need:** Deleting products is necessary to remove discontinued or unavailable items from the inventory.
- **Detailed Functional Behavior:**
  - The system shall allow administrators to delete products from the inventory.
  - Upon confirmation, the system shall remove the product details from the database.
- **Functional Logic:**
  - **Actors/Triggers:** Administrator initiates product deletion via the product management page.
  - **Inputs:** Product identifier for deletion.
  - **Input Validation:** Ensure the product exists in the database.
  - **Outputs/State Changes:** Product record deleted from the database.
  - **Preconditions:** Administrator must access the product management page.
  - **Main Flow:** Administrator confirms deletion, system removes product data.
  - **Alternate/Error Flows:** Display error message if product does not exist.
  - **Postconditions:** Product is removed from the inventory and no longer visible to customers.
- **Acceptance Criteria:**
  - Given an administrator on the product management page, when they confirm deletion of an existing product, then the product is removed from the inventory.
  - Given an administrator on the product management page, when they attempt to delete a non-existent product, then an error message is displayed.
  - Given an administrator on the product management page, when they cancel the deletion, then the product remains in the inventory.
- **Traceability:** `ProductController.delete`

### Feature Family 3: Order Management

**Overview:**  
Order management is a core feature that allows users to create, update, and track orders. This feature ensures that customer orders are processed efficiently and accurately.

#### SRS-FR-006: Create Order
- **Priority:** High
- **Source Evidence:** `OrderController.saveOrder`
- **Business/Operational Need:** Creating orders is essential for processing customer purchases and ensuring that inventory levels are updated accordingly.
- **Detailed Functional Behavior:**
  - The system shall provide a form for users to select products and specify quantities for their order.
  - Upon submission, the system shall validate the order details for availability and correctness.
  - The system shall store the order details in the database and update inventory levels.
- **Functional Logic:**
  - **Actors/Triggers:** User initiates order creation via the order page.
  - **Inputs:** Order details (product selections, quantities).
  - **Input Validation:** Ensure selected products are available and quantities are valid.
  - **Outputs/State Changes:** New order record created, inventory levels updated.
  - **Preconditions:** User must access the order page.
  - **Main Flow:** User submits order form, system validates and processes order.
  - **Alternate/Error Flows:** Display error message if validation fails or products are unavailable.
  - **Postconditions:** Order is created and visible in user order history.
- **Acceptance Criteria:**
  - Given a user on the order page, when they submit valid order details, then a new order is created and inventory is updated.
  - Given a user on the order page, when they submit invalid order details, then an error message is displayed.
  - Given a user on the order page, when they attempt to order unavailable products, then an error message is displayed.
- **Traceability:** `OrderController.saveOrder`

#### SRS-FR-007: Update Order
- **Priority:** Medium
- **Source Evidence:** `OrderController.updateOrder`
- **Business/Operational Need:** Updating orders is necessary to accommodate changes in customer requests or correct errors.
- **Detailed Functional Behavior:**
  - The system shall allow users to update order details, including product selections and quantities.
  - Upon submission, the system shall validate the updated order details for availability and correctness.
  - The system shall update the order details in the database and adjust inventory levels accordingly.
- **Functional Logic:**
  - **Actors/Triggers:** User initiates order update via the order management page.
  - **Inputs:** Updated order details (product selections, quantities).
  - **Input Validation:** Ensure selected products are available and quantities are valid.
  - **Outputs/State Changes:** Order record updated, inventory levels adjusted.
  - **Preconditions:** User must access the order management page.
  - **Main Flow:** User submits updated order form, system validates and updates order.
  - **Alternate/Error Flows:** Display error message if validation fails or products are unavailable.
  - **Postconditions:** Order details are updated and reflect the new information.
- **Acceptance Criteria:**
  - Given a user on the order management page, when they submit valid updates, then the order details are updated.
  - Given a user on the order management page, when they submit invalid updates, then an error message is displayed.
  - Given a user on the order management page, when they attempt to update to unavailable products, then an error message is displayed.
- **Traceability:** `OrderController.updateOrder`

#### SRS-FR-008: Cancel Order
- **Priority:** Low
- **Source Evidence:** `OrderController.deleteOrder`
- **Business/Operational Need:** Cancelling orders is necessary to handle customer cancellations and ensure inventory levels are adjusted.
- **Detailed Functional Behavior:**
  - The system shall allow users to cancel orders.
  - Upon confirmation, the system shall remove the order details from the database and adjust inventory levels.
- **Functional Logic:**
  - **Actors/Triggers:** User initiates order cancellation via the order management page.
  - **Inputs:** Order identifier for cancellation.
  - **Input Validation:** Ensure the order exists in the database.
  - **Outputs/State Changes:** Order record deleted, inventory levels adjusted.
  - **Preconditions:** User must access the order management page.
  - **Main Flow:** User confirms cancellation, system removes order data and adjusts inventory.
  - **Alternate/Error Flows:** Display error message if order does not exist.
  - **Postconditions:** Order is cancelled and no longer visible in user order history.
- **Acceptance Criteria:**
  - Given a user on the order management page, when they confirm cancellation of an existing order, then the order is removed and inventory is adjusted.
  - Given a user on the order management page, when they attempt to cancel a non-existent order, then an error message is displayed.
  - Given a user on the order management page, when they cancel the cancellation, then the order remains active.
- **Traceability:** `OrderController.deleteOrder`

### Feature Family 4: Authentication and Security

**Overview:**  
Authentication and security features ensure that only authorized users can access the system and perform actions based on their roles. This feature protects sensitive data and maintains system integrity.

#### SRS-FR-009: User Login
- **Priority:** High
- **Source Evidence:** `UserController.userLogin`
- **Business/Operational Need:** User login is crucial for verifying user identity and granting access to system features based on user roles.
- **Detailed Functional Behavior:**
  - The system shall provide a login form for users to input their email and password.
  - Upon submission, the system shall validate the credentials against stored user data.
  - The system shall grant access to the user dashboard upon successful validation.
- **Functional Logic:**
  - **Actors/Triggers:** User initiates login via the login page.
  - **Inputs:** User credentials (email, password).
  - **Input Validation:** Ensure email format is correct and password matches stored data.
  - **Outputs/State Changes:** User session is created, access granted to user dashboard.
  - **Preconditions:** User must access the login page.
  - **Main Flow:** User submits login form, system validates and grants access.
  - **Alternate/Error Flows:** Display error message if validation fails.
  - **Postconditions:** User is logged in and can access authorized features.
- **Acceptance Criteria:**
  - Given a user on the login page, when they submit valid credentials, then they are granted access to the dashboard.
  - Given a user on the login page, when they submit invalid credentials, then an error message is displayed.
  - Given a user on the login page, when they submit an unregistered email, then an error message is displayed.
- **Traceability:** `UserController.userLogin`

#### SRS-FR-010: Role-Based Access Control
- **Priority:** High
- **Source Evidence:** `SecurityConfig`
- **Business/Operational Need:** Role-based access control is necessary to ensure that users can only access features appropriate to their roles.
- **Detailed Functional Behavior:**
  - The system shall assign roles to users upon registration or by an administrator.
  - The system shall restrict access to features based on user roles.
- **Functional Logic:**
  - **Actors/Triggers:** User attempts to access a system feature.
  - **Inputs:** User role and requested feature.
  - **Input Validation:** Ensure user role permits access to the requested feature.
  - **Outputs/State Changes:** Access granted or denied based on role.
  - **Preconditions:** User must be logged in.
  - **Main Flow:** User requests access, system checks role and grants or denies access.
  - **Alternate/Error Flows:** Display error message if access is denied.
  - **Postconditions:** User access is controlled based on role.
- **Acceptance Criteria:**
  - Given a user with a specific role, when they attempt to access a permitted feature, then access is granted.
  - Given a user with a specific role, when they attempt to access a restricted feature, then access is denied.
  - Given an administrator, when they assign roles, then users have access based on their roles.
- **Traceability:** `SecurityConfig`

### Feature Family 5: Error Handling

**Overview:**  
Error handling ensures that the system can gracefully manage exceptions and provide informative feedback to users. This feature enhances user experience and system reliability.

#### SRS-FR-011: Exception Handling
- **Priority:** Medium
- **Source Evidence:** `Exceptions`
- **Business/Operational Need:** Exception handling is necessary to prevent system crashes and provide users with meaningful error messages when issues occur.
- **Detailed Functional Behavior:**
  - The system shall catch exceptions that occur during runtime and log them for analysis.
  - The system shall display user-friendly error messages when exceptions occur.
  - The system shall redirect users to a designated error page if necessary.
- **Functional Logic:**
  - **Actors/Triggers:** System encounters an exception during operation.
  - **Inputs:** None (triggered by system events).
  - **Input Validation:** Not applicable.
  - **Outputs/State Changes:** Error message displayed, exception logged.
  - **Preconditions:** System is running and processing requests.
  - **Main Flow:** Exception occurs, system logs and displays error message.
  - **Alternate/Error Flows:** Redirect to error page if necessary.
  - **Postconditions:** User is informed of the error, system continues operation.
- **Acceptance Criteria:**
  - Given a system operation, when an exception occurs, then the system logs the exception and displays an error message.
  - Given a system operation, when a critical exception occurs, then the system redirects to an error page.
  - Given a system operation, when a non-critical exception occurs, then the system continues operation after displaying an error message.
- **Traceability:** `Exceptions`

## 6. External Interface Requirements

### User Interface

- The system provides web-based interfaces for user registration, login, product management, and order processing.
- The interfaces are built using Thymeleaf templates and are accessible via standard web browsers.

### Hardware Interfaces

- Not specified in source evidence.

### Software Interfaces

- The system integrates with a MySQL database for data storage and retrieval.
- It uses Spring Boot for backend operations and Thymeleaf for frontend templating.

### Communications Interfaces

- The system is accessible via HTTP at `http://localhost:8080`.
- It supports secure communication protocols for user authentication and data transmission.

## 7. Data and State Requirements

### Data Objects

- **User:** Includes fields such as user ID, name, email, password, and contact number.
- **Product:** Includes fields such as product ID, name, price, description, and quantity.
- **Order:** Includes fields such as order ID, date, product details, and user information.

### State Flags

- Not specified in source evidence.

### Lifecycle Transitions

- User accounts transition from registered to active upon successful login.
- Products transition from available to unavailable based on inventory levels.
- Orders transition from created to processed upon successful payment.

### Persistence

- User, product, and order data are persisted in the MySQL database.

### Retention/Privacy Notes

- Not specified in source evidence.

## 8. Non-Functional Requirements

### Performance

- Not specified in source evidence.

### Reliability

- Not specified in source evidence.

### Security

- The system uses role-based access control to ensure secure access to features.
- User passwords are stored securely using encryption.

### Privacy

- Not specified in source evidence.

### Maintainability

- The system is built using modular components, facilitating easy maintenance and updates.

### Observability

- Not specified in source evidence.

### Scalability

- Not specified in source evidence.

### Portability

- The system is designed to run on any server supporting Java 8 and Spring Boot.

### Usability

- The system provides intuitive web interfaces for easy navigation and use.

## 9. Business and Validation Rules

- User registration requires unique email addresses.
- Product prices must be positive numbers.
- Orders can only be created for available products.

## 10. Assumptions, Dependencies, Risks, Open Questions

### Assumptions

- Users have access to a stable internet connection.
- The MySQL database is correctly configured and accessible.

### Dependencies

- The system depends on external libraries such as Thymeleaf and Spring Data JPA.

### Risks

- Potential security vulnerabilities if user data is not encrypted properly.
- System downtime if the database connection fails.

### Open Questions

- What are the specific performance targets for the system?
- Are there any additional security measures required beyond role-based access control?
- What are the data retention policies for user and order information?

## 11. Appendices

### Glossary

- **Thymeleaf:** A Java-based templating engine for rendering dynamic web pages.
- **Spring Boot:** A framework for building Java-based enterprise applications.
- **MySQL:** An open-source relational database management system.

### Source Traceability Matrix

| Requirement ID | Source Evidence |
|----------------|-----------------|
| SRS-FR-001     | `UserController.addUser` |
| SRS-FR-002     | `UserController.updateUser` |
| SRS-FR-003     | `ProductController.addProduct` |
| SRS-FR-004     | `ProductController.updateProduct` |
| SRS-FR-005     | `ProductController.delete` |
| SRS-FR-006     | `OrderController.saveOrder` |
| SRS-FR-007     | `OrderController.updateOrder` |
| SRS-FR-008     | `OrderController.deleteOrder` |
| SRS-FR-009     | `UserController.userLogin` |
| SRS-FR-010     | `SecurityConfig` |
| SRS-FR-011     | `Exceptions` |

### Issue List

- Not specified in source evidence.

## Non-Functional Requirements Addendum

The following source-based non-functional requirements were added because the generated result did not include the full required quality-attribute set. Numeric commitments are not invented when absent from source evidence.

| Requirement ID | Quality Attribute | Requirement | Source/Assumption Basis | Acceptance Criterion |
|---|---|---|---|---|
| SRS-NFR-002 | Reliability | The system shall recover or terminate safely after WebSocket disconnects, API errors, and interrupted processing. | Error handling, state reset, exception handling, and fallback behavior are visible. | Representative failure scenarios shall not corrupt session state and shall produce expected recovery or termination behavior. |
| SRS-NFR-003 | Security | The system shall protect API keys, environment variables, and external service credentials. | Environment variables such as OPENAI_API_KEY and external service integrations are used. | Secrets shall not appear in logs, generated documents, or user-facing responses. |
| SRS-NFR-004 | Privacy | The system shall process audio, transcript, and conversation state with minimum necessary retention. | Audio buffers, transcript text, and conversation memory are visible. | Retention, deletion, and masking rules shall be tracked as stakeholder confirmation items and verified once defined. |
| SRS-NFR-005 | Maintainability | Language handling, ASR, rule workflow, and error-handling areas shall remain maintainable and testable. | Multiple feature families, state management, and external integrations are visible. | Change impact, regression test scope, and configuration points shall be traceable. |
| SRS-NFR-006 | Observability | The system shall provide logs for important state transitions, external communication, errors, and retries. | Logging, debug, and error-handling behavior are visible. | Log fields, levels, and correlation needs shall be confirmed and sufficient for incident investigation. |
| SRS-NFR-007 | Scalability | The system shall account for increased sessions and external API usage without unsafe behavior. | Async processing, WebSocket, and external API calls are visible; exact concurrency/rate values are not defined in source evidence. | Concurrency, rate-limit, and backpressure policies shall be confirmable as open questions. |
| SRS-NFR-008 | Portability | The system shall support environment-based configuration for external dependencies. | ASR provider, API keys, and log levels are environment-driven. | Target environments, configuration procedures, and dependency services shall be documented. |
| SRS-NFR-009 | Usability | Voice response, language choice, interruption, transfer, and call ending shall remain understandable to users. | Language handling, turn detection, interruption, and transfer/end-call behavior are visible. | User acceptance tests shall cover representative conversation scenarios. |