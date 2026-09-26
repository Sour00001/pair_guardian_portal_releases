<div align="center">

# PAIR Guardian Portal
### Parent Authentication & Identification RFID — Guardian Portal

**An enterprise-grade, responsive Progressive Web Application (PWA) designed for parents and guardians to monitor real-time student school attendance, track campus drop-offs and pick-ups, inspect attendance trends, and manage RFID card lifecycles.**

**Developed & Maintained by [Curt Jasper B. Agbulos](https://github.com/Sour00001)**

[![Author](https://img.shields.io/badge/Author-Curt_Jasper_B._Agbulos-purple?style=flat-square&logo=github)](https://github.com/Sour00001)
[![Current Version](https://img.shields.io/badge/Version-v2.4-blue?style=flat-square&logo=git)](https://github.com/Sour00001/Pair-Guardian-Portal)
[![Release Date](https://img.shields.io/badge/Release_Date-September_25,_2026-green?style=flat-square)](https://github.com/Sour00001/Pair-Guardian-Portal)
[![Platform](https://img.shields.io/badge/Platform-Web_SPA_/_PWA-orange?style=flat-square)](https://pair-guardian-portal.vercel.app)
[![Access](https://img.shields.io/badge/Access-Authorized_Institutional_Use-lightgrey?style=flat-square)](#access-and-support)
[![Frontend Stack](https://img.shields.io/badge/Frontend-React_19_+_TypeScript_+_Vite-61DAFB?style=flat-square&logo=react)](https://react.dev/)
[![Backend Stack](https://img.shields.io/badge/Backend-Node.js_+_Express_+_MongoDB-339933?style=flat-square&logo=node.js)](https://nodejs.org/)

---

[Overview](#project-overview) • [Academic Purpose](#academic-purpose) • [Key Features](#key-features) • [System Requirements](#system-requirements) • [Access & Deployment](#access-and-deployment) • [Installation](#installation--local-setup) • [Environment Config](#environment-configuration) • [User Roles](#user-roles) • [Updates](#updates--version-history) • [Security](#privacy-and-security) • [Credits & Acknowledgments](#credits--acknowledgments) • [Documentation Reference](#documentation-reference)

</div>

---

## Project Overview

The **PAIR Guardian Portal** (*Parent Authentication & Identification RFID*) is an official web portal and mobile-friendly Progressive Web App (PWA) created and engineered by **Curt Jasper B. Agbulos** ([@Sour00001](https://github.com/Sour00001)). It provides parents, guardians, and school administrators with reliable, real-time visibility into student campus attendance.

Educational institutions face important responsibilities regarding student perimeter safety. The PAIR Guardian Portal connects directly to the school's central database, displaying real-time entry and exit logs captured by on-campus hardware RFID scanners.

### Core Problems Addressed
- **Campus Perimeter Uncertainty**: Instant, timestamped confirmation of student arrivals (`TIME_IN`) and departures (`TIME_OUT`).
- **Proxy Pickup Verification**: Differentiates between primary guardian attendance, authorized family/proxy pickups (`Proxy` badge), and administrative checkouts.
- **Hardware Badge Incident Management**: Enables guardians to report lost or damaged physical RFID cards directly from mobile devices, flagging the credentials in real time.
- **Digital Inclusion & Accessibility**: Delivers comprehensive accessibility controls including multi-language support (English, Filipino, Spanish, Chinese, Thai, Japanese), OpenDyslexic typography, 4 colorblind filters, high-contrast modes, and 13 customizable visual themes.

---

## Academic Purpose

This project was developed in partial fulfillment of the requirements for the **System Integration** course. It demonstrates the technical integration of:
- Edge hardware RFID badge scanning and timestamped logging
- Centralized NoSQL database synchronization (MongoDB Atlas)
- Secure, token-based authentication and role-based access control (JWT)
- Automated transactional email communication (Brevo SMTP for OTP password recovery)
- Modern web engineering practices (React 19, TypeScript, TanStack Query, Vite PWA)
- Universal accessibility (WCAG-aligned contrast calculations, dyspraxia/dyslexia tooling, localization)

> [!NOTE]
> This software is developed for **academic demonstration and authorized institutional use**. Application source code, operational database instances, and credentials remain private.

---

## System Ecosystem Architecture

The PAIR platform operates as an integrated two-part ecosystem:

```text
 ┌─────────────────────────────────────────────────────────┐
 │               School Campus Gate / Kiosks               │
 │  • Physical RFID Readers & Scanners                     │
 │  • PAIR Desktop / Kiosk Engine (redevsk/pair_releases)  │
 └────────────────────────────┬────────────────────────────┘
                              │
                              ▼ Writes Attendance Events
 ┌─────────────────────────────────────────────────────────┐
 │               PAIR Cloud Infrastructure                 │
 │  • MongoDB Atlas (Attendance Logs, Students, Guardians) │
 │  • Express REST API (Vercel Serverless Functions)       │
 │  • Brevo SMTP Service (Transactional OTPs)              │
 └────────────────────────────┬────────────────────────────┘
                              │
                              ▼ Reads & Manages
 ┌─────────────────────────────────────────────────────────┐
 │                  PAIR Guardian Portal                   │
 │  • Mobile-First Progressive Web App (PWA)               │
 │  • Responsive Desktop & Tablet Web Portal               │
 │  • Parent Attendance Tracking & RFID Tag Reporting      │
 └─────────────────────────────────────────────────────────┘
```

1. **[PAIR System Releases](https://github.com/redevsk/pair_releases)** (*Companion Repository*): Desktop gate-scanning engine and administrative software deployed on physical campus kiosks to capture RFID card scans.
2. **[PAIR Guardian Portal](https://github.com/Sour00001/Pair-Guardian-Portal)** (*This Repository*): The guardian-facing web application and installable PWA for monitoring attendance, viewing analytics, managing accounts, and reporting RFID card issues.

---

## Key Features

### 1. Real-Time Attendance & Interaction Log
- **Intelligent Log Pairing**: Automatically groups individual hardware `TIME_IN` and `TIME_OUT` events into unified, daily chronological attendance cards for each student.
- **Proxy Attribution Badging**: Clearly marks whether a student was accompanied by their primary guardian, an authorized family member, an administrative proxy (`Proxy` badge), or processed via automated system checkout (`System (Auto)`).
- **Search & Filtering**: Search attendance logs by student name or guardian name, filter by specific date ranges, and navigate via configurable table pagination (20 or 50 items per page).

### 2. Attendance Analytics & Trends
- **Visual Activity Trends**: Interactive SVG line charts visualizing student arrival and departure patterns across weekly, monthly, yearly, or custom date scopes.
- **Peak Traffic Breakdown**: Visual display of the top 6 busiest school gate hours with hover tooltips and dynamic hourly metrics.
- **Guardian Engagement Distribution**: Bar charts showing individual guardian drop-off and pick-up frequency.

### 3. RFID Lifecycle Management
- **Instant Incident Reporting**: Report lost or damaged physical RFID cards directly from mobile or desktop browsers.
- **Batch Processing**: Select single or multiple linked children, apply incident notes (e.g., *"Lost during commute"*), and submit status updates in one request.
- **Live Status Tracking**: Displays real-time tag states (`Active`, `Suspended`, `Lost`, `Damaged`) linked to student profiles.

### 4. Announcements & Campus Advisories
- **Interactive Home Bulletin**: Rotating carousel highlighting campus news, emergency advisories, and school schedule changes.
- **Touch & Motion Friendly**: Full swipe navigation on mobile devices with automatic rotation pause on hover or tap.

### 5. Accessibility & Personalization Suite
- **Multi-Language Support**: Fully localized in **6 languages**: English, Filipino (Tagalog), Spanish (Español), Chinese (简体中文), Thai (ไทย), and Japanese (日本語).
- **Curated Reading Typography**: Over 40 selectable font families, including specialized **OpenDyslexic** typography with adjustable word spacing.
- **Colorblind & High-Contrast Modes**: Built-in SVG matrix filters for Protanopia, Deuteranopia, Tritanopia, Grayscale, and High-Contrast visibility.
- **Global Visual Themes**: 13 atmospheric themes (Christmas, Ocean, Nature, Midnight, Valentine's, Halloween, etc.) with floating background motifs and persistent user preference storage.
- **2D Color Spectrum Picker**: Custom accent color selection with real-time WCAG contrast ratio calculations.
- **UI Softness Slider**: Granular control over interface border radius and card roundness.

### 6. Progressive Web App (PWA) Readiness
- **Installable Experience**: Add to Home Screen on iOS, Android, macOS, and Windows.
- **Offline Awareness**: Offline status indicators with cached data persistence powered by TanStack Query Sync Storage Persister.

### 7. Auditable Document Exports
- **Vector PDF Attendance Reports**: Formatted, branded PDF reports generated directly in the client browser using jsPDF and AutoTable.
- **CSV Data Export**: Excel-compatible UTF-8 BOM CSV exports for personal record keeping.

---

## Technology Stack

### Frontend
| Component | Technology | Version | Description |
| :--- | :--- | :--- | :--- |
| **UI Library** | React | `19.2.3` | Modern declarative component architecture |
| **Language** | TypeScript | `~5.8.2` | Static type safety and strict schema alignment |
| **Build System** | Vite | `^6.2.0` | High-speed build tool and hot module replacement |
| **Styling** | Tailwind CSS | `^3.4.19` | Utility-first styling with dynamic CSS variables |
| **Data Fetching** | TanStack React Query | `^5.96.2` | Server state management, auto-caching, and query sync |
| **Query Persistence** | React Query Persist Client | `^5.96.2` | Local storage state persistence |
| **Iconography** | Lucide React | `^0.562.0` | Comprehensive vector UI icon library |
| **PDF Generation** | jsPDF + AutoTable | `^4.1.0` / `^5.0.7` | Client-side vector PDF document compilation |
| **PWA Service Worker** | Vite Plugin PWA + Workbox | `^1.2.0` / `^7.4.0` | Service worker lifecycle, caching, and installability |

### Backend & API
| Component | Technology | Version | Description |
| :--- | :--- | :--- | :--- |
| **Runtime** | Node.js | `>=18.x` | JavaScript server-side runtime |
| **Web Framework** | Express | `^4.19.2` | RESTful routing and middleware engine |
| **Database ODM** | Mongoose | `^8.0.0` | Schema validation and MongoDB query abstraction |
| **Database** | MongoDB Atlas | `>=6.0` | Cloud document database |
| **Security Headers** | Helmet | `^8.1.0` | Content Security Policy and HTTP protection headers |
| **Sanitization** | express-mongo-sanitize | `^2.2.0` | NoSQL query injection prevention |
| **Rate Limiting** | express-rate-limit + rate-limit-mongo | `^8.3.2` / `^2.3.2` | MongoDB-backed distributed rate limiting |
| **Authentication** | jsonwebtoken | `^9.0.3` | Cryptographic JWT token signing and verification |
| **Password Hashing** | bcryptjs | `^3.0.3` | Salted credential hashing |
| **Email Transport** | Nodemailer | `^9.0.3` | SMTP integration for Brevo transactional OTP delivery |

---

## Current Release

| Property | Details |
| :--- | :--- |
| **Current Version** | **v2.4** |
| **Release Status** | Active / Production |
| **Release Date** | September 25, 2026 |
| **Primary Theme** | Global Visual Themes & Atmospheric Experience |
| **Latest Highlights** | 13 global themes, Japanese language localization, interactive avatar image viewer, 2D color spectrum picker, 40+ reading fonts. |

---

## Access and Deployment

The PAIR Guardian Portal is delivered as a secure web application:

- **Authorized Web Access**: Users access the portal through the institution's designated URL deployment:
  ```text
  https://pair-guardian-portal.vercel.app
  ```
- **Mobile Installation (PWA)**: When loaded on mobile Safari or Chromium browsers, users can select **"Add to Home Screen"** or **"Install App"** for a native app experience.
- **Account Provisioning**: Guardian accounts and student linkage are provisioned by authorized school administrators during student enrollment. Self-registration is restricted to authorized credentials verified by the institution.

---

## User Roles

| Role | Scope & Permissions |
| :--- | :--- |
| **Guardian / Parent** | View real-time attendance logs for linked students, inspect attendance analytics, report lost or damaged RFID tags, configure accessibility and UI preferences, export PDF/CSV logs, and manage account security (password/OTP recovery). |
| **Student / Minor** | System entity represented by student profile and hardware RFID badge UID. Student data is managed by linked guardians and administrative personnel. |
| **Administrator / Staff** | Manages student-guardian bindings, processes RFID badge assignments and replacements at on-campus desktop stations ([redevsk/pair_releases](https://github.com/redevsk/pair_releases)), and oversees campus gate operations. |

---

## Installation & Local Setup

To run the application locally for evaluation or development:

### 1. Prerequisites
- **Node.js**: `v18.0.0` or higher
- **npm**: `v9.0.0` or higher
- **MongoDB**: Local MongoDB server or MongoDB Atlas cluster connection URI

### 2. Clone the Repository
```bash
git clone https://github.com/Sour00001/Pair-Guardian-Portal.git
cd Pair-Guardian-Portal
```

### 3. Install Dependencies
Install frontend and backend dependencies:
```bash
# Install frontend dependencies
npm install

# Install backend dependencies
cd server
npm install
cd ..
```

### 4. Configure Environment Variables
Create `.env` files in the root and `server/` directories as detailed in [Environment Configuration](#environment-configuration).

### 5. Launch the Development Environment
Run both frontend and backend concurrently using the configured start script:
```bash
npm start
```
- **Frontend SPA**: `http://localhost:5173`
- **Backend API Server**: `http://localhost:5000`

---

## Environment Configuration

> [!WARNING]
> Never commit actual passwords, private API keys, database credentials, or secret tokens to source control. Use the placeholders below when setting up local `.env` files.

### Frontend (`.env` in root)
```env
# URL pointing to the backend Express server
VITE_API_URL=http://localhost:5000
```

### Backend (`server/.env`)
```env
# Server Port
PORT=5000

# Environment Mode (development | production)
NODE_ENV=development

# MongoDB Connection String
MONGODB_URI=mongodb+srv://<username>:<password>@<cluster-url>/pair_db?retryWrites=true&w=majority

# JWT Token Secret & Lifespan
JWT_SECRET=your_secure_jwt_secret_key_here
JWT_EXPIRES_IN=3h

# Brevo SMTP Configuration for OTP Delivery
EMAIL_HOST=smtp-relay.brevo.com
EMAIL_PORT=587
EMAIL_USER=your_brevo_smtp_login_email@domain.com
EMAIL_PASS=your_brevo_smtp_master_key_here
EMAIL_FROM="PAIR Portal" <noreply@yourdomain.com>

# Allowed Frontend Origin for CORS
FRONTEND_URL=http://localhost:5173
```

---

## System Requirements

### Software & Environment
- **Node.js Runtime**: `>= 18.0.0` (LTS recommended)
- **Package Manager**: npm `>= 9.0.0`
- **Supported Browsers**: Chrome 90+, Firefox 88+, Safari 14+, Edge 90+, Samsung Internet
- **Operating Systems**: Windows 10/11, macOS 11+, Linux, iOS 14+, Android 8+
- **Network**: Active broadband connection required for cloud database synchronization and transactional OTP emails

---

## Updates & Version History

The application includes an in-app **Updates Page** accessible from the portal navigation, providing a detailed breakdown of features introduced across each release:

| Version | Release Date | Summary |
| :--- | :--- | :--- |
| **v2.4** | Sep 25, 2026 | Global Visual Themes & Atmospheric Experience (13 themes, animated motifs). |
| **v2.3** | Sep 25, 2026 | Japanese Language Support & Full-Screen Image Viewer Modal. |
| **v2.2** | Sep 24, 2026 | Interactive System Overview & Edge Hardware Specification Guide. |
| **v2.1** | Sep 23, 2026 | 2D Hue-Saturation Spectrum Color Picker & Dual Wheel Modes. |
| **v2.0** | Sep 22, 2026 | Smooth Card Filtering, Instant Search, and Reduced Motion Enhancements. |
| **v1.4** | Sep 21, 2026 | 43 Custom Reading Fonts, OpenDyslexic Mode, and UI Softness Sliders. |
| **v1.3** | Sep 10, 2026 | Multi-Language Support (English, Filipino, Spanish, Chinese, Thai). |
| **v1.2** | Jul 22, 2026 | School Announcements Bulletin Carousel on Home Page. |
| **v1.1** | May 02, 2026 | Accessibility Themes, Colorblind Filters, and PDF/CSV Report Downloads. |
| **v1.0** | Mar 06, 2026 | Initial Web & PWA Launch for Guardian Real-Time Attendance Monitoring. |

---

## Privacy and Security

The PAIR Guardian Portal adheres to core data protection and security practices:

- **Authentication & Sessions**: Signed JSON Web Tokens (JWT) with 3-hour expiration and 30-minute idle session timeout.
- **Brute-Force Defense**: Strict rate limiting on authentication and OTP recovery endpoints (5 attempts per 15 minutes) backed by MongoDB distributed stores.
- **Input Sanitization**: Automatic stripping of MongoDB operator injection patterns via `express-mongo-sanitize`.
- **HTTP Header Hardening**: Comprehensive Content Security Policy (CSP), anti-clickjacking, and MIME-sniffing protections via Helmet.
- **Data Protection Hygiene**: Application configuration files (`.env`), database backups, server logs, and personal student records are strictly excluded from source control via `.gitignore`.

---

## Access and Support

- **Account Access**: Guardians requiring portal access or account recovery must contact their school's administrative office.
- **Technical Support**: Technical queries regarding campus kiosk hardware, RFID registration, or portal operation should be directed to the designated institutional system administrator.
- **Private Software Notice**: This application is not intended for unauthorized public redistribution or third-party commercial deployment.

## Credits & Acknowledgments

### Project Authors & Core Team
- **Lead Developer & System Architect**: **Curt Jasper B. Agbulos** ([@Sour00001](https://github.com/Sour00001))
  - Full-stack web application development, responsive PWA design, user interface architecture, accessibility & personalization suite, dynamic theming engine, multi-language localization, and backend database integrations.
- **Collaborator & Ecosystem Integration**: **redevsk** ([@redevsk](https://github.com/redevsk))
  - Hardware gate-scanning engine integration, campus announcement carousel synchronization, and desktop kiosk release packaging ([pair_releases](https://github.com/redevsk/pair_releases)).

### Academic & Institutional Recognition
- **Academic Program**: Developed in partial fulfillment of the academic requirements for the **System Integration** course.
- **Institutional Partner**: Designed for school safety monitoring and demonstration in collaboration with **Leap High Learning Center**.

### Open-Source Technologies & Frameworks
Special thanks to the open-source libraries and platforms powering this system:
- [React](https://react.dev/) & [TypeScript](https://www.typescriptlang.org/) — Declarative UI and strict type safety
- [Vite](https://vitejs.dev/) & [Vite Plugin PWA](https://vite-pwa-org.netlify.app/) — Build tooling, HMR, and Progressive Web App engine
- [Tailwind CSS](https://tailwindcss.com/) — Utility-first responsive design framework
- [TanStack Query](https://tanstack.com/) — Client-side state synchronization, query caching, and offline persister
- [Lucide Icons](https://lucide.dev/) — Vector iconography
- [jsPDF & AutoTable](https://github.com/parallax/jsPDF) — Client-side vector PDF document compilation
- [Node.js](https://nodejs.org/) & [Express](https://expressjs.com/) — RESTful server architecture and middleware
- [MongoDB Atlas](https://www.mongodb.com/) & [Mongoose](https://mongoosejs.com/) — Cloud database storage and schema modeling
- [Brevo](https://www.brevo.com/) — SMTP transactional email gateway for OTP delivery
- [Vercel](https://vercel.com/) — Serverless cloud hosting and SPA distribution

---

## Documentation Reference

The distribution and release documentation structure for this project was inspired by the professional release formatting of:

- **[PAIR Releases Repository](https://github.com/redevsk/pair_releases)** (`redevsk/pair_releases`)

*Note: This reference link provides attribution for documentation styling inspiration. The PAIR Guardian Portal is an independent web application component of the PAIR system ecosystem.*

---

<div align="center">
  <sub>PAIR Guardian Portal • Parent Authentication & Identification RFID • Developed by Curt Jasper B. Agbulos</sub>
</div>
