# Cloud Architecture Overview

This document provides a simple system context diagram for the monorepo: a React frontend and an Express API with an in-memory store.

## System Context Diagram

```mermaid
flowchart TD
    U[End User] --> B[React Frontend (Browser SPA)]
    B -->|HTTP/JSON| API[Express API Server]
    API --> MEM[(In-Memory Store)]

    %% Client-side local persistence (MVP)
    B --> LS[(Browser Local Storage)]

    %% Optional external integrations (none in scope)
    classDef outOfScope fill:#eee,stroke:#bbb,color:#666
    EXT[External Services]:::outOfScope
```

## Notes
- React frontend runs in the browser as a single-page application.
- Express API handles HTTP requests; current persistence is an in-memory store (no external DB).
- MVP keeps client-side data in browser Local Storage; backend remains stateless across restarts.
- No external services, notifications, or multi-user features are in scope.

---

## Sequence: Creating a TODO

```mermaid
sequenceDiagram
        participant U as End User
        participant FE as React Frontend (SPA)
        participant LS as Browser Local Storage
        participant API as Express API Server
        participant MEM as In-Memory Store

        U->>FE: Open app and submit "New Task"
        FE->>FE: Validate title (required)
        FE->>FE: Validate/sanitize dueDate (YYYY-MM-DD)
        FE->>FE: Sanitize priority (default P3)
        FE->>LS: Save task JSON
        LS-->>FE: Confirm write
        FE-->>U: Render task in list

        opt Backend-enabled mode (optional)
            FE->>API: POST /tasks (task payload)
            API->>MEM: Store task in memory
            API-->>FE: 201 Created + task
            FE-->>U: Reflect server task state
        end
```
