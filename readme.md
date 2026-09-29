# BHUMISETU (भूमिसितु)
### National Land Acquisition Management & Statutory Milestone Early-Warning Platform
**Ministry of Rural Development & Department of Land Resources | Government of India**  
*Enforcing Compliance with the Right to Fair Compensation and Transparency in Land Acquisition, Rehabilitation and Resettlement Act, 2013 (RFCTLARR Act, 2013)*

---

## 📑 Table of Contents

1. [Executive Summary: What is BHUMISETU?](#1-executive-summary-what-is-bhumisetu)
2. [The Real-World Problem Solved](#2-the-real-world-problem-solved)
3. [Statutory & Legal Framework (RFCTLARR 2013)](#3-statutory--legal-framework-rfctlarr-2013)
4. [Platform Architecture & System Personas](#4-platform-architecture--system-personas)
5. [Core Functional Modules & Features](#5-core-functional-modules--features)
   - 5.1 [7-Stage Statutory Acquisition Lifecycle Engine](#51-7-stage-statutory-acquisition-lifecycle-engine)
   - 5.2 [PostGIS Cadastral GIS & Spatial Coordinate Engine](#52-postgis-cadastral-gis--spatial-coordinate-engine)
   - 5.3 [Historical Cadastral (1970s) & Encroachment Detection](#53-historical-cadastral-1970s--encroachment-detection)
   - 5.4 [RERA Real Estate Project Gateway & Conflict Cross-Referencing](#54-rera-real-estate-project-gateway--conflict-cross-referencing)
   - 5.5 [Devanagari OCR & 7/12 Land Record Digitization](#55-devanagari-ocr--712-land-record-digitization)
   - 5.6 [AI Delay Risk & Survival Early-Warning Engine](#56-ai-delay-risk--survival-early-warning-engine)
   - 5.7 [Statutory Business Rules & Blocking Validation Hub](#57-statutory-business-rules--blocking-validation-hub)
   - 5.8 [Bulk Import & Ingestion Hub](#58-bulk-import--ingestion-hub)
   - 5.9 [DPDP Act 2023 Data Privacy & Retention Hub](#59-dpdp-act-2023-data-privacy--retention-hub)
   - 5.10 [Immutable Audit Trail & Regulatory Logging](#510-immutable-audit-trail--regulatory-logging)
   - 5.11 [Citizen & Public Portal (GIGW / S3WaaS Compliant)](#511-citizen--public-portal-gigw--s3waas-compliant)
6. [Technology Stack & Architectural Specifications](#6-technology-stack--architectural-specifications)
7. [User Guide & Demo Walkthrough](#7-user-guide--demo-walkthrough)
8. [Setup, Installation & Development](#8-setup-installation--development)
9. [Glossary of Legal & Revenue Terms](#9-glossary-of-legal--revenue-terms)

---

## 1. Executive Summary: What is BHUMISETU?

**BHUMISETU** (*Bhumi* = Land, *Setu* = Bridge) is an enterprise-grade digital public infrastructure (DPI) platform designed for the Government of India, State Revenue Departments, and Central Infrastructure Authorities (NHAI, Indian Railways, Metro Rail Corporations, Airport Authority of India, Industrial Corridor Development Corporations).

The platform serves as an end-to-end statutory operating system and early-warning decision support system for acquiring private and community land for public infrastructure projects under the landmark **Right to Fair Compensation and Transparency in Land Acquisition, Rehabilitation and Resettlement Act, 2013 (RFCTLARR Act, 2013)**.

### At a Glance:
- **Dual-Portal Ecosystem**:
  - **Citizen / Public Portal**: An open, bilingual (English & Hindi), accessibility-compliant (GIGW 3.0 / S3WaaS) portal enabling citizens to search gazette notifications, track land records, submit Section 15 objections, track compensation awards, and discover government welfare schemes.
  - **Revenue Officer Operations Portal**: A specialized back-office workspace for District Collectors, Special Land Acquisition Officers (SLAO), and Survey Officers to manage spatial parcels, resolve title conflicts, audit Devanagari OCR land records, monitor ML delay risks, and disburse compensation via PFMS Direct Benefit Transfer (DBT).
- **Spatial Precision**: Features an embedded **PostGIS Spatial Engine** and **1970s Archival Cadastral Comparison Module** that detects unauthorized field bund drift, government grazing land encroachment, and Right-of-Way (RoW) intrusions before compensation awards are finalized.
- **RERA Cross-Referencing**: Integrates with Real Estate Regulatory Authority (RERA) registers to automatically flag illegal Section 11(4) transactions and protect residential allottees.

---

## 2. The Real-World Problem Solved

Land acquisition in India has historically been fraught with procedural bottlenecks, litigation, and statutory lapses:

| Historical Challenge | Statutory Impact | How BHUMISETU Solves It |
|---|---|---|
| **Statutory Timeline Lapses** | Under RFCTLARR Section 19(1), if a declaration is not made within **12 months** of the preliminary notification, the entire acquisition lapses, costing hundreds of crores in re-notification. | **AI Survival & Delay Risk Engine** monitors active countdowns and predicts lapse probabilities with prescriptive intervention actions. |
| **Archaic Paper Records & Modi/Devanagari Scripts** | 7/12 extracts (*Satbara Utara*) and mutation registers (*Ferfar*) are frequently hand-written in regional scripts with fractional shares that do not tally to 100%. | **Human-in-the-Loop OCR Engine** digitizes Devanagari records, maps bounding boxes, and strictly enforces mathematical share reconciliation ($\sum \text{Shares} = 1.0000$). |
| **Unchecked Encroachment on Public Land** | Private landholders often encroach into adjacent PWD road margins, government grazing land (*Gairan*), or natural streams (*Nala*), claiming wrongful compensation. | **Historical Cadastral 1974 Settlement Revision Engine** overlays 50-year-old survey sheets against current satellite DGPS boundaries, calculating exact illegal areas and solatium deductions. |
| **RERA Real Estate Clashes** | Private builders sell plots or high-rise apartments on land already notified under Section 11, leading to innocent buyers being caught in demolitions or compensation disputes. | **RERA Project Gateway** cross-references cadastral survey numbers against MahaRERA/UP RERA databases, flagging Section 11(4) violations and freezing escrow accounts. |
| **Dispute Litigation & Section 15 Objections** | Objections submitted by farmers get lost in physical files, missing statutory hearing windows and resulting in High Court stays. | **Digital Section 15 Hearing Desk** logs every objection with unique tracking numbers, strict hearing deadlines, and disposal registers. |
| **Lack of Public Transparency** | Landowners lack visibility into how their land was valued, leading to mistrust and violent protests. | **Transparent Public Valuation Breakdown** breaks down market circle rate (ASR), rural multiplier (1.0 to 2.0), 100% Solatium, and 12% Additional Market Value. |

---

## 3. Statutory & Legal Framework (RFCTLARR 2013)

BHUMISETU enforces the statutory workflow mandated by the **RFCTLARR Act, 2013**:

```
[ Stage 1: Social Impact Assessment (Sec 4-9) ]
                     │
                     ▼
[ Stage 2: Preliminary Notification (Sec 11) ] ──▶ [ STRICT 12-MONTH CLOCK STARTS ]
                     │
                     ▼
[ Stage 3: Section 15 Public Objections & Hearing ] ──▶ (60-day window for citizen claims)
                     │
                     ▼
[ Stage 4: Declaration of Acquisition (Sec 19) ] ──▶ (Must occur within 12 months of Sec 11)
                     │
                     ▼
[ Stage 5: Compensation Award Determination (Sec 23-30) ]
       ├─ Market Value (Circle Rate × Rural Multiplier 1.0-2.0)
       ├─ Asset on Land (Trees, Crops, Wells, Structures)
       ├─ 100% Solatium (Sec 30)
       └─ 12% p.a. Additional Market Value (Sec 30)
                     │
                     ▼
[ Stage 6: DBT Disbursement & PFMS Payouts (Sec 37-38) ]
                     │
                     ▼
[ Stage 7: Physical Land Possession Handover (Sec 38) ]
```

---

## 4. Platform Architecture & System Personas

### 4.1 System Personas & Role-Based Access Control (RBAC)

BHUMISETU implements a strict four-tier persona model matching Indian revenue administration:

```
┌────────────────────────────────────────────────────────────────────────┐
│                        DISTRICT COLLECTOR / DM                         │
│  - Apex sanctioning authority                                         │
│  - Approves Section 19 declarations & Section 23 awards                │
│  - Exercises statutory overrides on blocking validations               │
└──────────────────────────────────┬─────────────────────────────────────┘
                                   │
┌──────────────────────────────────┴─────────────────────────────────────┐
│             SPECIAL LAND ACQUISITION OFFICER (SLAO / SDO)              │
│  - Conducts Section 15 objection hearings                              │
│  - Approves OCR digitized land records and resolves title defects      │
│  - Authorizes PFMS compensation vouchers and DBT payouts               │
└──────────────────────────────────┬─────────────────────────────────────┘
                                   │
┌──────────────────────────────────┴─────────────────────────────────────┐
│                    SURVEY OFFICER / TALATHI / DLR                      │
│  - Performs Joint Measurement Surveys (JMS) & DGPS boundary validation │
│  - Operates Cadastral GIS and 1974 historical encroachment comparison   │
│  - Verifies physical boundary stones and ground truth measurements     │
└──────────────────────────────────┬─────────────────────────────────────┘
                                   │
┌──────────────────────────────────┴─────────────────────────────────────┐
│                          CITIZEN / KHATEDAR                            │
│  - Searches land records by Gat/Khasra number and ULPIN                │
│  - Submits Section 15 objections online with documentary proof         │
│  - Tracks DBT compensation disbursements and submits DPDP DSR requests │
└────────────────────────────────────────────────────────────────────────┘
```

---

## 5. Core Functional Modules & Features

### 5.1 7-Stage Statutory Acquisition Lifecycle Engine
- **End-to-End Case Progression**: Manages land acquisition projects across seven statutory stages with real-time statutory countdown timers.
- **Stage Lock Guards**: Hard architectural guards prevent transitioning between stages if statutory prerequisites are unfulfilled (e.g., cannot transition to Stage 4 without disposing of all Section 15 objections or resolving blocking validations).
- **Statutory Milestone Countdown**: Live tracking of the critical Section 11 to Section 19 12-month statutory window, with color-coded alerts (Normal, Approaching Deadline, Breached).

### 5.2 PostGIS Cadastral GIS & Spatial Coordinate Engine
BHUMISETU incorporates a native client-side implementation of core **PostGIS spatial predicates** and geodetic algorithms:
- **`ST_Area(geom::geography)`**: Computes true geodesic surface area in square meters using spherical excess algorithms on the WGS 84 ellipsoid (EPSG:4326).
- **`ST_Perimeter(geom::geography)`**: Calculates true geodesic boundary perimeter in meters.
- **`ST_Distance(p1, p2)`**: Haversine distance computation between geographic points.
- **`ST_Intersects` & `ST_Contains`**: Point-in-polygon and polygon-intersection validation.
- **`ST_Buffer`**: Dynamic corridor generation (e.g., 60-meter Right-of-Way buffer along NH-48 or dedicated freight corridors).
- **`ST_Transform`**: Coordinate projection between WGS 84 (EPSG:4326), Web Mercator (EPSG:3857), and UTM Zone 43N (EPSG:32643).
- **PostGIS SQL Console**: An interactive terminal executing simulated spatial SQL queries directly against the cadastral feature collection, highlighting matching geometries on the interactive Leaflet map.

### 5.3 Historical Cadastral (1970s) & Encroachment Detection
Encroachment onto government land prior to acquisition is one of the largest sources of illegal compensation claims.
- **Archival Survey Digitization**: Ingests 1974 Settlement Revision records (survey sheets, boundary stones, old survey numbers, and guntha extents).
- **Dual-Layer Spatial Overlay**: Displays the 1974 Archival boundary in golden amber alongside the 2024 DGPS/satellite boundary in bright cyan.
- **Automated Encroachment Classification**:
  - `PWD_ROW_RESERVE`: Unauthorized expansion into statutory highway margins.
  - `GOVT_GAIRAN_GRAZING`: Encroachment into village common grazing/pasture land.
  - `NATURAL_NALA_BUFFER`: Unauthorized filling or diversion of natural water drainage streams.
  - `BOUND_DRIFT_AGRICULTURAL`: Gradual creeping of farm bunds into adjacent government land.
- **Boundary Stone Audit**: Tracks physical historical boundary stones (*Dhuracha Dagad* / *Hadd-chihna*), identifying missing, damaged, or displaced markers with displacement distances.
- **Statutory Solatium Deduction**: Computes the exact monetary penalty and ineligible compensation amount under Section 23/30 of RFCTLARR 2013, protecting public funds from fraudulent claims.

### 5.4 RERA Real Estate Project Gateway & Conflict Cross-Referencing
Under Section 11(4) of the RFCTLARR Act, once a Section 11 preliminary notification is gazetted, any sale, lease, mortgage, or development of the notified land without prior sanction of the Collector is void.
- **Live RERA Integration**: Connects with Real Estate Regulatory Authority systems (MahaRERA, UP RERA, GujRERA, K-RERA) to monitor residential layouts, townships, and commercial developments overlapping with acquisition corridors.
- **Conflict Severity Levels**:
  - `CRITICAL_BLOCKER`: Active Section 11(4) violation where developers continue selling plots on notified land.
  - `HIGH_RISK`: Clashing possession dates and major mortgage charges registered with commercial banks.
  - `MODERATE_WARNING`: Discrepancies between approved RERA layout areas and revenue survey extents.
- **Automated Enforcement Workflows**:
  - Drafting and issuing **Section 11(4) Statutory Freeze Notices**.
  - Dispatching **Summons to Promoters** for formal hearings before the Land Acquisition Officer.
  - Generating **Escrow Bank Directives** to freeze the 70% project development account.

### 5.5 Devanagari OCR & 7/12 Land Record Digitization
- **Bhashini & Indic-AI Alignment**: Specialized in parsing archaic Marathi/Hindi land records (7/12 Extracts, Sale Deeds, Mutation Registers).
- **Interactive Bounding Box Reviewer**: Visual overlay of document scans with field-by-field OCR recognition bounding boxes.
- **Field Confidence Scoring**: Color-coded confidence ratings (High Confidence $>90\%$, Medium, Low $<70\%$).
- **Review States**: Auto-Accepted, Pending Review, Corrected, Confirmed, and Manual Entry Required.
- **Strict Share Summation Rule**: Automatic validation checking that fractional co-ownership shares sum to exactly $1.0000$ (e.g., $0.5000 + 0.2500 + 0.2500 = 1.0000$).

### 5.6 AI Delay Risk & Survival Early-Warning Engine
- **Machine Learning Architecture**: Survival analysis model (Weibull AFT / XGBoost calibrated) trained on historical land acquisition case registries.
- **Risk Bands**: Low, Medium, High, and Critical probability of statutory lapse or project delay.
- **Explainable AI (XAI)**: Feature attribution breakdown indicating positive and negative drivers of delay (e.g., pending court stays, high objection density, SLAO workload, missing boundary stones).
- **Prescriptive Recommendations**: Suggested officer interventions (e.g., issue expedited notice, dispose objection, schedule joint measurement) with one-click disposition and audit logging.
- **Model Observability Hub**: Real-time evaluation metrics including PR-AUC ($0.884$), ROC-AUC ($0.912$), Brier Score ($0.082$), Expected Calibration Error ($0.027$), and Population Stability Index (PSI) feature drift monitoring.

### 5.7 Statutory Business Rules & Blocking Validation Hub
- **Automated Regulatory Watchdog**: Evaluates cases continuously against 10+ statutory revenue rules.
- **Severity Levels**:
  - `BLOCKING`: Prevents case progression (e.g., undisposed Section 15 objections, ownership share mismatch, unverified bank mandates).
  - `MAJOR`: High-risk warnings requiring officer attention.
  - `MINOR` & `ADVISORY`: Guidance notes for clean documentation.
- **Formal Waiver Protocol**: Authorizes designated District Collectors to waive non-statutory blockers with mandatory legal justification and immutable audit logging.

### 5.8 Bulk Import & Ingestion Hub
- **High-Throughput Batch Processing**: Ingests hundreds of land parcels and ownership records via standardized CSV/Excel templates.
- **Pre-Commit Verification**: Validates Gat numbers, census village codes, and ownership share integrity prior to committing records to the primary ledger.
- **Row-Level Error Reporting**: Visual inspection of valid, committed, and rejected rows with specific statutory rejection rules.

### 5.9 DPDP Act 2023 Data Privacy & Retention Hub
- **Digital Personal Data Protection Act, 2023 Compliance**:
  - Masked citizen PII: Aadhaar numbers masked as `XXXX-XXXX-8921`, masked bank accounts, and hashed phone numbers.
  - Consent-based processing trails for all citizen interactions.
- **Data Subject Rights (DSR) Management**:
  - Citizen Access Requests (Right to Access).
  - Citizen Correction Requests (Right to Rectification).
  - Lawful statutory retention schedule enforcement and secure data erasure logging.

### 5.10 Immutable Audit Trail & Regulatory Logging
- **Tamper-Evident Chronological Ledger**: Every user action (stage transition, OCR field correction, waiver approval, payment disbursement, risk override) is recorded with actor ID, designation, timestamp, and before/after state diffs.
- **High Court & CVC Evidentiary Standards**: Formatted for compliance with Central Vigilance Commission (CVC) guidelines and judicial scrutiny.

### 5.11 Citizen & Public Portal (GIGW / S3WaaS Compliant)
- **S3WaaS Design System**: Adheres to the Secure, Scalable and Sugamya Website as a Service guidelines of the Government of India.
- **Accessibility Suite**: Full support for High Contrast mode, font resizing (Normal, Large, Extra Large), keyboard navigation, and screen readers.
- **Bilingual Interface**: Seamless one-click toggling between English and Hindi across all headings, navigation items, and data labels.
- **Citizen Features**:
  - **Record Search**: Search by State, District, Tehsil, Village, Gat/Survey Number, or Case Reference.
  - **Section 15 Objection Filing**: File formal objections online, upload supporting registered sale deeds, and receive a permanent tracking ID (`OBJ-YYYY-XXXX`).
  - **Objection Hearing Tracker**: Check hearing dates, assigned Land Acquisition Officer, and order sheets.
  - **Gazette Notification Archive**: Download certified Section 4, 11, and 19 notifications.
  - **Government Schemes Directory & Entitlement Advisor**: Browse central and state welfare programs (PM-KISAN, PM GatiShakti, SVAMITVA, DILRMP) with a personalized eligibility calculator.

---

## 6. Technology Stack & Architectural Specifications

| Layer | Technologies Used | Purpose / Implementation |
|---|---|---|
| **Frontend Framework** | React 19, TypeScript, Vite | Modern, lightning-fast reactive single-page application. |
| **Styling & Design System** | Tailwind CSS v4, S3WaaS Palette | Authentic Government of India color palette (Navy Blue `#0b3866`, India Saffron `#f37021`, India Green `#138808`), GIGW-compliant typography. |
| **Mapping & GIS** | Leaflet, OpenStreetMap, Esri Satellite, CartoDB | Interactive geospatial viewer supporting polygon rendering, multi-tile basemaps, and custom layer switching. |
| **Spatial Engine** | Custom PostGIS Geodetic Math Library (`src/lib/postgis.ts`) | Spherical excess geodesic area, Haversine distance, polygon buffering, WGS 84 / UTM 43N transformations. |
| **Motion & Interaction** | Motion (Framer Motion) | Smooth transitions, modal overlays, and accessible animations. |
| **Icons & Visuals** | Lucide React, National Emblem of India, Tricolour Ribbon | Official emblems, ashoka chakra styling, and semantic iconography. |
| **Data Integrity** | React Context (`AppContext.tsx`), Strict TypeScript Enums | Centralized state management, role switching, real-time toast notifications, and optimistic UI updates. |
| **Build & Tooling** | Vite, tsx, ESLint, TypeScript 5.8 | Production-optimized bundling with tree-shaking and zero runtime errors. |

---

## 7. User Guide & Demo Walkthrough

BHUMISETU comes pre-loaded with comprehensive mock data, realistic infrastructure projects (e.g., NH-48 Expressway widening in Pune, Nashik Ring Road, Konkan Railway Doubling), and verified personas.

### Pre-Configured Demo Personas
Click the **"Official Demo Login"** button in the header to switch between roles instantly:

1. **Dr. Rajeshwar Deshmukh, IAS** — District Collector & District Magistrate (Pune)
   - *Permissions*: Full statutory powers, stage transition, blocking validation waiver, award approval.
2. **Smt. Sunita Kulkarni, Dy. Collector** — Special Land Acquisition Officer (SLAO - NHAI Cell)
   - *Permissions*: Conducts hearings, disposes Section 15 objections, corrects OCR data, issues notices.
3. **Shri Vikas Patil, Sub-Divisional Surveyor** — Cadastral & Survey Officer (Talathi / DLR)
   - *Permissions*: JMS survey validation, PostGIS spatial queries, 1974 historical boundary stone audit.
4. **Shri Tukaram Bapu Jadhav** — Citizen / Affected Landowner (Khatedar - Gat No. 142/A)
   - *Permissions*: Public portal access, submits Section 15 objection, tracks compensation DBT status.

### Recommended 5-Minute Tour:
1. **Explore the Public Portal**:
   - Navigate through **Search Records**, filter by *District: Pune*, *Village: Khed Shivapur*.
   - View the detailed compensation breakdown for *Case MH-PUN-2024-NH48-0042*.
   - Open **Section 15 Objections**, test the online submission form, and track `OBJ-2026-8812`.
   - Toggle **Language (हिंदी / English)** and **High Contrast mode** in the top utility bar.
2. **Switch to Officer Portal** (as SLAO or District Collector):
   - **Dashboard**: View high-level metrics (Active Cases, Sanctioned Budget, Critical Risk Cases, Pending Validations).
   - **Case Workspace (360°)**: Inspect the 7-stage lifecycle progress bar, ownership records, and statutory countdowns.
   - **Cadastral GIS Map**: Toggle between *OpenStreetMap* and *Satellite Imagery*, inspect *1974 Archival Cadastral Overlay*, and see the red encroachment polygon on Gat 142/A with calculated solatium deduction. Run a preset PostGIS query in the SQL console.
   - **RERA Gateway**: Review real estate developments overlapping with acquisition corridors, inspect Section 11(4) breaches, and review RERA escrow audits.
   - **Devanagari OCR Reviewer**: Compare scanned Marathi 7/12 extracts with extracted bounding boxes and correct any flagged field.
   - **Validation Queue**: Review blocking rules, test the formal Collector waiver flow, and view the immutable audit entry generated.
   - **Model Observability**: Examine PR-AUC, ROC-AUC, Brier score, and feature drift monitors.

---

## 8. Setup, Installation & Development

### Prerequisites
- **Node.js**: `v20.0.0` or higher
- **Package Manager**: `npm` or `bun`

### Quick Start

```bash
# 1. Clone the repository
git clone <repository-url>
cd bhumisetu

# 2. Install project dependencies
npm install

# 3. Configure environment variables (optional for local mock mode)
cp .env.example .env

# 4. Start the development server (runs on port 3000)
npm run dev

# 5. Build for production
npm run build
```

### Environment Variables (`.env.example`)
```env
# GEMINI_API_KEY: Optional key for generative insights
GEMINI_API_KEY="YOUR_GEMINI_API_KEY"

# APP_URL: Base URL where the applet is hosted
APP_URL="http://localhost:3000"
```

---

## 9. Glossary of Legal & Revenue Terms

- **RFCTLARR Act, 2013**: *Right to Fair Compensation and Transparency in Land Acquisition, Rehabilitation and Resettlement Act, 2013*. The governing Indian federal law for public land acquisition.
- **Section 4**: Mandatory Social Impact Assessment (SIA) study.
- **Section 11**: Preliminary Notification issued in the Official Gazette stating the intent to acquire land.
- **Section 11(4)**: Strict statutory bar prohibiting landowners or builders from creating any encumbrance, sale, or construction after Section 11 publication without the Collector’s prior permission.
- **Section 15**: Citizen’s statutory right to object to the acquisition within 60 days of preliminary notification.
- **Section 19**: Final Declaration of Acquisition issued after examining SIA and disposing of objections. Must be published within 12 months of Section 11.
- **Section 23 / 30**: Determination of the Compensation Award including Market Value, Assets, 100% Solatium, and 12% Additional Market Value.
- **Solatium**: Mandatory statutory compensation paid over and above the market value (100% under RFCTLARR) in consideration of the compulsory nature of the acquisition.
- **7/12 Extract (*Satbara Utara*)**: The primary land title and cultivation ledger maintained by revenue authorities in Maharashtra and western India.
- **Gat / Khasra Number**: The unique cadastral parcel number assigned to a piece of rural land during revenue settlement surveys.
- **Khatedar**: The legally recognized landowner or account-holder in revenue land records.
- **ULPIN**: *Unique Land Parcel Identification Number* (Bhu-Aadhaar), a 14-digit alphanumeric georeferenced identification number.
- **Gairan**: Village common land reserved for cattle grazing (Poramboke), strictly prohibited from private encroachment.
- **Potkharab**: Rocky, uncultivable, or waterlogged land within a survey number deducted from agricultural valuation.
- **PFMS**: *Public Financial Management System*, the central government gateway for Direct Benefit Transfer (DBT) disbursements.
- **S3WaaS**: *Secure, Scalable and Sugamya Website as a Service*, the Government of India framework for accessible, compliant websites.
- **GIGW 3.0**: *Guidelines for Indian Government Websites*, mandatory digital standards published by the National Informatics Centre (NIC).
- **DPDP Act, 2023**: *Digital Personal Data Protection Act, 2023*, India’s comprehensive privacy statute governing processing of personal digital data.

---

*BHUMISETU is developed to uphold fairness, statutory rigor, transparent governance, and spatial accuracy across public infrastructure projects across the Republic of India.*
