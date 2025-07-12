# Portfolio Asset Manager

## Overview

This is a full-stack web application for managing financial assets and portfolios. The application allows users to track various types of investments including bonds, fixed deposits, gold, stocks, mutual funds, and savings accounts. It provides comprehensive portfolio analysis with cash flow calculations and investment tracking capabilities.

## System Architecture

### Frontend Architecture
- **Framework**: React with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **UI Framework**: Tailwind CSS for styling with shadcn/ui components
- **State Management**: TanStack Query (React Query) for server state management
- **Routing**: Wouter for lightweight client-side routing
- **Form Handling**: React Hook Form with Zod validation

### Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript for type safety
- **Database**: PostgreSQL with Drizzle ORM
- **Database Provider**: Neon Database (serverless PostgreSQL)
- **API Pattern**: RESTful API with JSON responses
- **Session Management**: Express sessions with PostgreSQL store

### Database Schema
The application uses a single `assets` table with flexible columns to accommodate different asset types:
- Common fields: id, type, name, investment, createdAt
- Bond/FD/LIC specific: isin, yield, purchaseDate, maturityDate, interestCycle
- Stock/Mutual Fund specific: ticker, quantity, purchasePrice
- Gold specific: weight, purity, rate
- Savings Account specific: bankName, accountNumber, interestRate, openDate

## Key Components

### Asset Management
- **Asset Creation**: Form-based asset creation with type-specific fields
- **Asset Listing**: Tabular view of all assets with filtering and sorting
- **Asset Types**: Support for 8 asset types (bond, fd, gold, lic, stock, mutual_fund, savings_india, savings_uae)
- **Validation**: Zod schema validation for data integrity

### Portfolio Analytics
- **Portfolio Summary**: Total value, average yield, monthly income calculations
- **Cash Flow Analysis**: Interest payment tracking and maturity analysis
- **Asset Categorization**: Visual categorization with icons and color coding

### User Interface
- **Responsive Design**: Mobile-first approach with Tailwind CSS
- **Component Library**: Comprehensive UI components from shadcn/ui
- **Dark Mode**: Built-in dark mode support
- **Toast Notifications**: User feedback for actions and errors

## Data Flow

1. **Client Requests**: React components make API calls through TanStack Query
2. **API Layer**: Express routes handle HTTP requests and validate data
3. **Business Logic**: Server-side processing and calculations
4. **Database Operations**: Drizzle ORM manages PostgreSQL interactions
5. **Response**: JSON data returned to client with proper error handling

## External Dependencies

### Database
- **Neon Database**: Serverless PostgreSQL for production
- **Drizzle ORM**: Type-safe database operations
- **Database Migrations**: Managed through Drizzle Kit

### UI/UX
- **Radix UI**: Unstyled, accessible UI primitives
- **Tailwind CSS**: Utility-first CSS framework
- **Lucide Icons**: Icon library for consistent iconography

### Development Tools
- **TypeScript**: Type safety across the stack
- **Vite**: Fast development and build tooling
- **ESBuild**: Fast JavaScript bundler for production

## Deployment Strategy

### Development
- **Local Development**: Uses Vite dev server with HMR
- **Database**: Connects to Neon Database via DATABASE_URL
- **Session Storage**: PostgreSQL-backed sessions

### Production
- **Build Process**: 
  - Frontend: Vite builds static assets to `dist/public`
  - Backend: ESBuild bundles server code to `dist/index.js`
- **Deployment**: Single Node.js process serving both API and static files
- **Database**: Production PostgreSQL via Neon Database

### Environment Variables
- `DATABASE_URL`: PostgreSQL connection string (required)
- `NODE_ENV`: Environment specification (development/production)

## Changelog

```
Changelog:
- July 02, 2025. Initial setup with in-memory storage
- July 02, 2025. Added PostgreSQL database integration with Drizzle ORM
  - Replaced MemStorage with DatabaseStorage for persistent data
  - Integrated Neon Database for production-ready data storage
  - All asset data now persists across application restarts
- July 02, 2025. Created comprehensive Dashboard with portfolio analytics
  - Added new Dashboard tab as default landing page
  - Implemented portfolio-wide XIRR and CAGR calculations using Newton-Raphson method
  - Built Asset Class Allocation donut chart with 8 asset type color coding
  - Created interactive investment breakdown table with percentages
  - Added comprehensive Financial Freedom tracking module
  - Enhanced portfolio metrics display with rounded monthly income values
- July 02, 2025. Implemented CSV Import & Export functionality
  - Added CSV import capability for bulk asset creation with validation
  - Implemented portfolio data export with all asset fields
  - Created cash flow data export for external analysis
  - Added user-friendly format guides and error handling
  - Integrated import/export buttons in Asset Management and Cash Flow tabs
- July 03, 2025. Enhanced CSV Import with Advanced Features
  - Added real-time progress indicator during CSV import processing
  - Implemented comprehensive post-import summary popup with detailed results
  - Added automatic duplicate detection and prevention based on asset name/type and ISIN
  - Enhanced error handling with field-level validation and user-friendly error messages
  - Created visual categorization of successful, failed, and duplicate entries
  - Fixed React Query caching issues by updating staleTime configuration
  - Fixed date parsing issues to handle DD/MM/YYYY format in asset creation and CSV import
- July 03, 2025. Investment-Based View with CAGR and XIRR Analysis
  - Implemented comprehensive Investment Performance Summary Cards showing portfolio-wide metrics
  - Added Portfolio CAGR calculation with average annualized growth rate across all assets
  - Added Portfolio XIRR calculation using Newton-Raphson method for time-weighted cash flow returns
  - Created Best Performer identification highlighting the highest CAGR asset
  - Enhanced cash flow analysis table with sortable CAGR and XIRR columns
  - Added Indian currency formatting (K/L/CR) throughout investment performance displays
  - Integrated glassmorphism UI effects with neon glows and particle animations for immersive experience
```

## User Preferences

```
Preferred communication style: Simple, everyday language.
```