# Amici Events — Technical Overview

## What is Amici?

Amici is a full-stack event catering platform that connects customers with top-tier chefs. Customers submit event requests (date, venue, guests, budget, extras), and Amici matches them with chefs who provide offers. The platform handles the full lifecycle: request → offer → acceptance → payment → invoicing.

---

## Monorepo Architecture

Built with **Turborepo** using **Yarn Workspaces**. All apps and packages live in a single repository with shared configuration.

```
amici-events/
├── apps/                        # Applications
│   ├── web/                     # Main app (port 3000)
│   ├── admin/                   # Admin dashboard (port 3001)
│   ├── landing/                 # Marketing site + event request flow (port 3002)
│   ├── chef/                    # Chef-facing app (port 3003)
│   └── planner-api/             # Backend API service
│
├── packages/                    # Shared libraries
│   ├── ui/                      # Component library (84 components)
│   ├── core/                    # Firebase business logic
│   ├── core-supabase/           # Supabase logic, migrations, Edge Functions
│   ├── notifications/           # Email templates (React Email)
│   ├── config-eslint/           # Shared ESLint config
│   ├── config-tailwind/         # Shared Tailwind config + design tokens
│   └── config-typescript/       # Shared TypeScript config
│
├── turbo.json                   # Build pipeline
├── firebase.json                # Firestore rules & indexes
└── .github/workflows/           # CI/CD (staging + production)
```

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| **Runtime** | Node.js 20+, Deno (Edge Functions) |
| **Package Manager** | Yarn 1.22.19 (classic) |
| **Build System** | Turborepo 2.7.5 |
| **Framework** | Next.js 16 (App Router) |
| **Language** | TypeScript 5.9 |
| **UI Library** | React 19 |
| **Styling** | Tailwind CSS 4.1 |
| **Component Primitives** | Radix UI (13+ primitives) |
| **Forms** | react-hook-form + Zod validation |
| **State Management** | Zustand (landing app) |
| **Animation** | Framer Motion |
| **Database (NoSQL)** | Firebase Firestore |
| **Database (SQL)** | Supabase (PostgreSQL) |
| **Auth** | Firebase Auth + Supabase Auth |
| **Payments** | Mollie |
| **Email** | Resend + React Email templates |
| **Analytics** | PostHog + Hotjar |
| **Maps** | Google Maps / Places API |
| **PDF** | @react-pdf/renderer |
| **Hosting** | Vercel |
| **CI/CD** | GitHub Actions |

---

## Applications

### Landing (`apps/landing` — port 3002)
The public-facing marketing site and the main event request flow. This is where customers:
- Browse the homepage with chef/event imagery
- Fill out the multi-step event request form (date → venue → details → extras → submit)
- Sign up / log in
- View their dashboard with event status, offers, and invoices

Uses **MDX** for content pages (terms, privacy, about).

### Admin (`apps/admin` — port 3001)
Internal dashboard for the Amici team to:
- Review incoming event requests
- Manage chef/seller profiles
- Send offer requests to chefs
- Track payments and invoices
- Monitor platform activity

### Web (`apps/web` — port 3000)
Main web application for authenticated users.

### Chef (`apps/chef` — port 3003)
Chef-facing application where sellers can view and respond to event requests, manage their profiles, and submit offers.

---

## Dual Database Architecture

The project uses **both Firebase and Supabase** in parallel:

```
┌─────────────┐     ┌──────────────────┐
│  Firebase    │     │  Supabase        │
│  Firestore   │◄───►│  PostgreSQL      │
│             │     │                  │
│  - Auth     │     │  - RLS Policies  │
│  - Realtime │     │  - Migrations    │
│  - Legacy   │     │  - Edge Funcs    │
│    data     │     │  - Type-safe     │
└─────────────┘     └──────────────────┘
        │                    │
        └────── Sync ────────┘
         (firebase-mappers/)
```

### Firebase (`@amici/core`)
- **Authentication**: Email/password, Google OAuth, phone verification
- **Firestore**: Real-time data, legacy collections
- **Cloud Functions**: Server-side operations (europe-west1)
- Client SDK + Admin SDK for server operations

### Supabase (`@amici/core-supabase`)
- **PostgreSQL**: Relational data — applications, invoices, profiles, sellers, offers
- **Row Level Security (RLS)**: Every table has granular policies per operation and role
- **39+ Migrations**: Schema versioned in `supabase/migrations/`
- **17 Edge Functions** (Deno): Webhooks, email triggers, payment processing
- **Type Generation**: Auto-generated TypeScript types from the database schema

### Key Supabase Tables
- `applications` — Event requests from customers
- `application_offers` — Chef offers on applications
- `application_addons` — Add-ons attached to requests
- `sellers` — Chef/vendor profiles
- `profiles` — User profiles (extended auth)
- `invoices` / `invoice_payment_terms` — Billing
- `companies` — Organization data
- `chat_messages` — Real-time messaging

---

## Shared UI Library (`@amici/ui`)

**84 components** built on Radix UI + Tailwind CSS with a custom design token system.

### Component Categories
- **Forms**: Input, Select, Checkbox, RadioGroup, DatePicker, FlexibleDatePicker, AddressInput, PhoneInput, MaskedInput, MultiSelect
- **Feedback**: Dialog, AlertDialog, Toast, Popover, Tooltip
- **Layout**: Card, Tabs, Accordion, Carousel, ScrollArea, Collapsible, Separator
- **Navigation**: NavigationMenu, DropdownMenu, Menubar, Command Palette
- **Data**: Table (TanStack), Combobox, Badge, Avatar
- **Specialized**: ChefCard, CalendarCarousel, InputField/InputGroup, PDF utilities

### Design Token System
CSS custom properties for colors, spacing, and semantic tokens:
- Light/dark mode support
- Primary, secondary, accent, destructive, muted palettes
- Consistent border radius, input, and card tokens

### Import Pattern
```typescript
import { Button } from "@amici/ui/button"
import { cn, InputField, InputGroup } from "@amici/ui"
import { Input } from "@amici/ui/input"
```

---

## Key Integrations

### Payments (Mollie)
- Payment processing via Mollie API
- Webhook Edge Function (`mollie-webhooks`) handles payment notifications
- Invoice generation after payment confirmation
- Email notifications on payment events

### Email (Resend + React Email)
- **Resend** sends transactional emails
- **React Email** renders component-based templates to HTML
- **Edge Functions** trigger emails on database events:
  - `send-request-confirmation` — After a customer submits a request
  - `send-offer-received` — When a chef submits an offer
  - `send-offer-accepted` / `send-offer-rejected` — Offer status changes
  - `send-invoice` / `send-invoice-paid` — Billing events
  - `auth-hook-emails` — Auth events (signup, password reset)

### Analytics
- **PostHog**: Product analytics, event tracking, user identification
- **Hotjar**: Session recordings, heatmaps

### Google Maps / Places
- Address autocomplete in the event request flow
- Static map images on event detail pages
- Place details lookup

---

## Authentication Flow

```
User signs up/in
       │
       ▼
  Firebase Auth
  (email, Google, phone)
       │
       ▼
  Server creates session cookie
       │
       ▼
  Supabase RLS checks auth.uid()
  for data access policies
```

- Firebase handles the actual authentication (sign-up, sign-in, OAuth)
- Server Actions create Firebase custom claims for role-based access
- Supabase RLS policies use `auth.uid()` to scope data access
- Cookies manage session state across requests

---

## Event Request Flow (Core Business Logic)

```
1. Customer fills multi-step form:
   Date → Venue → Details → Extras → Contact Info

2. Application created in Supabase via Server Action
   (submitApplicationForm → admin client → bypasses RLS)

3. Edge Functions trigger:
   - Confirmation email to customer
   - Notification to admin

4. Admin reviews & sends offer requests to chefs

5. Chefs submit offers

6. Customer reviews & accepts an offer

7. Payment processed via Mollie

8. Invoice generated, emails sent
```

---

## Development Workflow

### Running Locally
```bash
yarn dev                          # All apps in parallel
yarn dev --filter=landing         # Single app
yarn supabase:start               # Local Supabase instance
```

### Building & Quality
```bash
yarn build                        # Build all packages & apps
yarn lint                         # ESLint across monorepo
yarn type-check                   # TypeScript checking
yarn test                         # Vitest test runner
yarn format                       # Prettier formatting
```

### Supabase Operations
```bash
yarn supabase:start               # Start local instance
yarn supabase:db:gen-types:local  # Generate types from local DB
yarn supabase:db:apply-migrations # Apply migrations locally
```

---

## CI/CD Pipeline

### GitHub Actions Workflows

**On PR** (`ci.yaml`):
- Validates Supabase type generation matches schema
- Ensures no uncommitted type changes

**On push to `dev`** (`staging.yaml`):
- Deploys migrations to Supabase staging
- Deploys all Edge Functions

**On push to `main`** (`prod.yaml`):
- Deploys migrations to Supabase production
- Deploys all Edge Functions
- Vercel auto-deploys apps

```
PR → CI checks → Merge to dev → Staging deploy → Merge to main → Production deploy
```

---

## Environment Structure

| Environment | Branch | Supabase | Vercel |
|------------|--------|----------|--------|
| Local | any | Local instance | localhost |
| Staging | `dev` | Staging project | Preview |
| Production | `main` | Production project | Production |

### Key Environment Variables
- `NEXT_PUBLIC_FIREBASE_*` — Firebase client config
- `NEXT_PUBLIC_SUPABASE_URL` / `NEXT_PUBLIC_SUPABASE_PUBLISHABLE` — Supabase client
- `SUPABASE_SERVICE_ROLE_KEY` — Admin access (server-side only)
- `MOLLIE_API_KEY` / `MOLLIE_PROFILE_ID` — Payment processing
- `GOOGLE_CLOUD_API_KEY` — Maps & Places
- `COOKIE_SECRET_CURRENT` / `COOKIE_SECRET_PREVIOUS` — Session management
