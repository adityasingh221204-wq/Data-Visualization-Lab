# 📊 Assignment 5 — Mini Capstone Project: Data Storytelling & Dashboard Theming

<div align="center">

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Excel](https://img.shields.io/badge/Microsoft%20Excel-217346?style=for-the-badge&logo=microsoftexcel&logoColor=white)
![Dataset](https://img.shields.io/badge/Dataset-PG%20Portal%20Grievances-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

**Course:** Data Visualization Lab (TE7663) &nbsp;|&nbsp; **Sem:** V &nbsp;|&nbsp; **Academic Year:** 2026–2027  
**Practical No.:** 5 &nbsp;|&nbsp; **Submitted:** 28 September 2026

</div>

---

## 📁 Repository Contents

| File | Description |
|------|-------------|
| [`Assignment_5.pbix`](./Assignment_5.pbix) | Power BI Desktop dashboard file — fully interactive |
| [`expt 5.pdf`](./expt%205.pdf) | Lab manual / experiment sheet with theory, objectives, and assignment questions |
| [`Grievance_Dataset_Cleaned.xlsx`](./Grievance_Dataset_Cleaned.xlsx) | Cleaned dataset sourced from CPGRAMS / PG Portal, India |

---

## 🎯 Experiment Title

> **To design and implement a mini capstone project demonstrating data storytelling and dashboard theming techniques**

---

## 🏛️ Domain & Dataset

### Domain
**Public Governance / E-Governance — Citizen Grievance Redressal**

### Dataset: PG Portal (CPGRAMS) Grievance Data
The dataset is sourced from India's **Centralized Public Grievance Redress and Monitoring System (CPGRAMS)**, available via the **pgportal.gov.in** public dashboard. It captures grievance statistics across:

- **91 Central Government Organizations / Ministries**
- **36 States and Union Territories**

The raw data was downloaded from the PG Portal, cleaned, and organized into a structured Excel workbook for Power BI import.

---

## 🗂️ Dataset Structure

The cleaned workbook (`Grievance_Dataset_Cleaned.xlsx`) contains **3 sheets**:

### Sheet 1: `Org_Wise` (91 rows × 11 columns)
Organization-level grievance data for Central Government bodies.

| Column | Description |
|--------|-------------|
| `OrganizationName` | Name of the Central Ministry / Department |
| `Received` | Total grievances received |
| `Disposed` | Total grievances disposed / resolved |
| `PctDisposed` | Disposal rate (%) = Disposed / Received × 100 |
| `Pending0_60` | Pending grievances aged 0–60 days |
| `Pending60_180` | Pending grievances aged 60–180 days |
| `Pending180_365` | Pending grievances aged 180–365 days |
| `PendingOver1Yr` | Pending grievances aged over 1 year |
| `Pending (calc)` | Derived: Received − Disposed |
| `Aged Pending (>60d)` | Derived: Pending60_180 + Pending180_365 + PendingOver1Yr |
| `Aged Share` | Derived: Aged Pending / Total Pending |

### Sheet 2: `State_Wise` (38 rows × 11 columns)
State/UT-level grievance data.

| Column | Description |
|--------|-------------|
| `StateUT` | Name of the State or Union Territory |
| `Received` | Total grievances received |
| `Disposed` | Total grievances disposed / resolved |
| `PctDisposed` | Disposal rate (%) |
| `Pending0_60` | Pending 0–60 days |
| `Pending60_180` | Pending 60–180 days |
| `Pending180_365` | Pending 180–365 days |
| `PendingOver1Yr` | Pending over 1 year |
| `Pending (calc)` | Derived: Received − Disposed |
| `Aged Pending (>60d)` | Derived: sum of 60d+ buckets |
| `Aged Share` | Derived: Aged Pending / Total Pending |

### Sheet 3: `Read Me`
Documents all cleaning operations performed on the raw data.

---

## 🧹 Data Cleaning & Preparation

The raw PG Portal data required the following preprocessing steps before Power BI import:

### Org_Wise Sheet
- ✅ Trimmed leading/trailing whitespace from all organization names
- ✅ Fixed spelling error: `"Rejuvenuation"` → `"Rejuvenation"` (Ministry of Jal Shakti entry)
- ✅ Standardized numeric columns to integer/decimal types

### State_Wise Sheet
- ✅ Removed `"Union Territory of "` prefix from UT names (e.g., `"Union Territory of Ladakh"` → `"Ladakh"`)
- ✅ Standardized state names: `"NCT of Delhi"` → `"Delhi"`
- ✅ Fixed spelling: `"Chattisgarh"` → `"Chhattisgarh"`

### Derived / Helper Columns Added
Three calculated columns were added as Excel formulas (not hardcoded values) to enable dynamic DAX interaction in Power BI:

```
Pending (calc)      = Received - Disposed
Aged Pending (>60d) = Pending60_180 + Pending180_365 + PendingOver1Yr
Aged Share          = Aged Pending (>60d) / Pending (calc)
```

### Power BI Import Steps
```
Home → Get Data → Excel Workbook → Select file
→ Check: Org_Wise ✅  State_Wise ✅
→ Transform Data → Apply cleaning in Power Query → Close & Apply
```

---

## 📈 Key Dataset Statistics (National Overview)

### State-Wise Aggregates (Total Row)

| Metric | Value |
|--------|-------|
| **Total Grievances Received** | 7,51,518 |
| **Total Grievances Disposed** | 5,62,581 |
| **National Disposal Rate** | 74.86% |
| **Total Pending (0–60 days)** | 1,12,100 |
| **Total Pending (60–180 days)** | 60,921 |
| **Total Pending (180–365 days)** | 15,916 |
| **Pending Over 1 Year** | 0 |

### Top 5 Organizations by Grievances Received

| Organization | Received | Disposed | Disposal % |
|---|---|---|---|
| Financial Services (Banking Division) | 2,24,672 | 2,18,236 | 97.14% |
| Uttar Pradesh (State) | — | — | — |
| Central Board of Direct Taxes (IT) | 54,480 | 50,330 | 92.38% |
| Financial Services (Insurance) | 28,059 | 27,319 | 97.36% |
| Central Board of Excise & Customs | 11,988 | 11,682 | 97.45% |

### Best & Worst Performing States (Disposal Rate)

| Rank | State/UT | Disposal Rate |
|------|----------|--------------|
| 🥇 1st | **Telangana** | 97.03% |
| 🥈 2nd | **Chandigarh** | 93.46% |
| 🥉 3rd | **Andaman & Nicobar** | 93.43% |
| ⚠️ Bottom | **Manipur** | 2.40% |
| ⚠️ Bottom | **Nagaland** | 9.60% |
| ⚠️ Bottom | **West Bengal** | 14.65% |
| ⚠️ Bottom | **Jammu & Kashmir** | 14.79% |

### High-Volume States with Poor Disposal

| State | Received | Disposal % | Concern |
|-------|----------|-----------|---------|
| **Maharashtra** | 44,569 | 52.02% | Very high pending aged grievances |
| **Andhra Pradesh** | 15,596 | 55.61% | Large aged backlog |
| **West Bengal** | 21,235 | 14.65% | Critical — only 3,110 disposed |
| **Chhattisgarh** | 11,139 | 48.98% | Nearly half pending |

---

## 🖥️ Power BI Dashboard

### Dashboard Theme
A **custom JSON theme** (`PG_Grievance_theme.json`) was applied to maintain visual consistency:
- **Primary colour:** Deep government-blue palette
- **Accent colour:** Amber/gold for pending/warning indicators
- **Background:** Dark navy with white card panels
- **Font:** Consistent hierarchy — Title → Section Heading → KPI → Chart label
- **Style:** Formal analytical / public policy theme

### Dashboard Layout

```
┌────────────────────────────────────────────────────────────────┐
│          📊 India Grievance Redressal Dashboard                │
│          Source: CPGRAMS / PG Portal | 2026                    │
├────────────────────────────────────────────────────────────────┤
│  [KPI: Total Received]  [KPI: Total Disposed]  [KPI: Disposal%]│
│         [KPI: Total Pending]    [KPI: Aged Pending]            │
├─────────────────────────────┬──────────────────────────────────┤
│  Bar Chart:                 │  Map:                            │
│  Top 15 Orgs by Received    │  State-Wise Disposal Rate        │
│                             │  (Choropleth / Bubble Map)       │
├─────────────────────────────┼──────────────────────────────────┤
│  Stacked Bar:               │  Donut Chart:                    │
│  Pending Aging Buckets      │  Pending Breakdown               │
│  (0-60 / 60-180 / 180-365)  │  (0-60d vs 60-180d vs 180-365d) │
├─────────────────────────────┴──────────────────────────────────┤
│  Table: State-Wise Detail (Sortable, with conditional format)   │
├────────────────────────────────────────────────────────────────┤
│  🔍 Slicers: State/UT Filter | Organization Filter             │
├────────────────────────────────────────────────────────────────┤
│  💡 Key Insights Panel (Text Box with Narrative)               │
└────────────────────────────────────────────────────────────────┘
```

### Visualizations Used

| # | Visual Type | Data Used | Purpose |
|---|-------------|-----------|---------|
| 1 | **KPI Cards (×5)** | Total Received, Disposed, Disposal%, Pending, Aged Pending | At-a-glance performance overview |
| 2 | **Horizontal Bar Chart** | Org_Wise — Top 15 by Received | Compare grievance volume across ministries |
| 3 | **Filled Map / Bubble Map** | State_Wise — PctDisposed | Geographic analysis of redressal performance |
| 4 | **Stacked Bar Chart** | State_Wise — Pending aging buckets | Distribution of pending by age bracket |
| 5 | **Donut Chart** | Aggregate pending breakdown | Part-to-whole analysis of aging distribution |
| 6 | **Sorted Bar / Column** | State_Wise — PctDisposed ranked | Ranking states by performance |
| 7 | **Data Table** | Full State_Wise detail | Drill-down and detailed reference |
| 8 | **Slicer (State filter)** | StateUT column | Interactive filtering |
| 9 | **Text Box (Insight Narrative)** | Manual key findings | Storytelling narrative layer |

### DAX Measures Created

```dax
-- Total Received (Org_Wise)
Total Received = SUM(Org_Wise[Received])

-- Total Disposed
Total Disposed = SUM(Org_Wise[Disposed])

-- National Disposal Rate
Disposal Rate % = DIVIDE([Total Disposed], [Total Received], 0) * 100

-- Total Pending
Total Pending = [Total Received] - [Total Disposed]

-- Aged Pending (>60 days)
Aged Pending = 
    SUM(Org_Wise[Pending60_180]) + 
    SUM(Org_Wise[Pending180_365]) + 
    SUM(Org_Wise[PendingOver1Yr])

-- Aged Share %
Aged Share % = DIVIDE([Aged Pending], [Total Pending], 0) * 100
```

---

## 🎨 Dashboard Theming Details

A custom Power BI theme file (`PG_Grievance_theme.json`) was designed and applied:

```json
{
  "name": "PG_Grievance",
  "dataColors": ["#1F3A5F", "#2E86AB", "#A23B72", ...],
  "background": "#12263A",
  "foreground": "#FFFFFF",
  "tableAccent": "#F2C811"
}
```

**Theming Principles Applied:**
| Principle | Implementation |
|-----------|---------------|
| **Consistency** | Same font (Segoe UI), same colour palette throughout |
| **Contrast** | Dark background with light text; amber highlights for critical KPIs |
| **Simplicity** | No 3D charts, no decorative graphics, minimal gridlines |
| **Hierarchy** | Dashboard title → Section headings → KPI values → Chart labels |
| **Branding** | Government/policy formal tone — blues and golds |

---

## 📖 Data Story: The Grievance Redressal Crisis in India

### Context — What?
India's CPGRAMS system receives **hundreds of thousands of citizen grievances** annually across central ministries and state governments. This dashboard analyses how effectively these grievances are being resolved.

### Overview — So What?
- 🇮🇳 **7.5 lakh+ grievances** were filed in the period covered by this dataset
- Only **74.86%** were disposed of nationally — meaning over **1.88 lakh grievances remain pending**
- Over **76,800 grievances** have been pending for **more than 60 days**, indicating systemic delays

### Exploration — Key Patterns Found

1. **The Banking/Finance Sector is the biggest receiver** — The Financial Services (Banking Division) alone received **2.24 lakh grievances** (~30% of all central org grievances), but maintains a strong **97.14% disposal rate**

2. **Uttar Pradesh dominates state-level volume** — With **2.54 lakh** grievances, UP is the most grievance-prone state, but manages **87.49% disposal** — better than many smaller states

3. **West Bengal is in crisis** — Despite receiving **21,235 grievances**, only **3,110** (14.65%) were disposed. Nearly **9,000+ grievances** are stuck in the 60–180 day aged category

4. **Manipur, Nagaland, Ladakh and J&K** all show disposal rates below 20%, pointing to governance bottlenecks or administrative capacity issues in these regions

5. **Maharashtra's hidden backlog** — Despite being a large state with resources, Maharashtra shows only **52%** disposal with a massive **2,865 grievances pending 180–365 days**

6. **High performers** like Telangana (97.03%), Rajasthan (90.87%), and Gujarat (90.22%) show that high volume and high disposal rate can coexist

### Key Insight — The Most Important Finding
> ⚠️ **The aged backlog (60+ days) is concentrated in a small number of large states.** West Bengal, Maharashtra, Haryana, and Andhra Pradesh together account for the majority of all 60-day+ pending grievances. Targeted intervention in these 4 states could resolve over 40% of the national aged backlog.

### Action / Recommendation — Now What?
- 🔧 **Priority audit** of West Bengal's grievance redressal machinery — investigate why only 14.65% disposal rate despite large staff
- 📋 **Time-bound escalation mechanism** for grievances crossing 60 days in high-volume states
- 🏆 **Replicate best practices** from Telangana and Gujarat (both high volume + high disposal)
- 📊 **Monthly monitoring dashboard** should be shared with State Chief Secretaries for accountability

---

## 🧪 Experiment Objectives & Outcomes

### Objectives (from Lab Manual)
- [x] Identify a suitable real-world dataset and formulate meaningful analytical questions
- [x] Perform basic data cleaning, transformation, and preparation for visualization
- [x] Select appropriate charts and visual representations based on the nature of data
- [x] Apply data storytelling principles to communicate insights effectively
- [x] Develop an interactive dashboard containing multiple coordinated visualizations
- [x] Apply dashboard theming, formatting, layout, and visual hierarchy techniques
- [x] Interpret the results and communicate actionable insights derived from the dashboard

### Outcomes Achieved
- [x] Prepared and organized a real-world dataset (CPGRAMS) for visualization
- [x] Selected and implemented 9+ suitable visualizations for different analytical requirements
- [x] Developed a coherent data story (Context → Overview → Exploration → Insight → Action)
- [x] Applied dashboard layout, formatting, filtering, and theming techniques with custom JSON theme
- [x] Presented insights and recommendations supported by visual evidence

---

## 📚 Theory Summary

### Data Storytelling
Data storytelling is the process of communicating insights from data through a combination of:

```
Data  +  Visualization  +  Narrative  →  Insight
```

- **Data** provides the evidence
- **Visualization** makes patterns, trends, and relationships easier to understand
- **Narrative** provides context and guides the audience towards the key message

### The "What? – So What? – Now What?" Framework
| Question | Applied in this Project |
|----------|------------------------|
| **What?** | CPGRAMS grievance data across 91 central orgs and 36 states |
| **So What?** | 25% of grievances remain unresolved; West Bengal in critical state |
| **Now What?** | Target 4 key states; replicate high performers; monthly monitoring |

### Visualization Selection Rationale
| Purpose | Chart Used | Why |
|---------|-----------|-----|
| Comparison (orgs) | Horizontal Bar | Easy rank comparison |
| Geographic analysis | Map | Shows spatial distribution of disposal rates |
| Distribution | Stacked Bar | Shows proportion of aging buckets |
| Part-to-whole | Donut Chart | Pending breakdown |
| KPI monitoring | KPI Cards | Immediate attention to headline numbers |
| Detailed drill-down | Table | Enable exploration of individual entries |

---

## 🛠️ Tools & Software Used

| Tool | Version | Purpose |
|------|---------|---------|
| **Microsoft Power BI Desktop** | Latest (2026) | Dashboard creation, DAX, theming |
| **Microsoft Excel** | Microsoft 365 | Data cleaning and helper column formulas |
| **PG Portal / CPGRAMS** | — | Data source |
| **Custom JSON Theme** | `PG_Grievance_theme.json` | Dashboard visual consistency |

---

## 📝 Assignment Questions (from Lab Manual)

1. Explain the concept of data storytelling. Describe the role of data, visualization, and narrative in communicating insights effectively.
2. Differentiate between data visualization and data storytelling. Explain how storytelling adds value to a dashboard.
3. Explain the importance of selecting an appropriate visualization for a given analytical question. Give suitable examples for comparison, trend, distribution, relationship, and part-to-whole analysis.
4. What is a dashboard? Explain the essential characteristics of an effective and user-friendly dashboard.
5. What is visual hierarchy? Explain how size, position, colour, contrast, and whitespace can be used to establish visual hierarchy in a dashboard.

---

## 👨‍🎓 Student Information

| Field | Details |
|-------|---------|
| **Course** | Data Visualization Lab |
| **Course Code** | TE7663 |
| **Semester** | V |
| **Academic Year** | 2026–2027 |
| **Practical No.** | 5 |
| **Submission Date** | 28 September 2026 |

---

<div align="center">

*Dashboard built with ❤️ using Microsoft Power BI Desktop*  
*Data Source: CPGRAMS / PG Portal, Government of India*

</div>
