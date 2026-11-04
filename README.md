CareSys - Modern Hospital Management System & Database Analytics
CareSys HMS is an integrated, single-page hospital management system and relational database dashboard designed to streamline outpatient (OPD) visits, inpatient (IPD) ward bed occupancy, physician scheduling, patient directories, and automated multi-format data exports.

Features
Live KPI Executive Dashboard: Real-time metrics tracking total registered patients, today's OPD consultations, active inpatient admissions, and available ward bed counts.

Patient Directory & Advanced Filtering: Searchable patient records by name or phone with multi-field filters for gender and blood group.

Ward & Bed Occupancy Board: Multi-ward inventory tracking (General Ward, Private Rooms, ICU) with live status toggling (Available vs Occupied) and one-click patient discharges.

Outpatient (OPD) Ticketing: Quick consultation registration linking patients to specialized doctors with automatic fee resolution.

Audit Activity Log: Terminal-style live activity feed tracking all system transactions and user actions with precise timestamps.

Multi-Format Data Exporters: Client-side compilation and instant download of patient records into CSV, native Microsoft Excel (.xlsx), and JSON formats.

Tech Stack
Frontend: HTML5, Tailwind CSS (CDN), Font Awesome 6.4, Google Fonts (Inter)

Logic & State: JavaScript (ES6+)

Exporters: SheetJS (xlsx.full.min.js)

Database Backend: ANSI SQL (MySQL / PostgreSQL compatible)

Database ER Schema & Entities
The relational database is normalized up to Third Normal Form (3NF) across 6 core entities:

Patients: Demographics, contact numbers, age, gender, and blood group.

Doctors: Physician profiles, specializations, and consultation fee tariffs.

Wards: Hospital ward categories and daily room stay rates.

Beds: Individual bed tracking linked to wards with occupancy status flags.

OpdVisits: Outpatient consultation logs linking patients, doctors, symptoms, diagnosis, and fees.

Admissions: Inpatient stay logs tracking patient bed assignments, admission timestamps, reasons, and discharge dates.

Getting Started
Prerequisites
Any modern web browser (Google Chrome, Microsoft Edge, Mozilla Firefox)

An active internet connection (to load Tailwind CSS, SheetJS, Font Awesome, and Google Fonts via CDN)

Optional: MySQL / PostgreSQL server for full backend relational deployment.

Running the Web Portal
Clone or download the repository files to your local machine.

Open hospital_management_system.html directly in any web browser.

Interact with the dashboard: register OPD visits, admit patients, discharge bed occupancies, and export data.
