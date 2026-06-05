### LogiRoute Analytics - Logistics Performance Dashboard

[![Play video](video-play-button.svg)](Video.mp4)

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


#### DAX Measures & Calculated Columns

##### Core KPIs

```DAX
Total Orders = COUNT(Orders[Order Date])

Delivered Orders =
CALCULATE([Total Orders], Orders[Order Status] = "Delivered")

On Time Orders =
CALCULATE(
    [Total Orders],
    Orders[Order Status] = "Delivered",
    Orders[Is On Time] = TRUE()
)

On Time Delivery Rate =
[On Time Orders] / [Delivered Orders]

Delayed Delivery =
CALCULATE(
    [Total Orders],
    Orders[Order Status] = "Delivered",
    Orders[Is On Time] = FALSE()
)

Delayed Delivery Rate =
[Delayed Delivery] / [Delivered Orders]

Average Delivery Time(Hrs) =
AVERAGE(Orders[Delivery Time Hours])

CSAT Satisfied Orders =
CALCULATE(
    [Total Orders],
    Orders[Customer Satisfaction Score] >= 4
)

CSAT % =
[CSAT Satisfied Orders] / [Total Orders]
```

##### Previous Month (PM) Measures

```DAX
PM Orders =
CALCULATE(
    [Total Orders],
    DATEADD('Date Table'[Date], -1, MONTH)
)

PM On Time Delivery Rate =
CALCULATE(
    [On Time Delivery Rate],
    DATEADD('Date Table'[Date], -1, MONTH)
)

PM CSAT =
CALCULATE(
    [CSAT %],
    DATEADD('Date Table'[Date], -1, MONTH)
)

PM Avg Delivery Time =
CALCULATE(
    [Average Delivery Time(Hrs)],
    DATEADD('Date Table'[Date], -1, MONTH)
)
```

##### Month-over-Month (MoM) Measures

```DAX
MOM Orders % =
DIVIDE(
    [Total Orders] - [PM Orders],
    [PM Orders]
)

MOM On Time Delivery % =
DIVIDE(
    [On Time Delivery Rate] - [PM On Time Delivery Rate],
    [PM On Time Delivery Rate]
)

MOM CSAT % =
DIVIDE(
    [CSAT %] - [PM CSAT],
    [PM CSAT]
)

MOM Avg Delivery % =
DIVIDE(
    [Average Delivery Time(Hrs)] - [PM Avg Delivery Time],
    [PM Avg Delivery Time]
)
```

##### Driver Information Measures

```DAX
YoE =
"YOE: "
    & SELECTEDVALUE(Drivers[Experience Years], "N/A")
    & " Years"

No of Drivers =
"No of Drivers: "
    & COUNT(Drivers[DriverID])

Hire Date Title =
"Hire Date: "
    & SELECTEDVALUE(Drivers[Hire Date])

Drivers Title =
SELECTEDVALUE(
    Drivers[DriverName],
    "All Drivers"
)
    & " made "
    & [Total Orders]
    & " Deliveries in "
    & [Year Month Title]
```

##### Rating Measure

```DAX
Star Rating =
REPT(
    UNICHAR(9733),
    AVERAGE(Drivers[Performance Rating])
)
&
REPT(
    UNICHAR(9734),
    5 - AVERAGE(Drivers[Performance Rating])
)
```

##### Date Table Columns

```DAX
Day =
FORMAT('Date Table'[Date], "ddd")

Day NO =
WEEKDAY('Date Table'[Date], 2)

Month =
FORMAT('Date Table'[Date], "mmmm")

Month No. =
MONTH('Date Table'[Date])

Year =
YEAR('Date Table'[Date])
```

### Conclusion

This dashboard provides a comprehensive view of logistics operations by tracking order volume, delivery performance, customer satisfaction, driver efficiency, and vehicle utilization. Through interactive visualizations, KPI monitoring, and time-based analysis, stakeholders can identify operational bottlenecks, measure performance trends, and make data-driven decisions to improve overall delivery efficiency and customer experience.

