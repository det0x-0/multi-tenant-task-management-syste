# Zenith: Multi-Tenant Task Management System

Zenith is a premium, enterprise-ready task management platform designed for multi-tenant scalability. It provides strict data isolation, hierarchical Role-Based Access Control (RBAC), and a comprehensive audit logging system, all wrapped in a modern, high-performance UI.

![Zenith Preview](https://via.placeholder.com/1200x600?text=Zenith+Dashboard)

## 🚀 Core Architectural Pillars

### 1. Multi-Tenant Architecture
Unlike simple single-tenant apps, Zenith supports multiple organizations within a single database instance.
- **Tenant Auto-Provisioning**: New organizations are automatically created during registration.
- **Organization Switcher**: Users can belong to multiple workspaces and switch contexts seamlessly via the sidebar.

### 2. Strict Data Isolation
Data security is enforced at the database level. Every core table (`projects`, `tasks`, `org_members`, `audit_log`) is scoped by `org_id`.
- **Query Scoping**: Middleware intercepts requests, verifies tenant membership, and ensures that every SQL query is strictly scoped to the active tenant.
- **Zero Leakage**: One organization can never view or modify data belonging to another, even if project IDs are known.

### 3. Hierarchical RBAC (Role-Based Access Control)
Zenith implements a robust permission system with three distinct roles:
- **Admin**: Full control over projects, members, and organizational settings.
- **Manager**: Can create/edit projects and tasks and invite members, but cannot perform destructive admin actions (like deleting projects).
- **Member**: Focuses on task execution. Access to management tools and deletion is restricted at both the UI and API levels.

### 4. Comprehensive Audit Logging
Every sensitive action (invites, role changes, project deletion) is recorded in an immutable audit trail, tracking the **Who, What, When, and Where** for enterprise compliance.

---

## 🛠 Technology Stack
- **Frontend**: React (Vite), Vanilla CSS (Custom Design System), Lucide Icons.
- **Backend**: Node.js (ESM), Express.
- **Database**: Native Node.js `sqlite` (v24+ compatible).
- **Authentication**: JWT with secure cookie storage.

---

## 🏁 Quick Start

### Prerequisites
- Node.js 24 or later (required for native `node:sqlite` support).

### Installation
1. **Clone and Install Backend**:
   ```bash
   cd backend
   npm install
   ```
2. **Clone and Install Frontend**:
   ```bash
   cd frontend
   npm install
   ```

### Running Locally
1. Start the backend:
   ```bash
   cd backend
   node src/index.js
   ```
2. Start the frontend:
   ```bash
   cd frontend
   npm run dev
   ```

---

## 🧪 Demo Credentials

To experience the RBAC features immediately, use the following pre-seeded account:

| Role | Email | Password |
| :--- | :--- | :--- |
| **Admin** | `demo@zenith.com` | `password123` |
| **Member** | `demomember@zenith.com` | `Zenith123!` |

---

## 🔒 Security & Performance
- **Zero Dependencies for DB**: Uses the native Node v24 SQLite module for zero-latency, portable data storage.
- **Glassmorphism UI**: High-end aesthetic with responsive layouts and micro-animations.
- **Middleware Protected**: Every route is guarded by double-layer security (Auth + Organization Context).
