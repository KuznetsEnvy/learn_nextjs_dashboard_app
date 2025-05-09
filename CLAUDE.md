# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Next.js dashboard application built with the App Router, showcasing a financial dashboard with invoices and customer management. It demonstrates modern Next.js 14+ features including server components, data fetching, authentication, and more.

## Common Commands

```bash
# Install dependencies (using pnpm)
pnpm install

# Start development server with turbopack
pnpm dev

# Build the application
pnpm build

# Start production server
pnpm start

# Lint the codebase
pnpm lint
```

## Architecture

### 1. Next.js App Router Structure

This application uses Next.js App Router with a folder-based routing system:

- `app/` - Contains all routes and components
  - `dashboard/` - Dashboard routes (protected by authentication)
    - `(overview)/` - Dashboard home page (grouped route)
    - `customers/` - Customers management
    - `invoices/` - Invoices management with CRUD operations
  - `login/` - Authentication page
  - `lib/` - Utility functions and data fetching
  - `ui/` - UI components

### 2. Authentication Flow

- Uses Next.js Auth with Credentials provider
- Authentication config in `auth.config.ts` and `auth.ts`
- Protected routes via middleware.ts
- Login form at `/login` redirects to dashboard upon success

### 3. Data Fetching

- Server-side data fetching in `app/lib/data.ts`
- Uses the Postgres client for database queries
- Structured type definitions in `app/lib/definitions.ts`

### 4. Server Actions

- Form handling through React Server Actions in `app/lib/actions.ts`
- Uses Zod for form validation
- Implements create, update, and delete operations for invoices

### 5. Key Components

- Dashboard components with cards, charts, and tables
- Form components for creating and editing invoices
- Navigation and layout components
- Loading states with Suspense boundaries

### 6. State Management

- Uses React's `useActionState` for form state management
- Server-side data fetching with proper error handling
- Cache invalidation with `revalidatePath`

### 7. Performance Features

- Route segmentation for code splitting
- Loading states with Suspense boundaries
- Streaming with React Suspense
- Data fetching optimizations

## Development Notes

- Database connections use PostgreSQL via the `postgres` package
- Authentication is handled via NextAuth.js
- Form validation uses Zod
- Styling is done with Tailwind CSS
- Type safety is ensured through TypeScript