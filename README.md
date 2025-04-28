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

| Layer / Component | Tech Stack | Responsibility | Key Elements |
|-------------------|-----------|----------------|--------------|
| **Client** | *Angular&nbsp;+ Kendo UI* | Single-page web UI for vendors & attendees | • Angular components & routing<br/>• HTTP services<br/>• State management (NgRx / services)<br/>• Reactive forms & validation |
| **Server** | *ASP.NET Core* | REST API, auth, business logic | • API controllers<br/>• Middleware (logging, auth)<br/>• Dependency injection<br/>• DTOs & service layer |
| **Application** | *.NET (CQRS)* | Coordinates use-cases between UI & domain | • Command / Query handlers<br/>• Validation rules<br/>• Transaction management |
| **Domain** | *Plain C#* | Core business rules—framework-agnostic | • Entities (User, Campaign, …)<br/>• Value objects<br/>• Domain services<br/>• Aggregate roots |
| **Infrastructure** | *EF Core, external SDKs* | Implements technical concerns | • Repositories<br/>• External integrations (email, payments)<br/>• Logging & caching<br/>• Config management |
| **Persistence** | *SQL Server + EF Core* | Data storage & retrieval | • DbContext<br/>• Migrations & seed data<br/>• Query optimisation |


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

