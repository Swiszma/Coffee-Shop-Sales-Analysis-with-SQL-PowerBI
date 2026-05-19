# Coffee-Shop-Sales-Analysis-with-SQL-PowerBI
End-to-end transformation of 149k raw coffee transactions into strategic growth. Uses a Dual-Layer Validation workflow (MySQL ETL + Power BI) to optimize revenue, staffing, and inventory for a multi-location New York City franchise. Engineered for high-precision diagnostic storytelling and outstanding results.


### Table of Contents ###
[Project Overview and Business Task](project_overview_and_business_tas)

[Strategic Objectives](strategic_objectives)

[Data Sourcing and Integrity](data_sourcing_and_integrity)

[Data Engineering and ETL](data_engineering_and_etl)

[SQL Analysis](SQL_analysis)

[Power BI Dashboard Architecture](power_bi_ashboard_architecture)

[Strategic Recommendations](strategic_recommendations)

## Project Overview and Business Task ##
#### Welcome to the Coffee Shop Sales Growth Case Study. ####
This project analyzes six months of transactional data from a multi-location coffee franchise in New York City (NYC). The goal is to transform 149,116 rows of raw, item-level data into a strategic diagnostic tool that provides the C-Suite (Executive Leadership) and Operations Managers with total visibility into revenue velocity, staffing bottlenecks, and product performance.

### The Business Task ###
The core objective is to identify growth opportunities and operational inefficiencies. Specifically, the analysis must answer:
- How is Revenue trending Month-over-Month (MoM)?
- Which hours of the day represent the "Golden Window" for staffing?
- Which product categories drive the highest profit margins vs. volume?

### The Analyst's Approach ###
Rather than relying on basic spreadsheet summaries, a robust Dual-Layer Validation pipeline was engineered:
- MySQL (Workbench): Engineered advanced SQL queries to handle Extract, Transform, Load (ETL) processes, ensuring financial precision (pennies) and temporal accuracy.
- Microsoft Power BI: Architected an interactive, executive-facing Business Intelligence (BI) dashboard utilizing custom DAX (Data Analysis Expressions) measures and a native matrix calendar heatmap.

## Strategic Objectives ##
#### Ask Phase ####
To ensure the analysis hit the "North Star" of the business, I defined the project via three stakeholder lenses:
- C-Suite Executives: Need high-level revenue trajectory and Month-over-Month (MoM) growth benchmarks.
- Operations Managers: Need granular "Staffing Pulse" data (Sales by Hour/Day) to optimize labor costs.
- Inventory Leads: Need to identify "Hero Products" to prevent stockouts and optimize supply chain orders.
- Strategic Note: I identified an "Invisible Leak" early: the raw data lacked a total_sales column. I decided to engineer this in the SQL layer to ensure 100% financial integrity before the data touched the UI (User Interface).

## Data Sourcing and Integrity ##
#### Prepare Phase & the Data Source ####
The primary dataset consists of 149,116 rows of transactional data spanning January 2023 to June 2023 across three locations: Astoria, Hell's Kitchen, and Lower Manhattan.
##### ROCCC Evaluation: #####
- Reliable (HIGH): First-party transactional logs.
- Original (HIGH): Direct internal business data.
- Comprehensive (MEDIUM): Required engineering for total_sales.
- Current (HIGH): Covers the most recent 6-month fiscal period.
- Cited (HIGH): Well-documented internal source.

## Data Engineering and ETL ##
#### Process Phase ####
To ensure maximum scalability and transparency, I utilized a multi-tool Extract, Transform, Load (ETL) approach.
#### Step 1: SQL Surgical Transformation ####
Raw dates were imported as TEXT to prevent the "Date Trap" (data loss during conversion). I then executed:
- Date/Time Casting: Utilized STR_TO_DATE() to convert DD/MM/YYYY strings into native SQL DATE and TIME objects.
- The "Penny Precision" Fix: Converted unit_price from DOUBLE to DECIMAL(10,2). This eliminated floating-point rounding errors that would skew C-Suite financial reports.
#### Step 2: Feature Engineering ####
- Total Sales: Manifested the missing revenue metric: transaction_qty * unit_price.
- Header Sanitization: Used ALTER TABLE to remove "Invisible Dust" (Byte Order Marks and leading spaces) from column headers to prevent "Unknown Column" errors during analysis.

## SQL Analysis ##
#### Analyze Phase ####
I bypassed "cookie-cutter" reporting for deep-dive SQL exploration:
- The Velocity Engine: Used LAG() and OVER() Window Functions to calculate Month-over-Month (MoM) growth.
- Discovery: Revenue surged by 31.8% in May, identifying a significant seasonal shift.
- The "High-Jump" Benchmark: Engineered a subquery to compare daily sales against the Monthly Average Line.
- Discovery: This allowed me to label days as "Above Average" or "Below Average" for instant operational diagnostics.
- Hourly Pulse: Aggregated 149k rows into 24 "Hourly Cups."
- Discovery: Identified the 8:00 AM – 10:00 AM window as the most profitable 120 minutes of the day ($19K+ revenue).
  
Find SQL Analysis and Queries [here](https://drive.google.com/file/d/1k0BbyzWwQmRM9Gaf7L1eZwUJabifBOX6/view?usp=drive_link)

## Power BI Dashboard Architecture ##
#### Share Phase ####
##### Data Modeling #####
I established a Star Schema by building a dedicated Dim_Date table. This "Master Clock" ensured our MoM logic remained unbroken even during holidays or $0 sales days.

#### Advanced UI/UX Features ####
- The "Plus-Sign" Indicator: Engineered DAX strings (▲ +6.2% | +9.8K Vs LM) to provide the CEO with "Velocity" (Percentage) and "Weight" (Dollars) in a single glance.
- The "Hot Product" Tooltip: Integrated a TOPN(1) measure into the Hourly Heatmap. Hovering over any peak hour reveals the #1 selling product (e.g., Barista Espresso) for that specific window.
- Native Matrix Heatmap: Built a custom calendar grid that "glows" based on sales volume and indicates sales, quanties, and orders when hovered on, allowing managers to visually identify high-performing days without reading a single table.

<img width="1227" height="747" alt="image" src="https://github.com/user-attachments/assets/971f2a7a-77b8-46c5-8423-6d24bc5756ad" />


## Strategic Recommendations ##
#### Act Phase ####
##### Executive Summary (Final Conclusion) #####
The franchise is in a high-growth phase, doubling revenue from January to June. However, growth is heavily dependent on a two-hour morning window. To sustain this trajectory, I recommend:
1. The "Peak-Sync" Staffing Strategy
- The Data: 8 AM – 10 AM contributes 30% of daily revenue.
- The Action: Schedule "Lead Baristas" specifically for this window and mandate equipment calibration at 7:30 AM to ensure zero downtime.
2. The "Sunset Scone" Bundle
- The Data: Sales drop 60% after 4:00 PM, while Bakery items remain the most resilient category.
- The Action: Launch a "Coffee + Pastry" afternoon bundle to pull revenue into the quiet hours and increase Average Transaction Value (ATV).
3. The "Astoria Playbook" Replication
- The Data: Astoria leads the franchise in growth velocity (+30.8% MoM).
- The Action: Replicate Astoria's local marketing and service SOPs (Standard Operating Procedures) in the Lower Manhattan location to stabilize its growth curve.
4. Espresso Safety Protocol
- The Data: Barista Espresso drives nearly $22K of monthly revenue.
- The Action: Establish a 25% "Safety Stock" for espresso beans and implement monthly preventative maintenance on machines to protect the business's primary revenue engine.

##### Analyst's Final Note: #####
This project demonstrates the power of Dual-Layer Validation. By mastering the SQL backend before building the Power BI frontend, I ensured a solution that is not only beautiful but mathematically bulletproof.
