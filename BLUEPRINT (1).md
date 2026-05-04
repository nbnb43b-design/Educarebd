# 🏫 Educare BD — School Management System

**Software Blueprint & Project Specification**
Version 1.0 | April 2026

---

## ১. Project Overview

এই software টি একটি AI-powered School Management System যেটি face recognition, automated attendance, parent notification, এবং school administration সব কিছু একটি platform-এ handle করবে।

| **বিষয়** | **বিবরণ** |
|---|---|
| Project Name | Educare BD - School Management System |
| Target Users | 700-800 জন Students + Teachers per school |
| Platform | Mobile App + Web App + CCTV Integration |
| Core Technology | AI Face Recognition + Machine Learning |
| Attendance Window | সকাল ৭:০০ - ১১:০০ (প্রতিদিন) |
| Notification Deadline | দুপুর ১২:০০ এর মধ্যে |

---

## ২. System Architecture

### ২.১ Hardware Layer (Physical Setup)

School gate-এ নিচের hardware গুলো থাকবে:

- ২টি High-Resolution Camera (gate-এর দুই পাশে)
- High frame rate এবং wide angle lens
- Night vision capability
- Weather-proof enclosure
- DVR (Digital Video Recorder) — footage store করার জন্য
- Local Processing Unit — AI inference চালানোর জন্য
- Internet Connection — cloud sync এর জন্য

### ২.২ Software Architecture (3-Layer)

| **Layer** | **Component** | **কাজ** |
|---|---|---|
| Frontend | Mobile App + Web App | Users দেখবে এবং interact করবে |
| Backend | API Server (Node.js/Python) | Business logic handle করবে |
| AI Engine | Face Recognition + ML Model | Face detect ও attendance নেবে |
| Database | PostgreSQL + Redis | সব data store হবে |
| Notification | SMS Gateway + Voice Call API | Parents কে জানাবে |

---

## ৩. Core Feature: AI Attendance System

### ৩.১ Daily Attendance Flow

প্রতিদিন সকাল ৭:০০ থেকে ১১:০০ পর্যন্ত system active থাকবে:

| **Step** | **সময়** | **কাজ** |
|---|---|---|
| Step 1 | ৭:০০ AM | Camera activate, AI model start |
| Step 2 | ৭:০০-১১:০০ | Gate দিয়ে প্রবেশের সময় face detect করে database match করবে |
| Step 3 | Real-time | Present/Absent auto-update হবে attendance sheet-এ |
| Step 4 | ১১:০০ AM | Attendance window close, final sheet generate |
| Step 5 | ১১:০০-১২:০০ | Absent list তৈরি, parent contact বের করা |
| Step 6 | ১২:০০ PM | SMS + Voice Call পাঠানো শুরু |

### ৩.২ Machine Learning এর কাজ

- সারাদিন data collect করবে এবং model refine করবে
- Low-light বা angle-এ face recognition accuracy বাড়াবে
- False positive/negative কমাতে continuously learn করবে
- Database-এ নতুন face add হলে auto-train হবে

### ৩.৩ Performance Requirements

- 700-800 জন member এর load handle করতে পারবে
- System crash হবে না — load balancing থাকবে
- Face recognition: < 2 seconds per person
- 99.5% uptime guarantee

---

## ৪. Notification System

### ৪.১ Absent হলে কী হবে

দুপুর ১২টার মধ্যে absent students-দের parents কে notify করা হবে:

- Database থেকে absent student-এর parent/guardian contact বের হবে
- প্রথমে SMS পাঠাবে
- তারপর Recorded Voice Call দেবে (আপনার নিজের voice recording)
- Call টি বাংলায় হবে: "আপনার সন্তান আজ school-এ আসেনি..."
- Database update হবে — call দেওয়া হয়েছে কিনা record থাকবে
- Maximum ৩ দিন পর্যন্ত এই process চলবে absent students-দের জন্য

### ৪.২ Dashboard এ দেখাবে

- কাকে call দেওয়া হয়েছে
- Call successfully connected হয়েছে কিনা
- কতদিন ধরে absent
- Total absent count per student

---

## ৫. App & Web Platform

### ৫.১ Platform Structure

| **Platform** | **কে ব্যবহার করবে** | **Access Level** |
|---|---|---|
| Mobile App | Students, Parents, Teachers | Role-based |
| Web App | Admin, Teachers | Full access |
| Admin Panel | School Admin | Super access |

### ৫.২ Login System

- **Student/Parent Login:** Student ID বা Phone number দিয়ে login, শুধু নিজের তথ্য দেখতে পারবে
- **Teacher Login:** Teacher ID এবং Password দিয়ে login, নিজের class-এর কিছু update করতে পারবে
- **Admin Login:** সব কিছু access এবং modify করতে পারবে

### ৫.৩ Permission Matrix

| **Feature** | **Student/Parent** | **Teacher** | **Admin** |
|---|---|---|---|
| Attendance দেখা | ✅ নিজেরটা | ✅ Class-এর | ✅ সব |
| Data modify করা | ❌ | ✅ Limited | ✅ সব |
| Exam paper বানানো | ❌ | ✅ | ✅ |
| Salary দেওয়া | ❌ | ❌ | ✅ |
| Notice দেওয়া | ❌ | ❌ | ✅ |
| Call system | ❌ | ❌ | ✅ Auto |

---

## ৬. সম্পূর্ণ Feature List

### ৬.১ Implemented Features (V1.0)

| **#** | **Feature** | **বিবরণ** | **Priority** |
|---|---|---|---|
| 1 | AI Attendance | Face recognition দিয়ে auto attendance | 🔴 High |
| 2 | Absent Call System | Parents কে voice call + SMS | 🔴 High |
| 3 | Exam Paper Generator | Monthly exam-এর question paper তৈরি | 🟡 Medium |
| 4 | Online Salary Payment | bKash/Mobile banking দিয়ে salary | 🟡 Medium |
| 5 | Tiffin Request | Parents app থেকে tiffin order | 🟢 Low |
| 6 | Book List | সব class-এর book list দেখা ও download | 🟢 Low |
| 7 | Notice Board | School notice download করা | 🟡 Medium |
| 8 | Suggestion Paper | Suggestion paper কিনতে পারবে app থেকে | 🟢 Low |
| 9 | Teacher Directory | সব teacher-এর details ও contact | 🟢 Low |
| 10 | Leave Application | School ছুটির আবেদন করা | 🟡 Medium |

### ৬.২ Future Features (V2.0)

- Online Class Integration (Zoom/Google Meet)
- Result Management System
- Library Management
- Transport Tracking
- Multi-school Admin Panel
- Analytics & Reporting Dashboard
- Parent-Teacher Meeting Scheduler

---

## ৭. Database Structure

| **Table Name** | **Data যা থাকবে** |
|---|---|
| students | ID, নাম, ছবি, class, parent contact, face_encoding |
| teachers | ID, নাম, subject, phone, salary info |
| attendance | student_id, date, status, time, camera_id |
| calls_log | student_id, parent_phone, call_status, date, attempt_count |
| payments | teacher_id, amount, method, date, status |
| notices | title, content, file_url, date, class_target |
| exam_papers | subject, class, questions, date, created_by |

---

## ৮. Technology Stack

| **Category** | **Technology** | **কারণ** |
|---|---|---|
| AI / Face Recognition | Python + DeepFace / InsightFace | Accurate ও fast |
| Machine Learning | TensorFlow / PyTorch | Model training এর জন্য |
| Backend API | Node.js + Express / FastAPI | High performance |
| Database | PostgreSQL + Redis (cache) | Reliable ও fast |
| Mobile App | React Native | Android + iOS একসাথে |
| Web App | React.js | Fast ও modern UI |
| SMS Gateway | Twilio / SSL Wireless | Reliable SMS |
| Voice Call | Twilio Programmable Voice | Recorded call |
| Payment | bKash API / SSLCOMMERZ | Bangladesh payment |
| Hosting | AWS / DigitalOcean | Scalable server |

---

## ৯. Development Phases (Roadmap)

| **Phase** | **সময়** | **কাজ** |
|---|---|---|
| Phase 1 | Month 1-2 | Database design, Face recognition model, Basic API |
| Phase 2 | Month 3-4 | Attendance system, Camera integration, Dashboard |
| Phase 3 | Month 5-6 | Mobile App, Web App, SMS/Call system |
| Phase 4 | Month 7-8 | Payment system, Exam paper, Notice board |
| Phase 5 | Month 9 | Testing, Bug fix, Performance optimization |
| Phase 6 | Month 10 | Pilot launch with 1 school |
| Phase 7 | Month 11-12 | Full launch, Scale to multiple schools |

---

## ১০. Important Notes

- System টি crash-proof করতে হবে — 700-800 জন একসাথে process করার সময় load balanced হতে হবে
- Face data সম্পূর্ণ secure রাখতে হবে — encrypted storage
- Internet না থাকলেও local-এ attendance নিতে পারবে, পরে sync হবে
- Regular backup — প্রতিদিন automatic database backup
- CCTV footage থেকে attendance নেওয়া হবে — কোনো card বা manual input লাগবে না

---

*Educare BD — School Management System Blueprint v1.0*
