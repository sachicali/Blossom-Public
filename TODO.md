# Blossomss Development TODO

This document outlines planned features, improvements, and refactoring tasks for the Blossomss application.

## Recently Completed (July 2025) ✅
- [x] Firebase/Firestore migration (all 28 data models)
- [x] All 26 Firebase migration tests passing
- [x] Comprehensive security rules deployed to production
- [x] Production build completed successfully
- [x] Real-time listener hooks implemented
- [x] Offline functionality guide created
- [x] Automated testing framework set up
- [x] Security improvements from Copilot review
- [x] Automated security workflows (CodeQL, dependency scanning)
- [x] Branch protection and security documentation
- [x] Custom domain configuration (blossomss.com)
- [x] Cloud Run monitoring and alerting setup
- [x] Secure file uploads with signed URLs
- [x] Error logging to Firebase collection
- [x] Discord OAuth integration with Firebase Auth

## High Priority (P0) - Phase A Foundation

### Authentication & Security
- [x] Complete authentication system implementation:
  - [x] Password-based authentication endpoints
  - [x] OAuth integration (Google, Discord)
  - [x] Phone number authentication with OTP verification
- [x] Implement proper JWT verification on the backend (created auth.middleware.ts)
- [x] Implement protected routing and JWT middleware
- [x] Set up React Query for state management
- [x] Build core dashboard page
- [ ] Create user profile management UI
- [ ] Implement comprehensive input validation on all API endpoints (backend)
- [ ] Implement rate limiting on API endpoints (backend)
- [ ] Ensure `bcrypt` is configured with sufficient salt rounds for password storage (backend)

### Core Functionality
- [ ] Implement a robust suite of unit, integration, and end-to-end tests (frontend & backend)
- [ ] Expand admin panel functionality:
    - [ ] User management interface (CRUD, roles)
    - [ ] System monitoring dashboards
    - [ ] Content moderation tools

### Deployment & Infrastructure
- [ ] Deploy to Google Cloud Run (manual steps required)
- [ ] Set up production monitoring and alerts
- [ ] Migrate production data from PostgreSQL to Firestore
- [ ] Roll out to beta users

## Medium Priority (P1) - Phase B Features

### Real-time Communication
- [ ] Implement WebSocket reconnection logic and error handling
- [ ] Build real-time messaging system between co-parents
- [ ] Create family room management features
- [ ] Optimize WebSocket performance for scalability (e.g., load balancing, dedicated service investigation)
- [ ] Implement push notifications via Firebase Cloud Messaging

### Authentication Enhancements
- [ ] Implement Two-Factor Authentication (2FA) for user logins
- [ ] Add password reset functionality
- [ ] Implement session management and device tracking

### User Experience (UX)
- [ ] Improve loading indicators and skeleton screens across the application.
- [ ] Expand notification system with user-configurable preferences.
- [ ] Conduct a thorough accessibility audit and implement improvements.
- [ ] Implement an in-app tour/onboarding for new users.

### Core Features Implementation
- [ ] Calendar & Scheduling:
  - [ ] Event creation and management
  - [ ] Shared calendar views
  - [ ] Parenting schedule templates
  - [ ] Event notifications
- [ ] Expense Management:
  - [ ] Expense tracking and splitting
  - [ ] PayPal integration for payments
  - [ ] Expense categories and reporting
  - [ ] Receipt attachments
- [ ] Document Management:
  - [ ] Document upload and organization
  - [ ] Secure sharing with permissions
  - [ ] Document categories (medical, legal, school)
  
### Performance Optimization
- [ ] Implement server-side image optimization (resizing, compression) for uploaded photos
- [ ] Regularly analyze and optimize frontend bundle size
- [ ] Review and optimize Firestore queries with proper indexes
- [ ] Implement caching strategies for frequently accessed data
- [ ] Add offline support for critical features

## Low Priority (P2)

### Feature Enhancements
- [ ] Advanced Calendar Features:
    - [ ] AI-powered Event Suggestions.
    - [ ] Integrated Task Management.
    - [ ] Shared Event Creation Workflows.
- [ ] Enhanced Messaging:
    - [ ] Video Messaging.
    - [ ] Rich Text Editing in Messages.
    - [ ] Message Reactions.
    - [ ] Scheduled Messages.
- [ ] Document Management Improvements:
    - [ ] Document Versioning.
    - [ ] Secure Document Sharing with Permissions.
    - [ ] Document Scanning (Mobile).
- [ ] Advanced Expense Tracking:
    - [ ] Receipt Scanning.
    - [ ] Expense Categories Customization.
    - [ ] Detailed Reporting & Analytics.
- [ ] Photo Album Enhancements:
    - [ ] Photo Editing Tools.
    - [ ] Facial Recognition (Opt-in).
    - [ ] Private Photo Sharing.
- [ ] Child Profile Expansion:
    - [ ] Growth Charts.
    - [ ] Developmental Milestones Tracking.
    - [ ] Wishlist Management.

### General Improvements
- [ ] Add more inline comments for complex logic and JSDoc/TSDoc for functions/components
- [ ] Implement Internationalization (i18n) support
- [ ] Integrate Stripe as an alternative or additional payment gateway
- [ ] Ensure consistent coding style, naming conventions, and architectural patterns
- [ ] Add comprehensive API documentation
- [ ] Create user documentation and help center
- [ ] Implement automated backup strategies

## Technical Debt & Refactoring
- [ ] Refactor WebSocket implementation to use Socket.io or similar for better scalability
- [ ] Migrate from Bun to Node.js if Bun limitations become problematic
- [ ] Implement proper dependency injection for better testability
- [ ] Add comprehensive logging and monitoring
- [ ] Create shared component library for consistent UI

## Notes
- Phase A (Foundation) tasks should be completed first as they form the core of the application
- Phase B features can be developed in parallel once authentication is complete
- Performance optimizations should be ongoing throughout development
- Security improvements should be prioritized and continuously reviewed
