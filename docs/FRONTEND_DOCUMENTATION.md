# ShurYan – Frontend Documentation

<div align="center">
  <img src="./images/shuryan.png" alt="ShurYan Logo" width="200" style="margin: 0 20px;"/>
  <img src="./images/proAr.png" alt="DEPI Logo" width="150" style="margin: 0 20px;"/>
</div>

<div align="center">
  <strong>Developed as a Graduation Project for the <a href="https://depi.gov.eg/">Dew of Egypt Digital Initiative (DEPI)</a></strong>
</div>

<br/>

<div align="center">
  
![React](https://img.shields.io/badge/React-19.1.1-61DAFB?style=for-the-badge&logo=react)
![Vite](https://img.shields.io/badge/Vite-7.1.7-646CFF?style=for-the-badge&logo=vite)
![TailwindCSS](https://img.shields.io/badge/Tailwind-4.1.16-38B2AC?style=for-the-badge&logo=tailwind-css)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![DEPI](https://img.shields.io/badge/DEPI-2025-orange?style=for-the-badge)

</div>

---

<div align="center">

### 📌 Main Repository

This is the **Frontend** repository. For complete project overview, architecture diagram, and links to all repositories:

**[🏠 Visit ShurYan Main Repository →](https://github.com/muhamedessamz/ShurYan)**

</div>

---

## Table of Contents

1. [Project Introduction](#project-introduction)
2. [Architecture Overview](#architecture-overview)
3. [Tech Stack](#tech-stack)
4. [Folder Structure](#folder-structure)
5. [Environment Setup](#environment-setup)
6. [Features by Role](#features-by-role)
7. [Routing Structure](#routing-structure)
8. [State Management](#state-management)
9. [API Integration](#api-integration)
10. [Authentication & Authorization](#authentication--authorization)
11. [UI Components](#ui-components)
12. [Styling & Theming](#styling--theming)
13. [Real-Time Features (SignalR)](#real-time-features-signalr)
14. [Performance Optimization](#performance-optimization)
15. [Testing](#testing)
16. [Deployment](#deployment)
17. [Best Practices](#best-practices)
18. [Contributing](#contributing)
19. [License](#license)

---

## Project Introduction

**ShurYan Frontend** is a modern, responsive React application that provides a comprehensive user interface for the ShurYan Healthcare Management System. Built with React 19 and Vite, it offers a seamless experience across all user roles.

### Key Features

- **Multi-Role Interface**: Dedicated dashboards for Patients, Doctors, Laboratories, Pharmacies, and Verifiers
- **Real-Time Updates**: SignalR integration for instant notifications
- **Responsive Design**: Mobile-first approach with TailwindCSS
- **Performance Optimized**: Code splitting, lazy loading, and optimized bundle size
- **Type-Safe**: PropTypes validation for component props
- **Modern UI/UX**: Material-UI components with custom theming
- **Secure**: JWT-based authentication with protected routes
- **Accessible**: WCAG 2.1 AA compliant

---

## Architecture Overview

ShurYan Frontend follows a **Feature-Based Architecture** with clear separation of concerns:

```
┌─────────────────────────────────────────────────────┐
│                  Presentation Layer                 │
│            (Pages, Layouts, Components)             │
└──────────────────┬──────────────────────────────────┘
                   │
┌──────────────────▼──────────────────────────────────┐
│                  Feature Modules                    │
│     (Auth, Doctor, Patient, Lab, Pharmacy, etc)     │
└──────────────────┬──────────────────────────────────┘
                   │
┌──────────────────▼──────────────────────────────────┐
│                  State Management                   │
│              (Zustand Stores, Contexts)             │
└──────────────────┬──────────────────────────────────┘
                   │
┌──────────────────▼──────────────────────────────────┐
│                  API Layer                          │
│         (Axios Client, Service Functions)           │
└──────────────────┬──────────────────────────────────┘
                   │
┌──────────────────▼──────────────────────────────────┐
│                  External Services                  │
│        (Backend API, SignalR, Google OAuth)         │
└─────────────────────────────────────────────────────┘
```

### Architecture Principles

- **Feature-Based**: Code organized by features, not file types
- **Component Composition**: Reusable, composable UI components
- **Unidirectional Data Flow**: Predictable state management
- **Separation of Concerns**: Clear boundaries between layers
- **DRY (Don't Repeat Yourself)**: Shared utilities and hooks

---

## Tech Stack

| Technology | Version | Purpose |
|------------|---------|---------|
| **React** | 19.1.1 | UI library |
| **Vite** | 7.1.7 | Build tool & dev server |
| **React Router** | 7.9.4 | Client-side routing |
| **TailwindCSS** | 4.1.16 | Utility-first CSS framework |
| **Material-UI** | 7.3.5 | Component library |
| **Zustand** | 5.0.8 | State management |
| **Axios** | 1.12.2 | HTTP client |
| **SignalR** | 10.0.0 | Real-time communication |
| **Framer Motion** | 12.23.24 | Animations |
| **React Hook Form** | - | Form management |
| **Yup** | 1.7.1 | Schema validation |
| **Leaflet** | 1.9.4 | Interactive maps |
| **date-fns** | 4.1.0 | Date manipulation |
| **Lucide React** | 0.548.0 | Icon library |

### Why These Technologies?

- **React 19**: Latest features including concurrent rendering and automatic batching
- **Vite**: Lightning-fast HMR and optimized production builds
- **TailwindCSS**: Rapid UI development with utility classes
- **Zustand**: Lightweight state management with minimal boilerplate
- **Material-UI**: Production-ready components with accessibility built-in

---

## Folder Structure

```
ShurYan-Frontend-dev/
├── public/                      # Static assets
├── src/
│   ├── api/                     # API client configuration
│   │   ├── client.js            # Axios instance setup
│   │   └── services/            # API service functions (13 services)
│   │       ├── authService.js
│   │       ├── doctorService.js
│   │       ├── patientService.js
│   │       ├── appointmentService.js
│   │       ├── prescriptionService.js
│   │       ├── laboratoryService.js
│   │       ├── pharmacyService.js
│   │       ├── paymentService.js
│   │       ├── notificationService.js
│   │       ├── chatService.js
│   │       └── ...
│   │
│   ├── assets/                  # Images, fonts, etc.
│   │   ├── shuryan.png
│   │   └── proAr.png
│   │
│   ├── components/              # Shared components (34 components)
│   │   ├── common/              # Generic reusable components
│   │   │   ├── Button.jsx
│   │   │   ├── Input.jsx
│   │   │   ├── Modal.jsx
│   │   │   ├── AppLoader.jsx
│   │   │   └── ...
│   │   └── layout/              # Layout components
│   │       ├── MainLayout.jsx
│   │       ├── AuthLayout.jsx
│   │       ├── DoctorLayout.jsx
│   │       ├── PatientLayout.jsx
│   │       ├── PharmacyLayout.jsx
│   │       └── LaboratoryLayout.jsx
│   │
│   ├── config/                  # Configuration files
│   │   └── constants.js
│   │
│   ├── contexts/                # React contexts
│   │   └── ThemeContext.jsx
│   │
│   ├── features/                # Feature modules (6 modules, 234 files)
│   │   ├── auth/                # Authentication feature
│   │   │   ├── components/
│   │   │   ├── pages/
│   │   │   ├── hooks/
│   │   │   └── index.js
│   │   │
│   │   ├── doctor/              # Doctor feature (84 files)
│   │   │   ├── components/
│   │   │   ├── pages/
│   │   │   │   ├── DoctorDashboard.jsx
│   │   │   │   ├── DoctorProfilePage.jsx
│   │   │   │   ├── PatientsPage.jsx
│   │   │   │   ├── AppointmentsPage.jsx
│   │   │   │   ├── ReviewsPage.jsx
│   │   │   │   └── SessionModalWrapper.jsx
│   │   │   ├── hooks/
│   │   │   └── index.js
│   │   │
│   │   ├── patient/             # Patient feature (70 files)
│   │   │   ├── components/
│   │   │   ├── pages/
│   │   │   │   ├── SearchDoctorsPage.jsx
│   │   │   │   ├── AppointmentsPage.jsx
│   │   │   │   ├── PrescriptionsPage.jsx
│   │   │   │   ├── LabResultsPage.jsx
│   │   │   │   ├── LabPrescriptionsPage.jsx
│   │   │   │   ├── LabOrdersPage.jsx
│   │   │   │   ├── ProfilePage.jsx
│   │   │   │   ├── PaymentSuccessPage.jsx
│   │   │   │   └── PaymentFailedPage.jsx
│   │   │   ├── hooks/
│   │   │   └── index.js
│   │   │
│   │   ├── pharmacy/            # Pharmacy feature (23 files)
│   │   │   ├── components/
│   │   │   ├── pages/
│   │   │   │   ├── PharmacyDashboard.jsx
│   │   │   │   ├── OrdersPage.jsx
│   │   │   │   └── PharmacyProfilePage.jsx
│   │   │   └── index.js
│   │   │
│   │   ├── laboratory/          # Laboratory feature (20 files)
│   │   │   ├── components/
│   │   │   ├── pages/
│   │   │   │   ├── LaboratoryDashboard.jsx
│   │   │   │   ├── ServicesPage.jsx
│   │   │   │   ├── OrdersPage.jsx
│   │   │   │   └── LaboratoryProfilePage.jsx
│   │   │   └── index.js
│   │   │
│   │   └── verifier/            # Verifier feature (16 files)
│   │       ├── components/
│   │       ├── pages/
│   │       │   ├── StatisticsPage.jsx
│   │       │   ├── DoctorsPage.jsx
│   │       │   ├── PharmaciesPage.jsx
│   │       │   └── LaboratoriesPage.jsx
│   │       └── index.js
│   │
│   ├── hooks/                   # Custom React hooks (7 hooks)
│   │   ├── useAuth.js
│   │   ├── useNotifications.js
│   │   ├── useSignalR.js
│   │   ├── useDebounce.js
│   │   └── ...
│   │
│   ├── pages/                   # Top-level pages
│   │   ├── home/
│   │   │   └── HomePage.jsx
│   │   ├── NotFoundPage.jsx
│   │   └── UnauthorizedPage.jsx
│   │
│   ├── providers/               # Context providers
│   │   ├── AuthProvider.jsx
│   │   ├── NotificationProvider.jsx
│   │   └── SignalRProvider.jsx
│   │
│   ├── services/                # Business logic services
│   │   └── signalRService.js
│   │
│   ├── stores/                  # Zustand stores
│   │   └── authStore.js
│   │
│   ├── styles/                  # Global styles (5 files)
│   │   ├── index.css
│   │   ├── tailwind.css
│   │   └── ...
│   │
│   ├── utils/                   # Utility functions (10 files)
│   │   ├── formatters.js
│   │   ├── validators.js
│   │   ├── helpers.js
│   │   └── ...
│   │
│   ├── App.jsx                  # Root component
│   ├── Router.jsx               # Route configuration
│   └── main.jsx                 # Application entry point
│
├── .env                         # Environment variables
├── .gitignore
├── eslint.config.js             # ESLint configuration
├── index.html                   # HTML template
├── package.json                 # Dependencies
├── postcss.config.js            # PostCSS configuration
├── tailwind.config.js           # Tailwind configuration
└── vite.config.js               # Vite configuration
```

---

## Environment Setup

### Prerequisites

- **Node.js** 18+ ([Download](https://nodejs.org/))
- **npm** or **yarn**
- **Git** for version control

### Local Development Setup

#### 1. Clone the Repository

```bash
git clone <repository-url>
cd ShurYan-Frontend-dev
```

#### 2. Install Dependencies

```bash
npm install
# or
yarn install
```

#### 3. Configure Environment Variables

Create `.env` file in the root directory:

```env
# API Configuration
VITE_API_BASE_URL=https://api.shuryan.com
VITE_API_TIMEOUT=30000

# SignalR Configuration
VITE_SIGNALR_HUB_URL=https://api.shuryan.com/hubs/notifications

# Google OAuth
VITE_GOOGLE_CLIENT_ID=your-google-client-id

# Paymob Configuration
VITE_PAYMOB_PUBLIC_KEY=your-paymob-public-key

# Feature Flags
VITE_ENABLE_ANALYTICS=false
VITE_ENABLE_DEBUG=true

# App Configuration
VITE_APP_NAME=ShurYan
VITE_APP_VERSION=1.0.0
```

#### 4. Run Development Server

```bash
npm run dev
# or
yarn dev
```

The application will be available at:
- **Local**: `http://localhost:5173`
- **Network**: `http://192.168.x.x:5173`

#### 5. Build for Production

```bash
npm run build
# or
yarn build
```

#### 6. Preview Production Build

```bash
npm run preview
# or
yarn preview
```

### Environment Variables Reference

| Variable | Description | Example |
|----------|-------------|---------|
| `VITE_API_BASE_URL` | Backend API base URL | `https://api.shuryan.com` |
| `VITE_SIGNALR_HUB_URL` | SignalR hub endpoint | `https://api.shuryan.com/hubs/notifications` |
| `VITE_GOOGLE_CLIENT_ID` | Google OAuth client ID | `xxx.apps.googleusercontent.com` |
| `VITE_PAYMOB_PUBLIC_KEY` | Paymob public key | `your-public-key` |

---

## Features by Role

### 🏥 Patient Features

- **Doctor Search & Discovery**
  - Search doctors by specialty, location, name
  - Filter by rating, experience, consultation fee
  - View doctor profiles with clinic information
  - Interactive map showing nearby doctors

- **Appointment Management**
  - Book appointments with real-time availability
  - View upcoming and past appointments
  - Cancel appointments
  - Receive appointment reminders

- **Prescriptions & Lab Orders**
  - View digital prescriptions
  - Send prescriptions to pharmacies
  - Track prescription status
  - View lab prescriptions and orders
  - Download lab results

- **Payments**
  - Secure online payment via Paymob
  - Payment history
  - Download receipts

### 👨‍⚕️ Doctor Features

- **Dashboard**
  - Today's appointments overview
  - Patient statistics
  - Revenue analytics
  - Recent reviews

- **Patient Management**
  - View patient list
  - Access patient medical history
  - View patient appointments

- **Appointment Management**
  - View daily/weekly schedule
  - Manage appointment status
  - Start consultation sessions

- **Session Management**
  - Record consultation notes
  - Create prescriptions
  - Order lab tests
  - AI-powered diagnosis assistance

- **Profile Management**
  - Update personal information
  - Manage clinic details
  - Set consultation fees
  - Upload verification documents

- **Reviews & Ratings**
  - View patient reviews
  - Reply to reviews
  - Rating statistics

### 🔬 Laboratory Features

- **Dashboard**
  - Pending orders overview
  - Revenue statistics
  - Service analytics

- **Order Management**
  - View lab orders
  - Respond with pricing
  - Update order status
  - Upload test results

- **Service Management**
  - Add/edit lab services
  - Set pricing
  - Manage availability

- **Profile Management**
  - Update lab information
  - Manage working hours
  - Set home collection options

### 💊 Pharmacy Features

- **Dashboard**
  - Pending prescriptions
  - Revenue statistics
  - Order analytics

- **Order Management**
  - View prescription orders
  - Respond with availability and pricing
  - Mark prescriptions as dispensed

- **Profile Management**
  - Update pharmacy information
  - Manage working hours
  - Update contact details

### ✅ Verifier Features

- **Doctor Verification**
  - Review doctor applications
  - Verify submitted documents
  - Approve/reject applications
  - View verification statistics

- **Statistics Dashboard**
  - Pending verifications
  - Approval/rejection rates
  - Monthly statistics

---

## Routing Structure

### Public Routes

| Route | Component | Description |
|-------|-----------|-------------|
| `/` | HomePage | Landing page |
| `/login` | LoginPage | User login |
| `/register` | RegisterPage | User registration |
| `/verify-email` | VerifyEmailPage | Email verification |
| `/forgot-password` | ForgotPasswordPage | Password reset request |

### Patient Routes (`/patient`)

| Route | Component | Auth Required |
|-------|-----------|---------------|
| `/patient/search` | SearchDoctorsPage | ✅ |
| `/patient/appointments` | AppointmentsPage | ✅ |
| `/patient/prescriptions` | PrescriptionsPage | ✅ |
| `/patient/lab-results` | LabResultsPage | ✅ |
| `/patient/lab-prescriptions` | LabPrescriptionsPage | ✅ |
| `/patient/lab-orders` | LabOrdersPage | ✅ |
| `/patient/profile` | ProfilePage | ✅ |
| `/patient/payment/success` | PaymentSuccessPage | ✅ |
| `/patient/payment/failed` | PaymentFailedPage | ✅ |

### Doctor Routes (`/doctor`)

| Route | Component | Auth Required |
|-------|-----------|---------------|
| `/doctor/dashboard` | DoctorDashboard | ✅ |
| `/doctor/profile` | DoctorProfilePage | ✅ |
| `/doctor/patients` | PatientsPage | ✅ |
| `/doctor/appointments` | AppointmentsPage | ✅ |
| `/doctor/reviews` | ReviewsPage | ✅ |
| `/doctor/session/:id` | SessionModalWrapper | ✅ |

### Laboratory Routes (`/laboratory`)

| Route | Component | Auth Required |
|-------|-----------|---------------|
| `/laboratory/dashboard` | LaboratoryDashboard | ✅ |
| `/laboratory/services` | ServicesPage | ✅ |
| `/laboratory/orders` | OrdersPage | ✅ |
| `/laboratory/profile` | LaboratoryProfilePage | ✅ |

### Pharmacy Routes (`/pharmacy`)

| Route | Component | Auth Required |
|-------|-----------|---------------|
| `/pharmacy/dashboard` | PharmacyDashboard | ✅ |
| `/pharmacy/orders` | OrdersPage | ✅ |
| `/pharmacy/profile` | PharmacyProfilePage | ✅ |

### Verifier Routes (`/verifier`)

| Route | Component | Auth Required |
|-------|-----------|---------------|
| `/verifier/statistics` | StatisticsPage | ✅ |
| `/verifier/doctors` | DoctorsPage | ✅ |
| `/verifier/pharmacies` | PharmaciesPage | ✅ |
| `/verifier/laboratories` | LaboratoriesPage | ✅ |

---

## State Management

### Zustand Store (authStore.js)

```javascript
import { create } from 'zustand';

const useAuthStore = create((set) => ({
  user: null,
  token: null,
  isAuthenticated: false,
  
  login: (user, token) => set({ 
    user, 
    token, 
    isAuthenticated: true 
  }),
  
  logout: () => set({ 
    user: null, 
    token: null, 
    isAuthenticated: false 
  }),
  
  updateUser: (userData) => set((state) => ({ 
    user: { ...state.user, ...userData } 
  })),
}));

export default useAuthStore;
```

### Context Providers

#### AuthProvider
- Manages authentication state
- Provides login/logout functions
- Handles token refresh

#### NotificationProvider
- Manages notification state
- Provides notification display functions

#### SignalRProvider
- Manages SignalR connection
- Handles real-time events

---

## API Integration

### Axios Client Configuration

```javascript
// src/api/client.js
import axios from 'axios';

const apiClient = axios.create({
  baseURL: import.meta.env.VITE_API_BASE_URL,
  timeout: 30000,
  headers: {
    'Content-Type': 'application/json',
  },
});

// Request interceptor
apiClient.interceptors.request.use(
  (config) => {
    const token = localStorage.getItem('token');
    if (token) {
      config.headers.Authorization = `Bearer ${token}`;
    }
    return config;
  },
  (error) => Promise.reject(error)
);

// Response interceptor
apiClient.interceptors.response.use(
  (response) => response.data,
  (error) => {
    if (error.response?.status === 401) {
      // Handle unauthorized
      localStorage.removeItem('token');
      window.location.href = '/login';
    }
    return Promise.reject(error);
  }
);

export default apiClient;
```

### API Services

#### authService.js
```javascript
import apiClient from '../client';

export const authService = {
  login: (credentials) => 
    apiClient.post('/api/Auth/login', credentials),
  
  register: (userData) => 
    apiClient.post('/api/Auth/register/patient', userData),
  
  verifyEmail: (data) => 
    apiClient.post('/api/Auth/verify-email', data),
  
  logout: () => 
    apiClient.post('/api/Auth/logout'),
};
```

#### doctorService.js
```javascript
export const doctorService = {
  getDashboardStats: () => 
    apiClient.get('/api/doctors/me/dashboard/stats'),
  
  getProfile: () => 
    apiClient.get('/api/doctors/me/profile'),
  
  updateProfile: (data) => 
    apiClient.put('/api/doctors/me/update-profile', data),
  
  getPatients: () => 
    apiClient.get('/api/doctors/me/patients'),
};
```

---

## Authentication & Authorization

### Protected Route Component

```javascript
import { Navigate } from 'react-router-dom';
import useAuthStore from '@/stores/authStore';

export const ProtectedRoute = ({ children, roles }) => {
  const { isAuthenticated, user } = useAuthStore();
  
  if (!isAuthenticated) {
    return <Navigate to="/login" replace />;
  }
  
  if (roles && !roles.includes(user?.role)) {
    return <Navigate to="/unauthorized" replace />;
  }
  
  return children;
};
```

### JWT Token Management

- **Storage**: localStorage
- **Refresh**: Automatic token refresh before expiry
- **Expiry Handling**: Redirect to login on token expiry

---

## UI Components

### Common Components

#### Button Component
```javascript
export const Button = ({ 
  children, 
  variant = 'primary', 
  size = 'md', 
  ...props 
}) => {
  const baseStyles = 'rounded-lg font-medium transition-colors';
  const variants = {
    primary: 'bg-blue-600 text-white hover:bg-blue-700',
    secondary: 'bg-gray-200 text-gray-800 hover:bg-gray-300',
    danger: 'bg-red-600 text-white hover:bg-red-700',
  };
  const sizes = {
    sm: 'px-3 py-1.5 text-sm',
    md: 'px-4 py-2',
    lg: 'px-6 py-3 text-lg',
  };
  
  return (
    <button 
      className={`${baseStyles} ${variants[variant]} ${sizes[size]}`}
      {...props}
    >
      {children}
    </button>
  );
};
```

#### Modal Component
```javascript
import { motion, AnimatePresence } from 'framer-motion';

export const Modal = ({ isOpen, onClose, children }) => {
  return (
    <AnimatePresence>
      {isOpen && (
        <motion.div
          initial={{ opacity: 0 }}
          animate={{ opacity: 1 }}
          exit={{ opacity: 0 }}
          className="fixed inset-0 bg-black/50 flex items-center justify-center z-50"
          onClick={onClose}
        >
          <motion.div
            initial={{ scale: 0.9, opacity: 0 }}
            animate={{ scale: 1, opacity: 1 }}
            exit={{ scale: 0.9, opacity: 0 }}
            className="bg-white rounded-lg p-6 max-w-md w-full"
            onClick={(e) => e.stopPropagation()}
          >
            {children}
          </motion.div>
        </motion.div>
      )}
    </AnimatePresence>
  );
};
```

---

## Styling & Theming

### TailwindCSS Configuration

```javascript
// tailwind.config.js
export default {
  content: ['./index.html', './src/**/*.{js,jsx}'],
  theme: {
    extend: {
      colors: {
        primary: {
          50: '#eff6ff',
          500: '#3b82f6',
          600: '#2563eb',
          700: '#1d4ed8',
        },
        secondary: {
          500: '#6b7280',
          600: '#4b5563',
        },
      },
      fontFamily: {
        sans: ['Inter', 'sans-serif'],
      },
    },
  },
  plugins: [],
};
```

### RTL Support

```javascript
import rtlPlugin from 'stylis-plugin-rtl';
import { CacheProvider } from '@emotion/react';
import createCache from '@emotion/cache';

const cacheRtl = createCache({
  key: 'muirtl',
  stylisPlugins: [rtlPlugin],
});

export const RTLProvider = ({ children }) => (
  <CacheProvider value={cacheRtl}>
    {children}
  </CacheProvider>
);
```

---

## Real-Time Features (SignalR)

### SignalR Connection Setup

```javascript
import * as signalR from '@microsoft/signalr';

export const createSignalRConnection = (token) => {
  const connection = new signalR.HubConnectionBuilder()
    .withUrl(import.meta.env.VITE_SIGNALR_HUB_URL, {
      accessTokenFactory: () => token,
    })
    .withAutomaticReconnect()
    .build();
  
  return connection;
};
```

### useSignalR Hook

```javascript
import { useEffect } from 'react';
import { createSignalRConnection } from '@/services/signalRService';
import useAuthStore from '@/stores/authStore';

export const useSignalR = (onNotification) => {
  const { token } = useAuthStore();
  
  useEffect(() => {
    if (!token) return;
    
    const connection = createSignalRConnection(token);
    
    connection.on('ReceiveNotification', (notification) => {
      onNotification(notification);
    });
    
    connection.start();
    
    return () => {
      connection.stop();
    };
  }, [token, onNotification]);
};
```

---

## Performance Optimization

### Code Splitting & Lazy Loading

```javascript
// Router.jsx
const DoctorDashboard = lazy(() => 
  import('@/features/doctor/pages/DoctorDashboard')
);

const PatientSearchPage = lazy(() => 
  import('@/features/patient/pages/SearchDoctorsPage')
);
```

### Image Optimization

- **Lazy loading**: Images load only when visible
- **WebP format**: Modern image format for better compression
- **Responsive images**: Different sizes for different screen sizes

### Bundle Size Optimization

- **Tree shaking**: Remove unused code
- **Code splitting**: Split code into smaller chunks
- **Dynamic imports**: Load code on demand

### Performance Metrics

- **First Contentful Paint (FCP)**: < 1.5s
- **Largest Contentful Paint (LCP)**: < 2.5s
- **Time to Interactive (TTI)**: < 3.5s
- **Bundle Size**: < 500KB (gzipped)

---

## Testing

### Unit Testing (Vitest)

```bash
npm run test
```

### Component Testing Example

```javascript
import { render, screen } from '@testing-library/react';
import { Button } from '@/components/common/Button';

describe('Button Component', () => {
  it('renders correctly', () => {
    render(<Button>Click me</Button>);
    expect(screen.getByText('Click me')).toBeInTheDocument();
  });
  
  it('handles click events', () => {
    const handleClick = vi.fn();
    render(<Button onClick={handleClick}>Click me</Button>);
    screen.getByText('Click me').click();
    expect(handleClick).toHaveBeenCalled();
  });
});
```

---

## Deployment

### Vercel Deployment

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel
```

### Netlify Deployment

```bash
# Build
npm run build

# Deploy dist folder
netlify deploy --prod --dir=dist
```

### Docker Deployment

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build
EXPOSE 5173
CMD ["npm", "run", "preview"]
```

---

## Best Practices

### Code Style

- **ESLint**: Enforce code quality rules
- **Prettier**: Consistent code formatting
- **Naming Conventions**: camelCase for variables, PascalCase for components

### Component Structure

```javascript
// 1. Imports
import React, { useState, useEffect } from 'react';
import PropTypes from 'prop-types';

// 2. Component
export const MyComponent = ({ prop1, prop2 }) => {
  // 3. State
  const [state, setState] = useState(null);
  
  // 4. Effects
  useEffect(() => {
    // Effect logic
  }, []);
  
  // 5. Handlers
  const handleClick = () => {
    // Handler logic
  };
  
  // 6. Render
  return (
    <div>
      {/* JSX */}
    </div>
  );
};

// 7. PropTypes
MyComponent.propTypes = {
  prop1: PropTypes.string.isRequired,
  prop2: PropTypes.number,
};
```

### Performance Tips

- Use `React.memo()` for expensive components
- Use `useMemo()` and `useCallback()` to avoid unnecessary re-renders
- Implement virtual scrolling for long lists
- Optimize images and assets

---

## Contributing

We welcome contributions! Please follow these guidelines:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Commit Message Format

```
type(scope): subject

body

footer
```

**Types**: feat, fix, docs, style, refactor, test, chore

---

## License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

---

**Developed with ❤️ for DEPI Graduation Project 2025**
