# VendasBoost PRO

> SaaS automation platform for social media marketing

![Status](https://img.shields.io/badge/Status-Production-brightgreen)
![Version](https://img.shields.io/badge/Version-10.0-blue)

---

## Overview

VendasBoost PRO is a complete SaaS platform that automates social media marketing workflows. It allows businesses to manage posting across multiple groups, schedule content, create marketplace listings, and track performance — all from a single dashboard.

The system supports multiple companies with employee management, subscription plans with usage limits, and a full admin panel for platform management.

---

## Key Features

**Automation Engine**
- Post to multiple groups simultaneously
- Create marketplace listings
- Single scheduling (date/time) and recurring weekly schedules
- Discover and join relevant groups automatically
- Multi-account support

**SaaS Platform**
- Multi-tenant architecture (companies and employees)
- Subscription plans with tiered usage limits
- Payment processing via MercadoPago (webhooks)
- Usage tracking and token-based metering

**Admin Dashboard**
- Platform-wide metrics and KPIs
- Company and employee management
- Audit logging
- Extension version management and distribution

**Security**
- JWT authentication with middleware
- Rate limiting per route
- Input validation and sanitization
- Code obfuscation for client distribution
- XSS protection and cookie-only auth

---

## Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    Chrome Extension                       │
│              (Content Scripts + Popup UI)                 │
└──────────────────────┬──────────────────────────────────┘
                       │ REST API
┌──────────────────────▼──────────────────────────────────┐
│                   Backend (Node.js)                       │
│  ┌─────────┐  ┌──────────┐  ┌────────────┐              │
│  │  Auth    │  │  Routes  │  │  Services  │              │
│  │Middleware│  │  (REST)  │  │  (Email,   │              │
│  └─────────┘  └──────────┘  │   Logger)  │              │
│                              └────────────┘              │
│  ┌──────────────────────────────────────────┐            │
│  │         Models (Sequelize ORM)            │            │
│  │  User | Company | Usage | Webhook | ...   │            │
│  └──────────────────────────────────────────┘            │
└──────────────────────┬──────────────────────────────────┘
                       │
          ┌────────────▼────────────┐
          │     Database (SQL)      │
          └─────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│                    Admin Panel                            │
│            (Static HTML + Vanilla JS)                    │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│               CI/CD (GitHub Actions)                     │
│           Automated testing and deployment                │
└─────────────────────────────────────────────────────────┘
```

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| **Runtime** | Node.js, Express |
| **Database** | SQL (Sequelize ORM) |
| **Auth** | JWT, cookie-based sessions |
| **Payments** | MercadoPago SDK (subscriptions + webhooks) |
| **Client** | Chrome Extension (Manifest V3) |
| **Admin** | Static HTML + Vanilla JavaScript |
| **Testing** | Jest (unit + integration, 14+ test suites) |
| **CI/CD** | GitHub Actions (CI pipeline + CD deployment) |
| **Process** | PM2 (production process manager) |
| **Security** | Rate limiter, validators, code obfuscation |

---

## Testing

The project includes comprehensive tests covering:

- **Unit tests** — Authentication middleware, plan limits, input validators
- **Integration tests** — All REST routes (auth, admin, companies, plans, subscriptions, usage, webhooks, extension, health)
- **Security tests** — Webhook signature verification, route protection

---

## Project Stats

| Metric | Value |
|--------|-------|
| Total files | 169 |
| Test suites | 14+ |
| Version | 10.0 |
| Development period | Dec 2025 — Feb 2026 |

---

*This is a showcase repository. The source code is in a private repository.*
