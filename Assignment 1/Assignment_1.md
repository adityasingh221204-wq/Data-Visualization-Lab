# Assignment 1: Exploring Raw Data & Transforming Insights with Power BI

## 📝 Executive Overview
This assignment documents the step-by-step implementation, key data transformations, and analytic discoveries made while working with the **AdventureWorks Customer Lookup** dataset within Microsoft Power BI. 

The primary objective was to transition a raw, flat demographics table into a modern, self-explanatory executive dashboard that delivers automated business intelligence without requiring manual narration.

---

## 🔧 Phase 1: Power Query Text Transformations
The initial phase required targeted data engineering inside the Power Query Editor to isolate and clean web domain metrics from customer contact records.

### Objectives & Implementation Steps:
1. **Column Duplication:** Located the `EmailAddress` column, right-clicked, and selected **Duplicate Column** to preserve original contact data.
2. **Column Renaming:** Renamed the newly generated column to `Domain Name`.
3. **Delimiter Extraction:** Selected `Domain Name`, navigated to `Transform` > `Extract` > `Text Between Delimiters`. 
   * **Start Delimiter:** `@`
   * **End Delimiter:** `.`
   * *Result:* Extracted core strings like `adventure-works`.
4. **Data Cleaning & Standardization:** 
   * Used **Replace Values** to find all hyphens (`-`) and replace them with a single space (` `).
   * Applied `Transform` > `Format` > `Capitalize Each Word`.
   * *Result:* Standardized messy strings into clean corporate indicators (e.g., `Adventure Works`).
5. **Load:** Selected **Close & Apply** to update the data model.

---

## 📊 Phase 2: Analytics & Dashboard Design Strategy
To make the dashboard fully intuitive and eliminate the need for verbal explanations, the user interface was built around **Action Titles** (stating the conclusion rather than the column names) and visual decluttering.

### 1. Unified KPI Banner (Top Header)
* **Total Customers:** Uses a distinct count metric on `CustomerKey` showing **18,149** unique customers.
* **Avg. Purchasing Power:** Displays the dynamic average of `AnnualIncome` (`$57,269`).
* **Home Owner Rate:** Uses a foundational DAX measure calculating a **67.53%** baseline across the global demographic.

### 2. Analytical Visualizations Grid
* **"Management & Professionals Drive Highest Income Tiers"** *(Horizontal Bar Chart)*: Ranks average income by occupation, highlighting the premium economic segments.
* **"70%+ of Customers Hold a College Degree or Higher"** *(Horizontal Bar Chart)*: Breaks down customer density by educational attainment, showcasing an educated consumer base.
* **"Married Customers Are Overwhelmingly Homeowners"** *(Grouped Column Chart)*: Compares `MaritalStatus` against `HomeOwner` status, showing a sharp correlation between married status and asset ownership.
* **"Perfect 50/50 Gender Split Across Customer Base"** *(Donut Chart)*: Tracks demographic distribution, showing a balanced `50.6% Male` to `49.4% Female` ratio (excluding `NA` values for noise reduction).

---

## 🧮 Phase 3: DAX Implementations
Explicit Data Analysis Expressions (DAX) measures were constructed to facilitate dynamic filter context recalculations across all cards.

### Total Customers Measure
```dax
Total Customers = COUNTROWS('AdventureWorks Customer Lookup')