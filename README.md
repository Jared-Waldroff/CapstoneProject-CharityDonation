# Charity Donation 

## Overview
This project involves the development of a web application designed to enhance interaction between vendors and attendees at conventions. The application aims to modernize the traditional practice of distributing swag by leveraging technology to facilitate charitable contributions while creating a more engaging experience for attendees. Link to production running on UBC server: https://cs499section3.ok.ubc.ca/charity/group6/app/

If you need to review the implementation, please contact me directly for restricted access.

## Table of Contents
1. [System Architecture](#system-architecture)
2. [Components](#components)
4. [Installation and Setup](#installation-and-setup)
5. [Usage](#usage)
6. [Technologies Used](#technologies-used)
7. [Current Features](#features)
   
## System Architecture
**Architecture Diagram:**
Our system uses the CLEAN system architecture according to what the KelownaSoftware template provided us with. The architecture allows us to maintain consitency and reusability that is so important in a larger scale project.


![Clean Diagram](./docs/design/CleanArchitecture.png)

- **Client:** Frontend component.
- **Server:** Backend server: The entry point for API calls.
- **Application Layer:** Contains application services.
- **Domain Layer:** Holds the core business logic and domain models.
- **Infrastructure Layer:** Interfaces for external dependencies and services.
- **Persistence Layer:** Manages data access.

## Components
### Client
The client application is developed using **Angular**, a robust front-end framework that allows for the creation of dynamic, single-page applications. This component serves as the user interface for interacting with the backend services and is designed to provide a seamless and responsive user experience. The website incorporates Kendo UI compoennts to enhance the visual appeal and functionality of the application. 

#### Key Components:
- **Angular Components:** UI components for various views (e.g., dashboard, forms, lists).
- **Services:** HTTP services for making API calls to the server.
- **State Management:** Management of application state using libraries like NgRx or services.
- **Routing:** Configuration of client-side routing for navigation between different views.
- **Styling:** Integration of styles and themes for a cohesive UI/UX, possibly using CSS frameworks or libraries.
- **Form Validation:** Implementation of reactive forms with validation logic.

### Server
The server component is built using **ASP.NET**, a powerful framework for developing web applications and APIs. This component acts as the backbone of the application, handling incoming requests, processing business logic, and interacting with the database layer.

ASP.NET provides robust features for routing, model binding, and dependency injection, enabling the development of a scalable and maintainable architecture. The server exposes RESTful APIs that the client application can consume, facilitating seamless communication between the front end and back end. 

With ASP.NET’s built-in security features and middleware capabilities, the server is designed to ensure secure and efficient data handling, setting a solid foundation for future enhancements and integrations.

#### Key Components:
- **API Controllers:** RESTful controllers for handling incoming requests and returning responses.
- **Middleware:** Custom middleware for logging, error handling, and authentication.
- **Dependency Injection:** Configuration of dependency injection for managing service lifetimes and dependencies.
- **Business Logic:** Service classes that encapsulate business rules and coordinate data processing.
- **Data Transfer Objects (DTOs):** Use of DTOs for shaping data exchanged between the client and server.

### Application
The Application layer serves as the intermediary between the presentation layer and the domain layer, encapsulating the use cases and application logic of the system. This layer is responsible for coordinating the flow of data between the user interface and the underlying domain models, ensuring that business rules are adhered to.

By employing patterns such as Command and Query Responsibility Segregation (CQRS), the application layer efficiently handles requests for data retrieval and manipulation. It orchestrates the interaction with the domain services, managing transactions and integrating with the infrastructure to facilitate operations such as sending notifications or processing user input. This separation of concerns promotes cleaner code and enhances maintainability.

#### Key Components:
- **Use Cases:** Definition of application-specific use cases for handling commands and queries.
- **Command Handlers:** Classes that process commands and execute the necessary business logic.
- **Query Handlers:** Classes that execute queries to retrieve data and prepare it for the client.
- **Validation Logic:** Implementation of validation rules for commands before processing.
- **Transaction Management:** Management of database transactions to ensure data consistency.

### Domain
The Domain layer is the core of the application, housing the business logic and domain models that represent the fundamental concepts and rules of the system. This layer is designed to be independent of external frameworks, ensuring that it remains focused on the business logic without being influenced by technological choices.

Domain models encapsulate the essential data and behavior relevant to the business, allowing for a clear representation of entities and their relationships. By employing domain-driven design principles, this layer enables a rich understanding of the problem space, fostering a more intuitive and coherent architecture that can adapt to changing business requirements.

#### Key Components:
- **Domain Models:** Definition of entities that represent the core business concepts (e.g., User, Campaign).
- **Value Objects:** Creation of value objects for representing attributes that have no identity (e.g., Email, Address).
- **Domain Services:** Implementation of services that contain business logic not belonging to any single entity.
- **Aggregate Roots:** Definition of aggregate roots to enforce consistency boundaries within the domain.

### Infrastructure
The Infrastructure layer serves as the technical foundation of the application, providing implementations for external dependencies and services that the application and domain layers rely on. This includes components such as data access, logging, caching, and external service integrations (e.g., email services, payment gateways).

By abstracting these technical details from the core business logic, the infrastructure layer promotes loose coupling and allows for easier testing and maintenance. It also enables the application to interact with various external systems while maintaining a consistent interface for the domain and application layers.

#### Key Components:
- **Data Access Layer:** Implementation of repositories for interacting with the database using Entity Framework Core.
- **External Service Integrations:** Interfaces and implementations for external services (e.g., email, payment processing).
- **Logging:** Setup of logging for tracking application behavior and errors.
- **Caching:** Implementation of caching strategies for improving read performance.
- **Configuration Management:** Handling application settings and environment-specific configurations.

### Persistence
The Persistence layer is responsible for managing data storage and retrieval, typically interacting with databases. This layer utilizes Entity Framework Core to abstract the complexities of database operations, enabling a clean and intuitive interface for data access.

Through this layer, the application can perform CRUD (Create, Read, Update, Delete) operations on domain models, ensuring that data integrity and relationships are maintained. The persistence layer is designed to facilitate seamless interactions with the database while allowing for future modifications, such as changing the underlying database technology or optimizing data access patterns.

#### Key Components:
- **Database Context:** Configuration of the Entity Framework Core DbContext for managing database connections.
- **Migrations:** Setup of database migrations for evolving the database schema over time.
- **Seed Data:** Implementation of seed data to populate the database with initial values.
- **Query Optimizations:** Writing optimized queries for efficient data retrieval.


## Installation and Setup
This section outlines the steps necessary to set up and run the system in both local development and production environments. The setup process includes installation prerequisites, repository cloning instructions, and application launch procedures specific to each environment.
### Prerequisites
#### Local Development Environment
   - Docker
#### Production Environment
   - Docker
   - Proxy Configuration: Ensure that traffic is routed from `https://cs499section3.ok.ubc.ca:80/charity/group6/app/` to `http://localhost:3006/charity/group6/app/`

### Cloning the Repository
The application source code is hosted on GitHub and can be cloned using either HTTPS or SSH:
HTTPS:
```
git clone https://github.com/COSC-499-W2024/capstone-project-team-6-003.git
```
SSH:
```
git clone git@github.com:COSC-499-W2024/capstone-project-team-6-003.git
```

### Launching the Application
#### Local Development
To start the application in the local environment, run the following command:
```docker compose up --build frontend```
#### Production Environment
To deploy the application in the production environment, use the following command:
```docker compose up --build frontend-prod```
### Running Tests
This section describes the procedures for executing both frontend and backend tests to ensure the correctness and stability of the application.
#### Frontend Tests
Frontend tests are written using the Angular testing framework and can be executed via the Angular CLI.
Steps to Run Frontend Tests:
- Open a terminal.
- Navigate to the frontend project directory:
 `cd app/Src/KelownaSoftware.Client`
- Execute the test suite using the Angular CLI:
`ng test`

This will compile and run the test suite in a browser-based testing environment, displaying the results in real time.

#### Backend Tests
Backend tests must be executed using an integrated development environment (IDE) that supports .NET test execution, such as Visual Studio or JetBrains Rider.

Steps to Run Backend Tests:
- Open the solution in Visual Studio or Rider.
- Locate the test project within the solution explorer.
- Right-click the test project or individual test classes/methods.
- Select Run Tests or use the IDE’s test runner interface to execute all or selected tests.

Test results, including pass/fail status and any relevant output, will be displayed in the IDE's test results panel.


### Usage
#### API Documentation
See [API Docs](./docs/design/API/API_Documentation.md)

## Technologies Used
- .NET, SQL Server, Entity Framework Core, Docker, Angular, Kendo UI Components, xUnit for testing.
- Generative AI was used in sections of workflow to help with testing and debugging

## Features

### Core Features
| Feature | What it does |
|---------|--------------|
| **Create Account** | Vendors register with email + password and are routed to their personal dashboard.<br/>*Demo creds*: `2@2.com / Testing123!`, `vm@vm.com / Testing123!` |
| **Create Charity** | Search 85 k + CRA charities, add nicknames, and manage your own list (Vendor-Manager role required). |
| **Create Campaign** | Wizard-style flow:<br/>1. **Basic Info** – name, description, goal, sign-up value<br/>2. **Fields** – choose required/custom attendee fields & “refer-a-friend” bonus<br/>3. **Eligible Charities** – pick from your charity list<br/>4. **Review** – Activate / deactivate anytime |
| **Campaign Dashboard** | Real-time graphs (sign-ups over time & by charity), KPI cards, CSV export, live refresh. |

### Attendee Experience
| Step | Details |
|------|---------|
| **Access Page** | Opens in a new window from the vendor dashboard. |
| **Dashboard View** | Goal progress, charity info, shareable QR code. |
| **Fish Gamification** | Pick a fish to drop in the tank—latest fish gets a crown ✨ (local-only bug on prod). |
| **Sign-up Flow** | Choose charity → fill required fields → confetti + email-confirm toast → add fish. |

### Organizations
| Feature | What it does |
|---------|--------------|
| **Create / Join** | Generate an org code and share it with teammates. |
| **Org Dashboard** | Leaderboard of members (crown for top donor), aggregate stats for campaigns, sign-ups & donations. |
| **Role-Based Restrictions** | Org leader controls colours/logo & charity list—members inherit settings. |

### Profile & Personalization
* **Account Info** – view roles & permissions  
* **Brand Colours** – set primary / secondary / tertiary (auto-propagates to org)  
* **Logo Upload** – displays across dashboards & attendee pages  
* **Achievements** – badges, toast notifications, level-up progress bar  

### Bonus Features
| Feature | What it does |
|---------|--------------|
| **Admin Page** | `admin@admin.com / Testing123!` – edit users, ban/unban (soft-ban, no hard deletes). |
| **Translations** | One-click English / French via *ngx-translate*. |
| **Leaderboard** | Global vs. org-only charts (filter by sign-ups or donations). |

