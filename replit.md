# Replit.md - Resource Reservation System

## Overview

This is a full-stack TypeScript application for managing resource reservations in an educational environment. The system allows users to create, view, and manage reservations for various resources like chemistry labs, computer labs, projectors, and digital whiteboards across different time shifts.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **UI Library**: Radix UI components with shadcn/ui styling system
- **Styling**: Tailwind CSS with CSS variables for theming
- **State Management**: TanStack Query (React Query) for server state management
- **Routing**: Wouter for lightweight client-side routing
- **Form Handling**: React Hook Form with Zod validation

### Backend Architecture
- **Runtime**: Node.js with Express.js server
- **Language**: TypeScript with ESM modules
- **Database**: PostgreSQL with Drizzle ORM
- **Database Provider**: Neon serverless PostgreSQL
- **API Pattern**: RESTful API with JSON responses
- **Development**: Hot reloading with Vite middleware integration

### Database Schema
- **Users Table**: Basic user authentication (id, username, password)
- **Reservations Table**: Resource bookings (id, professor, recurso, data, turno)
- **Validation**: Zod schemas for type-safe data validation
- **Migrations**: Drizzle-kit for database schema management

## Key Components

### Data Storage
- **Primary Storage**: PostgreSQL database via Neon serverless
- **ORM**: Drizzle ORM for type-safe database operations
- **Fallback**: In-memory storage implementation for development/testing
- **Schema Location**: `shared/schema.ts` contains all database definitions

### API Endpoints
- `GET /api/reservations` - Retrieve all reservations
- `POST /api/reservations` - Create new reservation with conflict checking
- `DELETE /api/reservations/:id` - Remove existing reservation

### UI Components
- **shadcn/ui**: Comprehensive component library with Radix UI primitives
- **Form Components**: Input, Select, Button, Label with consistent styling
- **Data Display**: Card, Table components for reservation listings
- **Feedback**: Toast notifications for user actions
- **Icons**: Lucide React for consistent iconography

### Validation & Type Safety
- **Shared Types**: Common types and schemas in `shared/` directory
- **Runtime Validation**: Zod schemas for API request/response validation
- **Type Safety**: Full TypeScript coverage across frontend and backend

## Data Flow

1. **User Input**: Forms collect reservation data with client-side validation
2. **API Request**: TanStack Query manages server communication
3. **Server Processing**: Express routes handle business logic and validation
4. **Database Operations**: Drizzle ORM executes type-safe database queries
5. **Response Handling**: Success/error states update UI with toast notifications
6. **State Updates**: React Query automatically refreshes affected data

### Conflict Resolution
- Server-side validation prevents double-booking same resource/time slot
- Real-time conflict checking before reservation creation
- User-friendly error messages for booking conflicts

## External Dependencies

### Database
- **Neon**: Serverless PostgreSQL database provider
- **Connection**: Uses DATABASE_URL environment variable
- **Features**: Automatic connection pooling and scaling

### UI Framework
- **Radix UI**: Accessible, unstyled component primitives
- **Tailwind CSS**: Utility-first CSS framework
- **CSS Variables**: Dynamic theming support for light/dark modes

### Development Tools
- **Vite**: Fast build tool with hot module replacement
- **TypeScript**: Static type checking and enhanced developer experience
- **ESBuild**: Fast JavaScript bundler for production builds

## Deployment Strategy

### Build Process
1. **Frontend Build**: Vite compiles React app to `dist/public/`
2. **Backend Build**: ESBuild bundles server code to `dist/index.js`
3. **Database**: Drizzle migrations ensure schema consistency

### Environment Configuration
- **Development**: Uses Vite dev server with Express API proxy
- **Production**: Serves static files from Express with API routes
- **Database**: Requires DATABASE_URL environment variable

### Scripts
- `npm run dev`: Start development server with hot reloading
- `npm run build`: Build both frontend and backend for production
- `npm run start`: Start production server
- `npm run db:push`: Apply database schema changes

### Hosting Requirements
- Node.js runtime environment
- PostgreSQL database (Neon recommended)
- Environment variables for database connection
- Static file serving capability for frontend assets