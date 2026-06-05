### LogiRoute Analytics - Logistics Performance Dashboard

Welcome to the **LogiRoute Analytics Dashboard** repository! This project is a comprehensive data analytics and business intelligence solution designed for a modern logistics and supply chain ecosystem. It tracks operations across delivery orders, fleet vehicles, regional hubs, and workforce (drivers) performance.

---

#### 🚀 Project Overview

The goal of this project is to transform raw logistics data into actionable business insights. The solution features interactive, multi-view Power BI dashboards that empower management to identify operational bottlenecks, track delivery performance, manage driver efficiency, and control vehicle reliability.

#### Key Metrics Tracked (KPIs)
* **Total Orders:** Tracks monthly order volumes and Month-over-Month (MoM) growth/decline.
* **On-Time Delivery Rate (%):** Monitors SLA compliance and tracks service level fluctuations.
* **Customer Satisfaction Score (CSAT):** Captures customer feedback trends to measure service quality.
* **Average Delivery Duration:** Evaluates processing and transit times in hours to optimize delivery routes.

---

#### 📊 Dashboard Views

The solution is divided into strategic layouts, each focusing on a core branch of the logistics workflow:

#### 1. Operations Overview 
Provides a macro-level overview of business success. It uses modern **KPI Card Visuals** with detailed conditional formatting (e.g., automated Red/Green indicators for MoM growth rules) to compare current performance directly against the previous month.

#### 2. Hubs Overview
* **Processed vs. Capacity Analysis:** Identifies whether regional hubs are working above or below their capacity limit.
* **Hub Turnaround Rankings:** Highlights top-performing hubs and isolates bottlenecks in processing times.
* **Daily Processing Time:** Tracks daily hours spent per hub to speed up turnaround cycles.

#### 3. Drivers Overview
* **Experience vs. Performance:** Connects a driver's Years of Experience (YoE) against their customer star ratings using scatter visualization.
* **Driver Performance Profiles:** Features dedicated profiling cards where managers can view a dynamic textual summary of a single driver's operational footprint (Hire Date, YOE, Total Deliveries, and Ratings).

#### 4. Vehicles Overview
* **Predictive Maintenance Signals:** Utilizes scatter plots to evaluate the correlation between Vehicle Age and breakdown incident frequencies.
* **Utilization Metrics:** Compares order volumes across different vehicle models and active availability status.

---

#### 🛠️ Data Architecture & Modeling

The project employs a star schema connecting transactional data with structural dimensions[cite: 2]:
* **Orders (Fact Table):** Order states (Delivered, Delayed, Cancelled), processing hours, delay reasons, and key foreign keys.
* **Drivers (Dimension):** Driver names, hiring metrics, employment structures, and tenure.
* **Vehicles (Dimension):** Maintenance frequencies, purchase history, and reliability states.
* **Date Table (Dimension):** A continuous date calendar facilitating complex Time Intelligence analysis.

---

#### ⚙️ Data Transformation (Power Query)

To guarantee flawless analytical calculations, the core data model went through standard ETL normalization phases:
* **Locale-Aware Date Standardization:** Standardized mixed chronological text string patterns (e.g., converting `DD-MM-YYYY` text string formats into default platform-recognized `Date` types using **UK/Bangladesh regional Locales** to prevent calculation errors and system crashes).
* **Missing Record Imputation:** Eradicating data anomalies in delivery fields and structuring data type rules strictly across all primary endpoints.

---

