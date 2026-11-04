#CareSys  

Modern Hospital Management System & Database PortalCareSys HMS is a comprehensive, single-page web dashboard and 3NF normalized ANSI SQL database engine designed to streamline outpatient consultations (OPD), inpatient ward admissions (IPD), physician scheduling, live bed occupancy tracking, and multi-format reporting.🌟 Key Features⚡ Real-Time Executive KPI Dashboard: Instantly tracks Total Registered Patients, Today's OPD Visits, Admitted Inpatients, and Available Ward Beds ratio.🩺 Outpatient Department (OPD) Portal: Log consultation tickets, record symptoms/diagnoses, assign physicians, and automatically calculate consultation tariffs.🛏️ Interactive Ward & Bed Management: Real-time visual tracking of multi-tier hospital wards (General Ward, Private Rooms, ICU). Supports one-click patient admissions and discharges with dynamic state toggles (Available vs Occupied).🔍 Patient Directory with Dynamic Filtering: Filter patient records instantly by text search (Name/Phone), Gender, or Blood Group.📊 Multi-Format Data Exporter: One-click export of clinical records to native Microsoft Excel (.xlsx) via SheetJS, CSV, and JSON.📜 Terminal-Style Audit Activity Log: Chronological live logging of all system transactions, admissions, discharges, and data exports with timestamping.💾 Normalized SQL Database Architecture: 3NF compliant schema scripts with relational foreign key integrity, triggers, and analytical views.🗂️ Database Architecture & NormalizationThe database architecture is designed up to Third Normal Form (3NF) across 6 core entities:  +------------------+         +-------------------+
  |     PATIENTS     |         |      DOCTORS      |
  +------------------+         +-------------------+
  | PK  patient_id   |<---\    | PK  doctor_id     |<---\
  |     name         |    |    |     name          |    |
  |     gender       |    |    |     specialization|    |
  |     age          |    |    |     consultation_fee   |
  |     phone        |    |    +-------------------+    |
  |     blood_group  |    |                             |
  |     address      |    |    +-------------------+    |
  +------------------+    |    |     OPD_VISITS    |    |
           |              |    +-------------------+    |
           |              |--->| PK  visit_id      |    |
           |              |    | FK  patient_id    |----/
           |              |    | FK  doctor_id     |
           |              |    |     symptoms      |
           |              |    |     diagnosis     |
           |              |    |     fee           |
           |              |    |     visit_time    |
           |              |    +-------------------+
           |              |
           |              |    +-------------------+
           |              |    |       WARDS       |
           |              |    +-------------------+
           |              |    | PK  ward_id       |<---\
           |              |    |     ward_name     |    |
           |              |    |     daily_rate    |    |
           |              |    +-------------------+    |
           |              |                             |
           |              |    +-------------------+    |
           |              |    |       BEDS        |    |
           |              |    +-------------------+    |
           |              |--->| PK  bed_id        |    |
           |              |    | FK  ward_id       |----/
           |              |    |     bed_number    |
           |              |    |     status        |
           |              |    +-------------------+
           |              |              ^
           |              |              |
           |              v              |
           |      +-------------------+  |
           |      |    ADMISSIONS     |  |
           |      +-------------------+  |
           |----->| PK  admission_id  |  |
                  | FK  patient_id    |  |
                  | FK  bed_id        |--/
                  |     admission_date|
                  |     discharge_date|
                  |     reason        |
                  +-------------------+
🛠️ Technology StackLayerTechnology / LibraryDescriptionFrontend LayoutHTML5Semantic structure & modern form controlsStylingTailwind CSSResponsive utility-first framework & glassmorphismIcons & FontsFont Awesome 6.4 / InterSystem UI icons and clean typographyClient EngineJavaScript (ES6+)Dynamic DOM rendering, state engine, & search algorithmsData ExportSheetJS (xlsx.js)Binary client-side Excel workbook generationBackend DBANSI SQL (MySQL / PostgreSQL)DDL, DML scripts, foreign keys, views, and triggers🚀 Quick Start & InstallationOption 1: Running the Dashboard Web PortalNo server setup or build process required!Clone this repository:git clone https://github.com/YourUsername/CareSys-Hospital-Management-System.git
Navigate to the project directory:cd CareSys-Hospital-Management-System
Open hospital_management_system.html directly in any web browser (Chrome, Edge, Firefox, Safari).Option 2: Setting Up the SQL Database BackendOpen your MySQL Workbench or PostgreSQL command line interface.Execute the schema script:CREATE DATABASE IF NOT EXISTS CaresysHMS;
USE CaresysHMS;
Run the DDL script contained in schema.sql (or copy from the project report) to build all 6 normalized tables with relational integrity checks.Run the seed dataset script to populate default patient records, ward definitions, bed structures, and physician tariffs.📂 Project Structure├── hospital_management_system.html   # Main interactive HMS web portal
├── schema.sql                        # Complete ANSI SQL DDL, DML, Triggers, & Views
├── README.md                         # Project documentation and setup guide
└── docs/
    └── Project_Report.pdf            # Comprehensive 20+ page academic report
📋 Features Walkthrough1. Registering an OPD VisitClick "+ New OPD Visit" in the top navigation header.Select a registered patient and an assigned consulting physician.Enter symptoms and clinical notes. The fee tariff will auto-populate based on doctor rates.Click "Save OPD Visit"—the system updates the dashboard metrics and activity log instantly.2. Admitting & Discharging InpatientsClick "+ Admit Patient".The system lists only beds currently marked as Available.Confirm admission to toggle the bed's status to Occupied.To release a bed, navigate to the Bed Occupancy Board and click "Discharge" on any occupied bed card.3. Exporting ReportsIn the Patient Directory section, click Export CSV, Export Excel, or JSON.SheetJS instantly compiles the data state into a formatted .xlsx spreadsheet file downloaded to your machine.📜 LicenseDistributed under the MIT License. See LICENSE for more information.👨‍💻 AuthorHritik SharmaMaster of Computer Applications (MCA)Chandigarh University (2026)UID: 26MCA20098
