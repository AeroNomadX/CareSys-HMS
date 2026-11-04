<div align="center">

# 🏥 CareSys - Modern Hospital Management System & Database Analytics

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38BDF8?style=flat-square&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)](https://www.mysql.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](https://opensource.org/licenses/MIT)

*An integrated web-based executive dashboard and normalized relational database system for managing outpatient consultations, inpatient ward bed occupancy, physician schedules, and real-time clinical data exports.*

</div>

---

## 🚀 Interactive Quick Menu
*Click any section below to expand and explore!* 👇

<details>
<summary><b>📋 Project Overview & Objectives</b> (Click to open)</summary>

**CareSys HMS** is designed to eliminate operational bottlenecks in small to medium-sized healthcare facilities by replacing fragmented paper records and manual spreadsheets with a unified relational architecture. 
- **Normalized Schema:** Enforces Third Normal Form (3NF) relational integrity across patients, doctors, wards, and admissions.
- **Real-Time Automations:** Dynamic bed allocation state toggling (`Available` vs `Occupied`) via database triggers and UI event listeners.
- **Multi-Format Reporting:** Instant client-side compilation and download of patient directories into CSV, Microsoft Excel (`.xlsx`), and JSON formats.

</details>

<details>
<summary><b>📊 Core Features & Dashboard Modules</b> (Click to open)</summary>

1. **Live KPI Metric Cards:** Instant executive overview tracking total registered patients, today's OPD visits, active inpatient admissions, and available ward bed counts.
2. **Patient Directory & Advanced Filtering:** Searchable patient records by name or phone with multi-field dropdown filters for gender and blood group.
3. **Ward & Bed Occupancy Board:** Multi-ward inventory tracking (General Ward, Private Rooms, ICU) with live status indicators and one-click patient discharges.
4. **Outpatient (OPD) Ticketing:** Quick consultation registration linking patients to specialized doctors with automatic fee tariff resolution.
5. **System Audit Activity Log:** Terminal-style live activity feed recording all clinical operations and user actions with precise timestamping.

</details>

<details>
<summary><b>🛠️ Tech Stack & Architecture</b> (Click to open)</summary>

- **Frontend Interface:** HTML5, Tailwind CSS (via CDN), Font Awesome 6.4, Google Fonts (Inter)
- **Application Logic:** JavaScript (ES6+) reactive state management engine
- **Data Exporters:** SheetJS (`xlsx.full.min.js`) for binary Excel workbook generation
- **Database Layer:** ANSI SQL compliant (MySQL / PostgreSQL compatible)

</details>

---

## 🗄️ Database Schema & Entities

The relational database comprises 6 normalized core entities:
- **`Patients`**: Stores demographic records, unique IDs, contact details, age, gender, and blood group tags.
- **`Doctors`**: Maintains physician profiles, medical specializations, and standard consultation fee tariffs.
- **`Wards`**: Defines hospital ward divisions (General Ward, Private Rooms, ICU) and daily room tariffs.
- **`Beds`**: Tracks individual bed codes linked to parent wards with real-time occupancy status flags.
- **`OpdVisits`**: Logs outpatient consultations linking patients to consulting physicians, symptoms, diagnosis notes, and fee totals.
- **`Admissions`**: Manages inpatient stay timelines, bed allocations, admission timestamps, reasons, and discharge logs.

---

## ⚙️ Quick Start & Installation

### Prerequisites
- Any modern web browser (Google Chrome, Microsoft Edge, Firefox)
- An active internet connection (to load Tailwind CSS, SheetJS, Font Awesome, and Google Fonts via CDN)
- Optional: A local MySQL or PostgreSQL database server to execute full relational SQL scripts.

### Running the Web Portal
1. Clone or download this repository to your local machine.
2. Open `hospital_management_system.html` directly in your web browser.
3. Use the dashboard to register OPD visits, admit/discharge patients, filter directories, and test data exports!

---

## 💻 SQL Database DDL Setup

To initialize the relational database schema on MySQL or PostgreSQL, you can execute the core DDL script:

```sql
CREATE DATABASE IF NOT EXISTS CaresysHMS;
USE CaresysHMS;

CREATE TABLE Patients (
    patient_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    gender VARCHAR(10) NOT NULL CHECK (gender IN ('Male', 'Female', 'Other')),
    age INT NOT NULL CHECK (age > 0 AND age < 120),
    phone VARCHAR(15) NOT NULL UNIQUE,
    blood_group VARCHAR(5) NOT NULL,
    address VARCHAR(255)
);

CREATE TABLE Doctors (
    doctor_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    specialization VARCHAR(100) NOT NULL,
    consultation_fee DECIMAL(10,2) NOT NULL CHECK (consultation_fee >= 0)
);

CREATE TABLE Wards (
    ward_id INT AUTO_INCREMENT PRIMARY KEY,
    ward_name VARCHAR(50) NOT NULL UNIQUE,
    daily_rate DECIMAL(10,2) NOT NULL CHECK (daily_rate
