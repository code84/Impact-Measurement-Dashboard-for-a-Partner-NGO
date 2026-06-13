````md
# 📊 Impact Measurement Dashboard: Translating Activities to Outcomes

[![Next.js](https://img.shields.io/badge/Next.js-14-black?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-18-blue?style=for-the-badge&logo=react)](https://reactjs.org/)
[![Python](https://img.shields.io/badge/Python-3.9+-yellow?style=for-the-badge&logo=python)](https://www.python.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)

**Challenge 5.1 — Impact Measurement Dashboard for a Partner NGO**  
**Domain / Track:** Analytics & Insights

![Dashboard Preview]![alt text](image.png) ![alt text](image-1.png)



---

## 📑 Table of Contents

- [🎯 The Problem & Our Solution](#-the-problem--our-solution)
- [🌳 Our Theory of Change (The KPI Tree)](#-our-theory-of-change-the-kpi-tree)
- [🧠 Addressing the Challenge Brief](#-addressing-the-challenge-brief)
- [✨ Core Features](#-core-features)
- [🏗 Architecture & Folder Structure](#-architecture--folder-structure)
- [🚰 The Data Pipeline Explained](#-the-data-pipeline-explained)
- [🚀 Getting Started (Run Locally)](#-getting-started-run-locally)
- [🔮 Future Roadmap](#-future-roadmap)

---

## 🎯 The Problem & Our Solution

The vast majority of Indian NGOs measure **activities** (events held, beneficiaries reached) rather than **outcomes** (lives changed, behaviors shifted). This gap weakens fundraising, prevents course correction, and obscures what is actually working.

The tooling problem is not a lack of BI software—it is the missing translation layer between messy field data and decision-relevant KPIs.

Built for a representative Education NGO, this platform takes raw relational field data (attendance, assessment scores, and financial expenses) and automatically transforms it into an interactive impact dashboard.

The platform answers the most important question for NGO leadership:

> **"How much does it cost us to measurably change one life?"**

---

## 🌳 Our Theory of Change (The KPI Tree)

### Activity (Input)

Allocate budget and conduct learning sessions.

**Metrics**
- Total Program Budget Spent
- Learning Hours Delivered

↓

### Output (Direct Result)

Students actively participate in the program.

**Metrics**
- Attendance Rate
- Percentage of Students with >80% Attendance

↓

### Outcome (Capability Shift)

Students improve learning outcomes.

**Metrics**
- Baseline vs Endline Score Improvement
- Percentage of Students Crossing Impact Threshold

↓

### Impact (Systemic Goal)

Improve efficiency of donor funding and maximize educational impact.

**Metrics**
- Cost-per-Impacted Student
- Overall Program Effectiveness

---

## 🧠 Addressing the Challenge Brief

### What is the one number the Executive Director should check every Monday?

#### Cost-per-Impacted Student

Formula:

```text
Cost-per-Impacted Student
=
Total Program Cost
/
Number of Impacted Students
````

If this metric increases, leadership immediately knows that:

* Costs are increasing
* Program outcomes are declining

---

### How do you handle data quality issues from field workers?

Data quality is enforced before visualization.

The transformation pipeline:

* Removes duplicates
* Validates beneficiary IDs
* Handles missing records
* Normalizes attendance data
* Standardizes assessment records
* Merges all data into a clean analytics dataset

All cleaning occurs inside:

```text
scripts/transform_data.py
```

---

### What is the right reporting cadence?

| Stakeholder        | Cadence   |
| ------------------ | --------- |
| Field Workers      | Weekly    |
| Program Managers   | Weekly    |
| Executive Director | Monthly   |
| Board Members      | Quarterly |

---

## ✨ Core Features

### Dynamic KPI Engine

* Real-time KPI calculations
* Adjustable Impact Threshold slider
* Threshold range: 5%–50% improvement

### CSR Export Engine

Generate professional PDF reports for:

* Donors
* CSR partners
* NGO board meetings
* Funding applications

### Geographic Analytics

Analyze performance by:

* Village
* District
* Region

Visualizations include:

* Scatter Charts
* Distribution Charts
* Performance Comparisons

### Demographic Insights

Analyze impact across:

* Gender
* Age Groups
* Communities

### Dark Mode Dashboard

A modern interface designed specifically for non-technical NGO staff.

---

## 🏗 Architecture & Folder Structure

```text
impact-dashboard/
│
├── scripts/
│   ├── generate_data.py
│   └── transform_data.py
│
├── raw_data/
│   ├── beneficiaries.csv
│   ├── attendance.csv
│   ├── assessments.csv
│   └── expenses.csv
│
├── public/
│   └── final_dashboard_data.csv
│
├── app/
│   ├── page.tsx
│   ├── layout.tsx
│   └── globals.css
│
└── package.json
```

---

## 🚰 The Data Pipeline Explained

### Step 1: Data Generation

**File:** `generate_data.py`

Generates:

* 500 beneficiary records
* 4 villages
* 6-month program data
* Attendance logs
* Assessment scores
* Expense records

Features:

* Realistic attendance behavior
* Realistic score distributions
* Attendance-performance correlation

### Step 2: Data Transformation

**File:** `transform_data.py`

Responsibilities:

* Merge all source datasets
* Calculate attendance rate
* Calculate score improvement
* Calculate impact metrics
* Aggregate expenses
* Generate dashboard-ready dataset

Output:

```text
public/final_dashboard_data.csv
```

---

## 🚀 Getting Started (Run Locally)

### Prerequisites

* Node.js 18+
* Python 3.9+

### Clone Repository

```bash
git clone <your-repository-url>
cd impact-dashboard
```

### Install Dependencies

```bash
npm install
```

### Start Development Server

```bash
npm run dev
```

Open:

```text
http://localhost:3000
```

### Data Pipeline Setup

```bash
cd scripts
python -m venv venv
```

Windows:

```bash
venv\Scripts\activate
```

Linux/macOS:

```bash
source venv/bin/activate
```

Install Python dependencies:

```bash
pip install pandas numpy
```

Generate data:

```bash
python generate_data.py
```

Transform data:

```bash
python transform_data.py
```

---

## 📈 Success Metrics

| Metric                      | Target         |
| --------------------------- | -------------- |
| Dashboard Load Time         | < 3 seconds    |
| Stakeholder Usability Score | ≥ 8/10         |
| KPI Accuracy                | 100%           |
| Data Quality Validation     | Automated      |
| Dashboard Refresh Speed     | Near Real-Time |

---

## 🔮 Future Roadmap

### PostgreSQL / Supabase Integration

Move from flat CSV files to a production-grade database architecture.

### Role-Based Access Control (RBAC)

**Field Workers**

* Submit attendance
* Upload assessments

**Program Managers**

* Review program performance

**Executive Directors**

* View impact dashboards
* Export reports

### AI-Powered Insights

Automatically generate:

* Weekly summaries
* Performance alerts
* Funding recommendations
* District-level interventions

### IRIS+ Framework Mapping

Map NGO outcomes to internationally recognized impact standards.

Benefits:

* Easier grant applications
* Better donor reporting
* Increased transparency

---

## 🏆 Expected Impact

This dashboard acts as a reusable impact measurement template that can be adapted by dozens of small and medium-sized NGOs.

By translating activities into measurable outcomes, organizations can:

* Improve program effectiveness
* Make data-driven decisions
* Increase donor confidence
* Demonstrate measurable impact
* Scale successful interventions

---

**Built for Challenge 5.1 — Impact Measurement Dashboard for a Partner NGO**

**Analytics & Insights Track**

```
```
