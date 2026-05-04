# 🏫 Educare BD — AI-Powered School Management System

**Software Blueprint & Project Specification**
Version 1.0 | April 2026

---

## 1. Project Overview

Educare BD is an AI-powered School Management System that integrates face recognition, automated attendance tracking, real-time parent notifications, and complete school administration — all within a single unified platform.

| **Field** | **Details** |
|---|---|
| Project Name | Educare BD - School Management System |
| Target Users | 700–800 Students + Teachers per school |
| Platform | Mobile App + Web App + CCTV Integration |
| Core Technology | AI Face Recognition + Machine Learning |
| Attendance Window | 7:00 AM – 11:00 AM (Daily) |
| Notification Deadline | By 12:00 PM |

---

## 2. System Architecture

### 2.1 Hardware Layer (Physical Setup)

The following hardware will be installed at the school entrance:

- 2× High-Resolution Cameras (one on each side of the gate)
  - High frame rate & wide-angle lens
  - Night vision capability
  - Weather-proof enclosure
- DVR (Digital Video Recorder) — for local footage storage
- Local Processing Unit — for on-device AI inference
- Internet Connection — for cloud synchronization

### 2.2 Software Architecture (3-Layer)

| **Layer** | **Component** | **Responsibility** |
|---|---|---|
| Frontend | Mobile App + Web App | User interaction & data visualization |
| Backend | API Server (Node.js / Python) | Business logic & data processing |
| AI Engine | Face Recognition + ML Model | Face detection & attendance automation |
| Database | PostgreSQL + Redis | Persistent & cached data storage |
| Notification | SMS Gateway + Voice Call API | Real-time parent alerts |

---

## 3. Core Feature: AI Attendance System

### 3.1 Daily Attendance Flow

The system remains active from 7:00 AM to 11:00 AM every school day:

| **Step** | **Time** | **Action** |
|---|---|---|
| Step 1 | 7:00 AM | Camera activates, AI model initializes |
| Step 2 | 7:00–11:00 AM | Faces detected at gate and matched against database |
| Step 3 | Real-time | Attendance sheet auto-updates (Present / Absent) |
| Step 4 | 11:00 AM | Attendance window closes, final report generated |
| Step 5 | 11:00 AM–12:00 PM | Absent list compiled, parent contacts retrieved |
| Step 6 | 12:00 PM | SMS + Voice Call notifications dispatched |

### 3.2 Machine Learning Capabilities

- Continuously collects data and refines the recognition model
- Improves accuracy under low-light conditions and varying angles
- Reduces false positives and negatives through ongoing learning
- Auto-retrains when new student faces are added to the database

### 3.3 Performance Requirements

- Handles concurrent load of 700–800 users without degradation
- Zero crash tolerance — load balancing enforced at all times
- Face recognition speed: **< 2 seconds per person**
- System uptime: **99.5% guaranteed**

---

## 4. Notification System

### 4.1 Absent Student Notification Flow

Parents of absent students are notified by 12:00 PM through the following process:

1. System retrieves parent/guardian contact from the database
2. An **SMS alert** is sent immediately
3. A **recorded voice call** follows (in Bengali): *"Your child did not attend school today..."*
4. All call logs are recorded — status, time, and attempt count
5. Follow-up notifications continue for up to **3 consecutive absent days**

### 4.2 Notification Dashboard

Admins can monitor the following in real time:

- Who has been contacted
- Whether the call was successfully connected
- How many consecutive days the student has been absent
- Total absence count per student

---

## 5. App & Web Platform

### 5.1 Platform Overview

| **Platform** | **Users** | **Access Level** |
|---|---|---|
| Mobile App | Students, Parents, Teachers | Role-based |
| Web App | Admin, Teachers | Full access |
| Admin Panel | School Administrator | Super access |

### 5.2 Login System

- **Student / Parent Login** — via Student ID or phone number; restricted to personal data only
- **Teacher Login** — via Teacher ID and password; can update class-level information
- **Admin Login** — full access to all data and system controls

### 5.3 Permission Matrix

| **Feature** | **Student / Parent** | **Teacher** | **Admin** |
|---|---|---|---|
| View Attendance | ✅ Own only | ✅ Class-level | ✅ All |
| Modify Data | ❌ | ✅ Limited | ✅ All |
| Create Exam Papers | ❌ | ✅ | ✅ |
| Process Salaries | ❌ | ❌ | ✅ |
| Post Notices | ❌ | ❌ | ✅ |
| Call System Access | ❌ | ❌ | ✅ Automated |

---

## 6. Feature List

### 6.1 V1.0 — Initial Release

| **#** | **Feature** | **Description** | **Priority** |
|---|---|---|---|
| 1 | AI Attendance | Automated face recognition-based attendance | 🔴 High |
| 2 | Absent Call System | Voice call + SMS alerts for parents | 🔴 High |
| 3 | Exam Paper Generator | Auto-generates monthly exam question papers | 🟡 Medium |
| 4 | Online Salary Payment | Teacher salary via bKash / mobile banking | 🟡 Medium |
| 5 | Tiffin Request | Parents can order tiffin through the app | 🟢 Low |
| 6 | Book List | View & download class-wise book lists | 🟢 Low |
| 7 | Notice Board | Download official school notices | 🟡 Medium |
| 8 | Suggestion Papers | Purchase suggestion papers in-app | 🟢 Low |
| 9 | Teacher Directory | Browse teacher profiles and contact info | 🟢 Low |
| 10 | Leave Application | Submit leave requests digitally | 🟡 Medium |

### 6.2 V2.0 — Planned Features

- Online Class Integration (Zoom / Google Meet)
- Result Management System
- Library Management
- Student Transport Tracking
- Multi-School Admin Panel
- Analytics & Reporting Dashboard
- Parent-Teacher Meeting Scheduler

---

## 7. Database Schema

| **Table** | **Fields** |
|---|---|
| `students` | id, name, photo, class, parent_contact, face_encoding |
| `teachers` | id, name, subject, phone, salary_info |
| `attendance` | student_id, date, status, time, camera_id |
| `calls_log` | student_id, parent_phone, call_status, date, attempt_count |
| `payments` | teacher_id, amount, method, date, status |
| `notices` | title, content, file_url, date, class_target |
| `exam_papers` | subject, class, questions, date, created_by |

---

## 8. Technology Stack

| **Category** | **Technology** | **Reason** |
|---|---|---|
| AI / Face Recognition | Python + DeepFace / InsightFace | High accuracy & speed |
| Machine Learning | TensorFlow / PyTorch | Model training & optimization |
| Backend API | Node.js + Express / FastAPI | High-performance REST API |
| Database | PostgreSQL + Redis (cache) | Reliable & fast data handling |
| Mobile App | React Native | Cross-platform (Android + iOS) |
| Web App | React.js | Modern, responsive UI |
| SMS Gateway | Twilio / SSL Wireless | Reliable SMS delivery |
| Voice Call | Twilio Programmable Voice | Recorded call automation |
| Payment | bKash API / SSLCOMMERZ | Bangladesh-compatible payment |
| Hosting | AWS / DigitalOcean | Scalable cloud infrastructure |

---

## 9. Development Roadmap

| **Phase** | **Timeline** | **Deliverables** |
|---|---|---|
| Phase 1 | Month 1–2 | Database design, Face recognition model, Core API |
| Phase 2 | Month 3–4 | Attendance system, Camera integration, Admin dashboard |
| Phase 3 | Month 5–6 | Mobile App, Web App, SMS & Voice Call system |
| Phase 4 | Month 7–8 | Payment system, Exam paper generator, Notice board |
| Phase 5 | Month 9 | QA testing, Bug fixes, Performance optimization |
| Phase 6 | Month 10 | Pilot launch with 1 school |
| Phase 7 | Month 11–12 | Full launch & multi-school scaling |

---

## 10. Technical Constraints & Standards

- **Crash-proof architecture** — load balancing required for 700–800 concurrent users
- **Data security** — all facial recognition data stored with encrypted encoding
- **Offline mode** — attendance recorded locally when internet is unavailable; synced on reconnection
- **Automated backups** — daily database backup with recovery support
- **No manual input required** — attendance captured entirely via CCTV, no card or biometric device needed

---

*Educare BD — School Management System | Blueprint v1.0 | Confidential*
