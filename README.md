### LogiRoute Analytics - Logistics Performance Dashboard

Welcome to the **LogiRoute Analytics Dashboard** repository! This project is a comprehensive data analytics and business intelligence solution designed for a modern logistics and supply chain ecosystem. 

#### 🚀 Project Overview

The goal of this project is to transform raw logistics data into actionable business insights. The solution features interactive, multi-view Power BI dashboards that empower management to identify operational bottlenecks, track delivery performance, manage driver efficiency, and control vehicle reliability.

#### Key Metrics Tracked (KPIs)

* **Total Orders:** Tracks monthly order and Month-over-Month (MoM) growth/decline.
* **On-Time Delivery Rate (%):** Monitors SLA compliance and tracks service level fluctuations.
* **Customer Satisfaction Score (CSAT):** Captures customer feedback trends to measure service quality.
* **Average Delivery Duration:** Evaluates processing and transit times in hours to optimize delivery routes.


#### 📊 Dashboard Views

The solution is divided into strategic layouts, each focusing on a core branch of the logistics workflow:

#### 1. Operations Overview 

Provides a macro-level overview of business success. It uses modern **KPI Card Visuals** with compare current performance directly against the previous month.

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

### Execution Steps

#### 1. Data Ingestion
- Import `Orders`, `Hubs`, `Drivers`, and `Vehicles` tables into Power BI.

#### 2. Data Transformation
- Fix `Actual Delivery Date` using **Locale Settings**.
- Remove broken type conversion steps.
- Handle missing values and clean data issues.

#### 3. Data Modeling
- Build a **Star Schema** using ID keys.
- Create a **Date Calendar** table for time-based analysis.

#### 4. DAX Measures
- Create KPIs:
  - Total Orders
  - On-Time Delivery Rate (%)
  - Average Delivery Time
  - CSAT (%)
- Develop **MoM Growth** measures.
- Create dynamic titles and text callouts.

#### 5. Dashboard Design
- Add side navigation and global filters.
- Build **Overview Dashboard** with KPI cards.
- Create dedicated pages for:

  - Hubs Analysis 
  - Driver Performance
  - Vehicle Performance

#### 6. Formatting & Optimization
- Apply conditional formatting for KPI trends.
- Improve layout, alignment, and visual consistency.


### 


