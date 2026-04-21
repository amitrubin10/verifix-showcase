# Verifix — Building Maintenance Management System

<p align="center">
  <img src="screenshots/logo.png" width="200" alt="Verifix" />
</p>

**Full-stack building maintenance management platform — breakdown calls, preventive maintenance, asset tracking, supplier management, SLA monitoring, and multi-building support**

Verifix replaces manual maintenance management with a structured, real-time system. Built for facility managers handling multiple buildings, contractors, and compliance requirements — from opening a breakdown call to tracking SLA deadlines and generating PDF reports.

> Built for and deployed at **Israel Ports Company** — managing 5 buildings including the headquarters at Menachem Begin 74, Tel Aviv.

---

## Live System

🔗 Deployed on Railway (production environment)

---

## Screenshots

<p align="center">
  <img src="screenshots/dashboard.png" width="700" alt="Main dashboard — breakdown calls and preventive maintenance overview" />
</p>

<p align="center">
  <img src="screenshots/health.png" width="700" alt="Building health meter and performance charts" />
</p>

<p align="center">
  <img src="screenshots/breakdown.png" width="700" alt="Breakdown calls management" />
</p>

<p align="center">
  <img src="screenshots/preventive.png" width="700" alt="Preventive maintenance by system" />
</p>

<p align="center">
  <img src="screenshots/assets.png" width="700" alt="Asset book" />
</p>

<p align="center">
  <img src="screenshots/suppliers.png" width="700" alt="Supplier book" />
</p>

<p align="center">
  <img src="screenshots/budget.png" width="700" alt="Annual budget tracking" />
</p>

<p align="center">
  <img src="screenshots/buildings.png" width="700" alt="Multi-building management" />
</p>

<p align="center">
  <img src="screenshots/sla.png" width="700" alt="SLA targets configuration" />
</p>

<p align="center">
  <img src="screenshots/settings.png" width="700" alt="System settings" />
</p>

---

## Features

### Breakdown Call Management
- Open breakdown calls from any device, including a public form requiring no login
- Track status per call: new, open, in progress, resolved
- Filter by building, status, and source
- WhatsApp and email notifications on new calls and SLA breaches
- SLA tracking with breach alerts

### Preventive Maintenance
- Define maintenance tasks per system type (HVAC, elevators, generators, chillers, UPS, fire systems, and more)
- Track status: pending, completed, delayed, cancelled
- 10 system types, 23+ tasks managed simultaneously
- Per-system completion percentages and progress tracking

### Building Health Meter
- Composite score (0–100) reflecting overall building condition
- Breakdown by category: preventive execution rate, open urgent calls, SLA compliance
- Visual performance charts per system

### Asset Book
- Full inventory of physical assets per building and floor
- System types: generators, defibrillators, VRF HVAC, UPS, first aid kits, chillers
- Per-asset history and document upload (contract, certificate)
- Active/inactive status management

### Supplier Book
- Supplier directory with contact details, domain, and SLA commitments
- Per-supplier notes (e.g. "Agreement for 4 annual chiller inspections only")
- Document upload per supplier
- Linked to system types for quick lookup

### SLA Management
- Define response time commitments per category and building
- Categories: furniture, electrical panels, HVAC, plumbing, locks, general
- Contractor assignment per category
- Visual SLA compliance dashboard

### Annual Budget
- Budget allocation per category and building
- Real-time utilization tracking with remaining balance
- Categories: gardening, safety, fire systems, pest control, mappings, cleaning, chillers, and more

### Reports
- Preventive maintenance report with filters: status, frequency, system type, building, date range
- Breakdown call report with SLA compliance analysis
- Open in new tab for print/PDF export

### Multi-Building Support
- Manage up to 5+ buildings from a single account
- Per-building data isolation and navigation
- Buildings: headquarters, offices, port terminals, retiree centers

### System Settings
- Company name and branding
- Public form URL for tenant/employee call submissions (no login required)
- WhatsApp number and email for alert routing
- User management with role-based access
- SQL backup and restore (full data export, recommended weekly)

### Mapping Management
- Email and phone routing rules per building
- Maps incoming messages/calls to the correct building automatically

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Next.js 14, React, Tailwind CSS |
| Backend | Next.js API Routes, Node.js |
| Database | PostgreSQL (Railway managed) |
| ORM | Prisma |
| Auth | JWT, middleware-based route protection |
| Deployment | Railway (continuous deployment) |
| Notifications | WhatsApp API, Email |
| Language | TypeScript |

---

## Architecture

```
┌─────────────────────────────────────────────────────┐
│                    Next.js App                       │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  │
│  │   Dashboard  │  │  Breakdown  │  │  Preventive │  │
│  │   + Health  │  │    Calls    │  │ Maintenance │  │
│  └─────────────┘  └─────────────┘  └─────────────┘  │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  │
│  │   Assets    │  │  Suppliers  │  │   Budget    │  │
│  │    Book     │  │    Book     │  │  + Reports  │  │
│  └─────────────┘  └─────────────┘  └─────────────┘  │
└──────────────────────┬──────────────────────────────┘
                       │ API Routes
┌──────────────────────▼──────────────────────────────┐
│                    Prisma ORM                        │
└──────────────────────┬──────────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────────┐
│              PostgreSQL (Railway)                    │
└─────────────────────────────────────────────────────┘
```

---

## Key Design Decisions

**Public call submission form** — Tenants and employees can open breakdown calls from any device without logging in. The system routes the call to the correct building automatically via the mapping engine.

**SLA as a first-class feature** — Every breakdown call and preventive task is tracked against defined SLA commitments. Breaches trigger immediate WhatsApp and email notifications to the relevant contacts.

**Multi-building from day one** — The data model supports multiple buildings under a single account, each with independent assets, suppliers, budgets, and SLA definitions.

**SQL backup** — Full database export on demand, allowing complete restoration on any PostgreSQL instance.

---

## Status

In active production use. Deployed and managed for a major Israeli infrastructure organization.

---

## Author

**Amit Rubin**
ERP & AI Operations Lead | QA, Automation & Product at Hashavshevet (Wizsoft)

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Amit_Rubin-blue)](https://www.linkedin.com/in/amit-rubin-316b83357/)
