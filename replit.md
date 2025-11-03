# AI Chatbot Agency - Admin Dashboard

## Overview

This is an MVP admin dashboard for managing multiple AI chatbots that can be embedded on client websites. The application allows a single administrator to create, configure, and manage chatbots with customizable appearance and webhook integrations. Each bot can be embedded via script or iframe, and visitor messages are forwarded to configured webhook URLs.

The system is built as a full-stack TypeScript application with a React frontend and Express backend, designed for simplicity and ease of deployment.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework**: React 18 with TypeScript using Vite as the build tool

**Routing**: Wouter for client-side routing (lightweight React Router alternative)

**State Management**: 
- React Context API (`AppContext`) for global application state
- TanStack Query (React Query) for server state management and API caching
- Local component state with React hooks

**UI Component System**:
- Shadcn/ui component library (Radix UI primitives with Tailwind CSS)
- Custom theme system using CSS variables for light/dark mode support
- Tailwind CSS for styling with "new-york" style variant
- Component aliases configured for clean imports (`@/components`, `@/lib`, etc.)

**Key Pages**:
- Login: Mock authentication page with email/password
- Dashboard: Overview with statistics and recent activity
- Bots: List view with create/edit/delete operations
- Settings: Admin profile and default configuration
- EmbedPreview: Display embed code for individual bots

**Design System**: Custom design guidelines based on modern SaaS aesthetics (Linear, Vercel, Stripe) with blue-purple gradient theme, rounded corners, and generous whitespace

### Backend Architecture

**Framework**: Express.js with TypeScript

**API Structure**: RESTful API with the following endpoints:
- `POST /api/auth/login` - Authentication
- `GET /api/bots` - Retrieve all bots
- `GET /api/bots/:id` - Retrieve single bot
- `POST /api/bots` - Create new bot
- `PUT /api/bots/:id` - Update bot
- `DELETE /api/bots/:id` - Delete bot

**Development Mode**: Vite middleware integration for HMR and development server

**Production Build**: 
- Frontend: Static assets built with Vite to `dist/public`
- Backend: Bundled with esbuild to `dist/index.js`

### Data Storage

**Primary Database**: PostgreSQL via Neon serverless
- ORM: Drizzle ORM with schema-first approach
- Schema location: `shared/schema.ts`
- Migrations: Drizzle Kit with output to `./migrations`

**Fallback Storage**: In-memory storage (`MemStorage` class) for development/demo
- Used when `DATABASE_URL` is not configured
- Includes seed data for demonstration
- Implements same `IStorage` interface as database storage

**Database Schema**:
- `users` table: Admin authentication (id, username, password)
- `bots` table: Chatbot configurations with fields for appearance (theme, dimensions, text), behavior (welcome message, suggested messages), and integrations (webhook URLs)

**Session Management**: Basic authentication without formal sessions in current implementation (to be enhanced)

### Authentication & Authorization

**Current Implementation**: 
- Simple username/password validation
- No JWT or session tokens (mock authentication)
- Single admin user model
- Client-side auth state in AppContext

**Future Considerations**: Session-based or token-based authentication should be implemented for production use

### Form Validation

**Library**: Zod for runtime type validation
- Schema definitions with `drizzle-zod` for automatic schema generation
- React Hook Form with `@hookform/resolvers` for form state management
- Type-safe validation aligned with database schema

## External Dependencies

### Database & ORM
- **Neon Serverless PostgreSQL**: Cloud-hosted PostgreSQL database
- **Drizzle ORM**: Type-safe SQL ORM with schema migrations
- **connect-pg-simple**: PostgreSQL session store (installed but not actively used)

### UI Component Libraries
- **Radix UI**: Headless component primitives (40+ components including Dialog, Dropdown, Select, etc.)
- **Shadcn/ui**: Pre-styled component system built on Radix UI
- **Tailwind CSS**: Utility-first CSS framework
- **class-variance-authority**: Type-safe variant styles
- **cmdk**: Command menu component

### Development Tools
- **Vite**: Frontend build tool and dev server
- **esbuild**: Backend bundler
- **tsx**: TypeScript execution for development
- **Replit Plugins**: Development tools for Replit environment (cartographer, dev banner, runtime error modal)

### Utility Libraries
- **date-fns**: Date formatting and manipulation
- **embla-carousel-react**: Carousel component
- **nanoid**: Unique ID generation
- **wouter**: Lightweight React router
- **clsx & tailwind-merge**: Conditional CSS class handling

### API Integration
- **Webhook URLs**: Bots are configured to send chat messages to external webhook endpoints (client-provided URLs)
- **Form Webhook URLs**: Optional secondary webhook for form submissions

### Font & Design Assets
- **Google Fonts**: Inter and Poppins font families
- **Lucide React**: Icon library

### Type Safety
- **TypeScript**: Full type coverage across frontend, backend, and shared schema
- **Zod**: Runtime validation matching TypeScript types