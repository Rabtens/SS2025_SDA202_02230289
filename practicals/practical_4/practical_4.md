# Task Management System - Architecture Overview

This document outlines the high-level architecture of the Task Management System, including its core services, entities, and interactions.

## Services

### 1. Integration Manager
- Functionality: Manages external integrations and calendar connections.
- Key Features:
  - Calendar connection: Syncs with external calendars.
  - External connection: Integrates with third-party services.
- Relationships:
  - can connect: Allows establishing connections with external systems.

---

### 2. Task Manager
- Functionality: Handles task lifecycle operations.
- Key Features:
  - Task: Core entity representing a task.
  - Creates Task: Initiates a new task.
  - Delete Task: Removes a task.
  - Reschedule Task: Updates task timing.
- Relationships:
  - gets: Receives input/triggers for task operations.

---

### 3. Notification Manager
- Functionality: Manages notifications and alerts.
- Key Features:
  - Notification: Core entity for alerts.
  - Acc Notification: Handles notification acknowledgments.
- Relationships:
  - connection: Links to other services (e.g., Task Manager).
  - gets: Receives notification requests.
  - Connects: Establishes communication channels.
  - Can: Supports conditional notification delivery.

---

### 4. User Manager
- Functionality: Administers user accounts and access.
- Key Features:
  - System Admin: Manages administrative privileges.
  - Registered users: Tracks user registrations.
- Relationships:
  - gets: Receives user data or requests.
