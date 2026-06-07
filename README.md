# Enerdata & Enedis Renewable Energy Production Analysis (Power BI) ⚡

## 📌 Project Overview
As a Data Analyst at **Enerdata** (a firm specialized in energy data analysis), I was mandated by **Enedis** to deliver a comprehensive, dynamic, and interactive Power BI report for their *Networks Studies and Strategic Forecasting Department*. 

<img width="3171" height="1770" alt="Capture d’écran 2026-06-07 à 09 47 01" src="https://github.com/user-attachments/assets/0366484e-9f9d-447e-919e-a7a0eeb4e408" />

The core objective of this report is to monitor the evolution of the renewable energy production park connected to the Enedis distribution network (2020–2025), evaluate local energy mix trends, isolate high-potential geographical zones, and cross-reference capacity data with climate factors (temperatures and sunshine hours) provided by Météo France.

## ⚙️ Data Engineering & Modeling (Power Query & DAX)
The project required a robust ETL workflow and an optimized relational model built from four distinct sources (Excel, CSV, and TXT):

1. **Data Extraction & Transformation (Power Query):**
   - Cleaned historical production logs by eliminating technical columns (`Tranche`, `ID_type_Inj`, `Code Département`).
   - Standardized all naming conventions to uppercase and strictly enforced correct data types.
   - Cleansed and aggregated regional meteorological datasets from Data.Gouv.
2. **Relational Modeling (Star Schema):**
   - Developed a composite join key (`CLÉ_RÉGION_TRIMESTRE`) combining the Regional INSEE Code and the Quarter date to seamlessly map the facts table to meteorological dimensions.
   - Set up a double-sided cross-filtering direction between renewable production and historical temperatures to enable deep analytical fluidity.
   - Built an independent time-intelligence **Calendar Table** in DAX covering the full evaluation window.
3. **Advanced DAX Metrics:**
   - **Storage Rate:** Calculated the precise percentage of installations fitted with energy storage capabilities using `CALCULATE`, `SUM`, and `DIVIDE`.
   - **Theoretical Yield (MW/Day):** Created a climate adequation metric for 2024 by isolating Photovoltaic capacities and dividing them by regional sunshine thresholds.

## 📊 Dashboard Architecture & Navigation
The final `.pbix` deliverable is organized into a modular, business-oriented framework structured across specialized layers:

* **Global Filter Constraint:** A report-wide page filter was permanently applied to restrict calculations strictly to **End of Quarter (Fin de Trimestre)** thresholds. This constraint prevents double-counting and ensures that annual accumulations reflect precise year-end total capacities.
* **Page 1: Renewable Energy Production Tracking (`Suivi de production`)**
  - High-level KPIs showcasing Total Installations, Total Power Output (MW), and Storage ratios.
  - Slicer configurations restricted to single-selection years with targeted interaction blocks to lock specific historical comparative charts.
* **Page 2: Regional Deep Dive (`Détails par Région`)**
  - Integrated an advanced **Drill-through (Drill-out)** action directly on the `RÉGION` attribute, allowing strategic stakeholders to right-click any overview visual and immediately unlock an intra-regional breakdown showing department-level rankings and production mix splits.
* **Page 3: Climate Analysis & Photovoltaic Performance (`Analyse climatique`)**
  - Dedicated focus on solar productivity, cross-referencing regional temperature heatmaps with 2024 sunshine durations.
  - Implemented conditional color gradients to automatically highlight territories displaying the highest theoretical weather-to-energy yields.
* **Page 4: Business Commentary (`Commentaires`)**
  - Core analytical write-up outlining strategic investment recommendations, climate adequation findings, and project goals directly inside the report interface.

## 💻 Technical Highlights
- **Power BI Desktop:** Advanced data modeling, custom relational star schemas, and dashboard UX/UI design.
- **DAX Formulas:** Advanced aggregation filtering, conditional division, and time-intelligence setups.
- **Business Intelligence Consulting:** Translating technical electrical grid metrics (MW) and weather datasets into actionable investment roadmaps for ecological transition planners.

