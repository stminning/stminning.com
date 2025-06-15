# ST MINNING Dashboard - Development Guide

## Project Overview
This is a client-side cryptocurrency mining simulation dashboard built with vanilla HTML, CSS, and JavaScript. The project simulates a mining platform where users can register, login, manage packages, track earnings, and perform transactions.

## Architecture

### Authentication System
- Uses localStorage for user session management
- Two authentication methods: email/password and Google OAuth simulation
- User data structure includes: id, username, email, balance, dailyIncome, totalWithdrawn, transactions
- New users start with $5 balance

### Data Storage
- **localStorage** is the primary data storage mechanism
- `users` array stores all registered users
- `currentUser` stores the active session
- All user interactions (transactions, mining progress) are persisted locally

### Core Components

#### 1. User Management
- **Signup/Login**: Email validation, password confirmation, Google OAuth simulation
- **Profile**: User information display and verification status
- **Settings**: Theme toggle, 2FA setup, notifications preferences

#### 2. Mining System
- Package-based mining with 6 different tiers ($50-$10,000)
- 30-day mining cycles requiring 24-hour user interaction
- Progress tracking with visual indicators
- 5% cancellation fee system

#### 3. Financial Operations
- **Deposits**: Multiple payment methods (USDT, BTC, BNB, Binance Pay)
- **Withdrawals**: Email-based request system via FormSubmit
- **Transactions**: Complete history with status tracking
- **QR Code Generation**: Dynamic QR codes for deposit addresses

#### 4. Verification System
- ID card upload (front/back)
- Selfie capture via camera API
- Two-factor authentication with Google Authenticator QR codes
- Document submission via email

## Key Features

### Payment Integration
- QR code generation using QRCode.js library
- FormSubmit.co integration for withdrawal requests
- Email notifications for verification and withdrawal requests

### Security Features
- Two-factor authentication simulation
- Camera access for identity verification
- Session management with automatic redirects

### UI/UX
- Dark/Light theme toggle
- Responsive design with Bootstrap 5
- Animated particle background
- Loading states and notifications
- Mobile-optimized interface

## Development Workflow

### File Structure
- `index.html` - Main dashboard (entry point after login)
- `login.html` - User authentication page
- `signup.html` - User registration page
- `redirect.html` - Fallback redirect handler

### State Management
All application state is managed through localStorage with the following key patterns:
- User authentication state
- Mining progress and timers
- Transaction history
- Application settings (theme, notifications)

### External Dependencies
- Bootstrap 5.3.0 (CSS framework)
- Font Awesome 6.0.0 (icons)
- QRCode.js (QR code generation)
- Google Fonts (Poppins, Roboto)

## Important Implementation Notes

### Mining Logic
- Packages run for 30 days with daily interaction requirements
- Timer system tracks next required user interaction
- Progress calculation based on elapsed time vs total duration
- Earnings accumulate based on package daily rates

### Email Integration
- Uses FormSubmit.co for serverless form handling
- Withdrawal requests sent to stminning@gmail.com
- Verification documents attached as image files
- Template-based email formatting

### QR Code Generation
- Deposit QR codes contain only wallet addresses
- Two-factor authentication uses proper otpauth:// format
- All QR codes use high error correction level

### Authentication Flow
1. Check localStorage for existing session
2. Redirect to login if no valid session
3. Auto-redirect logged users away from auth pages
4. Session persists across browser sessions

This application is designed to work entirely client-side with localStorage persistence and external services for email functionality.