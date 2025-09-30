# Overview

SecureExam is a comprehensive online examination platform designed to provide secure, proctored testing capabilities with advanced monitoring features. The application combines QR code-based hall ticket authentication, AI-powered face detection, real-time monitoring dashboards, and a secure kiosk exam mode to ensure academic integrity during online examinations.

The platform serves two primary user types: administrators who create and monitor exams, and students who take authenticated examinations under controlled conditions.

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture
- **Framework**: React with TypeScript using Vite as the build tool
- **UI Library**: shadcn/ui components built on top of Radix UI primitives
- **Styling**: Tailwind CSS with a custom design system featuring gradient themes and glassmorphism effects
- **Routing**: Wouter for client-side routing with role-based route protection
- **State Management**: TanStack Query for server state management and caching

## Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ESM modules
- **API Design**: RESTful API with WebSocket support for real-time features
- **Authentication**: Passport.js with JWT tokens (email/password authentication)
- **Real-time Communication**: WebSocket server for live monitoring and incident reporting

## Data Storage
- **Database**: PostgreSQL with Neon serverless hosting
- **ORM**: Drizzle ORM with type-safe schema definitions
- **Session Storage**: PostgreSQL-backed session store using connect-pg-simple
- **Migrations**: Drizzle Kit for schema migrations

## Key Features Architecture

### Authentication & Authorization
- Standard email/password authentication using Passport.js Local Strategy
- JWT (JSON Web Token) based session management for stateless authentication
- Role-based access control (admin/student roles)
- Session storage with PostgreSQL for persistent sessions
- Middleware-based route protection using JWT verification
- Platform-independent authentication (works on Render, AWS, Heroku, etc.)

### QR Code System
- Hall ticket generation with embedded metadata (student info, exam details, timestamps)
- QR code validation with expiration checks
- Secure authentication flow using QR scanning

### AI-Powered Monitoring
- Browser-based face detection using web APIs
- Real-time webcam monitoring with violation detection
- Multiple face detection and attention tracking
- Configurable sensitivity thresholds

### Real-time Monitoring
- WebSocket-based live communication between admin dashboard and student clients
- Real-time incident logging and alerting
- Live exam session monitoring with status updates
- Admin dashboard with live statistics and controls

### Exam Security
- Fullscreen exam mode with exit prevention
- Tab switching detection and logging
- Camera monitoring throughout exam duration
- Automatic security incident creation and escalation

## External Dependencies

- **Database**: Neon PostgreSQL serverless database
- **Authentication**: Passport.js with JWT for platform-independent authentication
- **Password Hashing**: bcrypt for secure password storage
- **UI Components**: Radix UI primitives for accessible component foundation
- **Styling**: Tailwind CSS for utility-first styling approach
- **QR Code Generation**: qrcode library for hall ticket QR generation
- **Face Detection**: Browser native APIs for real-time face recognition
- **WebSocket**: Native WebSocket API for real-time communication
- **File Upload**: Browser File API for identity verification
- **Session Management**: PostgreSQL-backed sessions via connect-pg-simple

## Recent Changes (September 2025)

### Authentication Migration
- **Migrated from Replit Auth to Passport.js + JWT**
  - Removed dependency on Replit OAuth (replitAuth.ts)
  - Implemented standard email/password login system
  - Created JWT-based token authentication
  - Added file-based admin credentials for demo (server/admin-credentials.json)
  - Created new admin login page (/admin/login)
  - Updated all frontend routes to use new authentication
  - Application now works on any hosting platform (Render, AWS, Heroku, etc.)
  
### Demo Credentials
- Admin login: admin@secureexam.com / admin123
- Credentials stored in ADMIN_CREDENTIALS.md and server/admin-credentials.json