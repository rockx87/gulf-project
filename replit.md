# Aurum Emirates

## Overview

Aurum Emirates is a Dubai-based investment platform focused on Oil, Gas, and Precious Metals trading with USDT integration. The application provides a mobile-first experience with features including portfolio management, AI-powered trading, futures/perpetual trading, market data display, and a multi-level referral system.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter (lightweight alternative to React Router)
- **State Management**: TanStack React Query for server state
- **Styling**: Tailwind CSS v4 with shadcn/ui components (New York style)
- **Animations**: Framer Motion for page transitions and UI animations
- **Build Tool**: Vite with custom plugins for Replit integration

The frontend follows a page-based structure under `client/src/pages/` with shared components in `client/src/components/`. The UI emphasizes a premium, elegant aesthetic with custom CSS variables for theming (silver/platinum color scheme).

### Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript (ESM modules)
- **API Pattern**: REST endpoints under `/api/` prefix
- **Development**: Vite dev server proxied through Express in development
- **Production**: Static file serving with SPA fallback

The server handles authentication, user management, investments, transactions, and referral tracking. Routes are defined in `server/routes.ts` with storage abstraction in `server/storage.ts`.

### Database Layer
- **ORM**: Drizzle ORM with PostgreSQL dialect
- **Schema Location**: `shared/schema.ts` (shared between client and server)
- **Validation**: Zod schemas generated from Drizzle schemas via drizzle-zod
- **Migrations**: Managed via `drizzle-kit push`

Key database tables:
- `users` - User accounts with wallet balances, referral codes
- `investments` - Investment records with asset types, amounts, return rates
- `transactions` - Deposit/withdrawal/payout history
- `referrals` - Multi-level referral tracking (7 levels)

### Authentication
- Password hashing with bcryptjs
- Session-based authentication planned (connect-pg-simple in dependencies)
- Simple PIN-based login UI (demo mode with hardcoded PIN "1234")

### Build System
- Custom build script (`script/build.ts`) using esbuild for server bundling
- Vite for client-side bundling
- Server dependencies are selectively bundled to reduce cold start times

## External Dependencies

### Database
- **PostgreSQL**: Required via `DATABASE_URL` environment variable
- **Session Store**: connect-pg-simple for PostgreSQL-backed sessions

### Frontend Libraries
- **UI Components**: Radix UI primitives (20+ packages for accessible components)
- **Charts**: Recharts (via shadcn/ui chart component)
- **Forms**: React Hook Form with Zod validation
- **Carousel**: Embla Carousel

### Development Tools
- **Replit Plugins**: vite-plugin-cartographer, vite-plugin-dev-banner, vite-plugin-runtime-error-modal
- **Meta Images Plugin**: Custom plugin for OpenGraph image handling

### Fonts
- Playfair Display (display/headings)
- Inter (body text)
- JetBrains Mono (monospace)

Loaded via Google Fonts CDN in `client/index.html`.