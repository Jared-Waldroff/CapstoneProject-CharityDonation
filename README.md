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

Core Features:
Create Account (Jared 100%):
A vendor can create a new account given an email as their unique identifier and password. They can login and be routed to their campaign dashboard. Some basic accounts that can be used to test different features are 2@2.com password: Testing123! and vm@vm.com password: Testing123!

Create Charity (Aidan M: 100%):
A vendor must create their own charity on the charity page before creating a campaign. A base charity can be searched for that is taken from a list of 85,000 charities from the Canadian government which show their name and location. Vendors can add their own nickname to the charity to shorten length and better communicate their cause. Vendors can create as many as they would like and their information can be viewed on the charities tab. If you are a vendor under manager role such as the 2@2.com account is to the vm@vm.vom , you will not be able to pick new charities to add to campaigns. This ability is reserved for the Vendor Manager.
Create Campaign: 
Basic Campaign Information (Aidan E: 60%, Aidan M: 40%):
Campaigns can be created by vendors by choosing a name, description, donation goal, and sign up value. The sign up value is how much money will be donated to the user upon each attendee signup. Users can later edit this part of their campaign from the campaign specific dashboard.

Choosing Fields (Aidan E: 100%):
The next page allows the vendor to customize what fields they would like to receive from a user. The email is always required, but the vendor can decide from preset types of fields such as name, age, location, job, and can decide whether each field is required before attendee submission. We acknowledged that we did not provide an exhaustive list of potential fields, so we allow the user to specify custom fields with whatever they would like from the vendor. There is also an option for the vendor to allow attendees to refer a friend. If selected, they can provide a “bonus” donation amount if an attendee inputs an email which has already signed up.

Selecting Eligible Charities (Aidan M: 40%, Aidan E: 60%):
After selecting the fields, vendors are prompted to choose which charities attendees can donate to via their campaign. The list of charities to choose comes from the charities created by the vendor, and any charities created by their organization if they’ve joined one.

Viewing Created Campaigns (Aidan M: 80%, Jared 20%):
The campaign will now be created and added to their campaign dashboard. Vendors can activate and deactivate their campaign as needed to prevent attendees with the link to sign up while not attending a convention.




Campaign Dashboard: 
After a campaign is created, vendors can click view to see the campaigns dashboard, which displays campaign information, graphs regarding signups, general statistics about the campaign, and view/download csv data of user information collected.
Campaign Dashboard Graphs (Aidan E 100%):
There are graphs on the campaign dashboard which show the number of signups over time and the number of signups for each charity. The time series graph can be customized from minute, hours, day to see where most of the campaigns signups were concentrated. When there are multiple charities to sign up for per campaign, the charity graph compares which charities attendees are choosing to donate to the most.

Campaign Dashboard Stats (Aidan E: 60%, Aidan M: 40%):
The stats are displayed in kendo cards and show the campaigns signup value, total signups, total amount donated, and the donation goal. 

Download CSV Data (Aidan M: 100%):
All the information collected by the campaign can be viewed in a table on the campaign dashboard. A button is included to download the csv for whatever the vendor needs the information for. Vendors can click refresh data to get any live updates without needing to refresh an entire page. A column is included describing whether the attendee verified their email after signing up.
Attendee Signup:
Accessing Page (Aidan E: 100%):
The attendee signup page can be accessed via the campaign dashboard. The page pops up in a new window to prevent attendees from navigating to pages intended for the vendor.

Dashboard (Aidan M: 70%, Jared: 25%, Aidan E: 5%):
The right side of the attendee page displays all basic information of the campaign an attendee is viewing. There is a progress bar showing how far along the campaign is to their goal, and information about all the charities which can be selected. A QR code is included to allow users to access the site on their phones if they want to keep walking while signing up.

Fish Gamification (Aidan E: 25%, Aidan M: 75%):
You’ll see on the left hand side a fish tank . In order to allow users to leave a lasting impression on the campaign, attendees can select a fish to add to the fishtank. The most recent fish to be added will have a crown for users to immediately identify their addition. This has a bug where the fish won’t show up on the deployed server but it will show up when you run it locally.

Inputting Information (Aidan E: 75%, Aidan M: 25%):
After an attendee clicks sign up, they select which charity they’d like to donate to, and fill out all the information specified by the vendor. They cannot submit their information until all required fields are filled in, and the attendee agrees for their information to be used by the vendor. If registration is successful, confetti flies, a toast notification to check their email for confirmation is displayed, and the attendee can select a fish to add to the tank.

Organizations:
Creating/Joining Organization (Jarred 100%):
Via the organization tab, a vendor can create an organization with a name of their choice. Once made, vendors can copy the organization code and send it to other representatives in their organization to join. Simply click join and paste the organization code in to be allowed in. 

Organization Dashboard (Aidan E: 75%, Aidan M: 25%):
The left side of the organization dashboard shows the owner and a list of all the members and their respective signups and donations. The member with the most donations will have a crown displayed next to their name. The right side of the organization dashboard shows aggregate statistics of campaigns, members, signups, and donations that the entire organization has done.

Restricting Vendor Members (Jared 100%):
Members in the organization can see the current settings set by the organization leader in the dashboard. The colors and logo will automatically populate on their dashboards and campaigns. Members are prevented from being able to change these while in the organization. Other charities created by the organization leader will now be available to their members, and the members will be restricted from creating more. 
Profile Page:
Viewing Account Information (Jared 75%, Aidan M: 25%):
The profile page can be reached by clicking the profile tab in the navbar, or clicking the user’s email in the top right of the header. Vendors can check basic information about their profile, and see what permissions they have (Vendor, Vendor Manager or Vendor Under Manager).

Changing Colors (Jared 50%, Aidan M: 50%):
Vendors can also change the primary, secondary, and tertiary colors of the platform to reflect the company they are representing. These colors will be displayed in all the dashboards and the attendee signup page. If you are the leader of an organization, these colors will populate across all the members as well. Note: Occasionally, switching accounts will cause the site to populate colors from the previous account. This is due to a small issue with our current user service, and refreshing the page fixes the issue.

Changing Logo (Jared 50%, Aidan M: 50%):
Vendors can also upload their company logo to be displayed in their header, and on the attendee sign up page. Just like the colors, they will populate across members in the organization. Note: The first time a vendor account is created, viewing the profile page will show a warning toast “vendor settings cannot be found”. This is because a vendor setting in the database is not created upon account registry but when they view a profile page. This will not persist multiple times

Achievements (Jared 100%):
Vendors are able to receive achievements for receiving different accolades from creating campaigns, collecting signups, and donation milestones. All earned and unearned achievements (and their respective badges) can be viewed from the profile page. A toast will be shown when a new achievement is earned.


Achievement Progress (Jared 100%):
The profile page includes an interactive leveling system. After a certain amount of achievements are received, a vendor can “level up” to the next stage.
Bonus Features:
Admin Page (Jared 20%, Aidan M: 80%): 
An admin account is created with credentials admin@admin.com Testing123! (this can and should be configured of course). An Admin can do all the functions of a normal vendor, but also has access to the admin page. The admin can edit user information and ban/unban vendors. If a vendor is banned, they can no longer login to the platform and will be notified when attempting to. The unbanning feature is important as we do not want to irreversibly delete user data.

Translations (Jared 10%, Aidan E: 55%, Aidan M: 35%):
At the bottom of the navbar, vendors can switch between English and French languages for the platform. All hard-coded text across the website will be swapped using the ngx translate library. 

Leaderboard (Aidan E: 80%, Aidan M: 20%):
The leaderboard page shows the rankings of top vendors across the entire platform in a bar graph. It can be filtered to show sign ups or donations, and a button is included to switch between seeing members of the whole platform, or just those in your organization.
