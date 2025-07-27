# Architecture Documentation

## Overview

Blossomss is designed as a full-stack web application with a clear separation of concerns between the frontend (client), backend (server), and database. This modular architecture allows for independent development, deployment, and scaling of each layer.

```mermaid
graph LR
    Client(Client) -->|API Requests| Server(Server)
    Server -->|Database Queries| Database(Database)
    Server -->|SMTP| EmailService(Email Service - Firebase)

    subgraph Frontend
        Client
        React
        Vite
        TypeScript
        Tailwind CSS
        Shadcn/ui
    end

    subgraph Backend
        Server
        Bun
        TypeScript
        Drizzle ORM
        JWT Authentication
    end

    subgraph Database
        Database
        PostgreSQL (Supabase)
    end

    style Client fill:#f9f,stroke:#333,stroke-width:2px
    style Server fill:#ccf,stroke:#333,stroke-width:2px
    style Database fill:#ffc,stroke:#333,stroke-width:2px
    style EmailService fill:#eee,stroke:#333,stroke-width:2px
```

## Layer Details

### 1. Client (Frontend)

- **Technology:** React, TypeScript, Vite, Tailwind CSS, Shadcn/ui
- **Location:** `client/` directory
- **Responsibility:**
    - User interface and user experience.
    - Handling user interactions and displaying data.
    - Making API requests to the server to fetch and manipulate data.
    - Routing and navigation using React Router DOM.
    - State management (to be decided - Zustand or TanStack Query).
    - UI components built with Shadcn/ui and styled with Tailwind CSS.
    - Section-specific scroll behavior management using custom hooks.
- **Key Modules:**
    - `src/components/`: Reusable UI components.
    - `src/pages/`:  Application pages/views.
    - `src/hooks/`:  Custom React hooks for reusable logic.
    - `src/lib/`:  Utility functions and shared logic.
    - `src/types/`: TypeScript type definitions.

- **Scroll Management:**
    - Custom scroll lock hook for section-specific scroll control
    - Section transitions with proper scroll state handling
    - Context-aware scroll behavior:
      - Locked scrolling for focused sections
      - Natural scrolling for content sections
      - Smooth transitions between states

### 2. Server (Backend)

- **Technology:** Bun, TypeScript, Drizzle ORM, JWT Authentication
- **Location:** `server/` directory
- **Responsibility:**
    - Business logic and application logic.
    - RESTful API endpoints for client communication.
    - Data validation and processing.
    - Authentication and authorization using JWT.
    - Database interactions using Drizzle ORM.
    - Integration with external services (e.g., Firebase for SMTP).
- **Key Modules:**
    - `server/routes/`: API route handlers, organized by feature.
    - `server/services/`: Business logic and service functions.
    - `server/lib/`: Utility functions and shared logic.
    - `server/config/`: Configuration files (environment variables, JWT, Firebase).
    - `db/`: Database schema definition and Drizzle ORM setup.

### 3. Database

- **Technology:** PostgreSQL (Supabase)
- **Location:** Supabase managed PostgreSQL instance. Schema defined in `db/schema.ts`. Migrations in `migrations/` directory.
- **Responsibility:**
    - Persistent data storage.
    - Data retrieval and manipulation.
    - Data integrity and consistency.
- **Schema:**
    - Defined using Drizzle ORM in `db/schema.ts`.
    - Tables for users, children, events, photos, messages, documents, expenses, etc. (detailed schema to be designed).

### 4. Email Service

- **Technology:** Firebase SMTP
- **Responsibility:**
    - Sending emails, e.g., for password reset, notifications, admin alerts.
- **Integration:**
    - Server integrates with Firebase SMTP service to send emails.
    - Configuration managed through Firebase Admin SDK and environment variables.

## Data Flow

1. **User Interaction:** User interacts with the frontend client (e.g., clicks a button, submits a form).
2. **API Request:** Client sends an API request to the server (e.g., `GET /api/children`, `POST /api/events`).
3. **Server Processing:**
    - Server receives the API request and authenticates/authorizes the user (using JWT).
    - Server processes the request, performs business logic, and interacts with the database using Drizzle ORM.
4. **Database Query:** Server queries the PostgreSQL database to fetch or modify data.
5. **Data Response:** Database returns data to the server.
6. **API Response:** Server sends an API response back to the client (e.g., JSON data, success/error status).
7. **UI Update:** Client receives the API response and updates the user interface accordingly.

## Modules and Components

(Detailed breakdown of key modules and components in each layer will be added here as development progresses)

## Future Considerations

- **Real-time Functionality:**  Explore WebSockets for real-time messaging and updates.
- **Scalability and Performance:**  Implement caching, database optimizations, and load balancing as needed.
- **Testing Strategy:**  Define a comprehensive testing strategy (unit, integration, e2e).
- **Deployment Pipeline:**  Set up CI/CD pipeline for automated deployments.
