# Project Overview

## Project Objective
The objective of this project was to design and develop a dynamic and interactive Car Sales Dashboard in Power BI that provides real-time visibility into critical sales KPIs. The dashboard enables stakeholders to:
 - Track sales performance using YTD, MTD, and YOY metrics
 - Compare current performance against previous periods (PTYD)
 - Analyse pricing trends and sales volume across time
 - Identify top-performing car by body styles, colours, and dealer regions
 - Explore sales data interactively to uncover trends, patterns, and growth opportunities

## Data Overview
The analysis is based on a structured car sales dataset capturing detailed transactional, customer, vehicle, and dealer information over a two-year period (2022–2023). The dataset was designed to support time-based performance analysis, product segmentation, and regional sales evaluation.

### Dataset Scope
 - Time Period: January 2022 – December 2023
 - Granularity: One record per car sale
 - Primary Use Case: Sales performance tracking, trend analysis, and KPI reporting

### Key Data Fields
The dataset includes a wide range of attributes grouped into the following categories:

#### Sales & Transaction Details

| Column Name | Description |
|-------------|-------------|
| Car_id | Unique identifier for each vehicle |
| Date | Transaction date |
| Price ($) | Sale price per vehicle |
| Units Sold | Derived sales quantity |

#### Customer Attributes

| Column Name     | Description |
|-----------------|-------------|
| Customer Name   | Full name of customer |
| Gender          | Gender (Male/Female) |
| Annual Income   | Customer’s reported annual income |
| Phone           | Customer contact phone number |

#### Vehicle Information

| Column Name   | Description |
|---------------|-------------|
| Company       | Brand of the vehicle (e.g., Ford, BMW, Nissan) |
| Model         | Specific vehicle model name |
| Body Style    | e.g Sedan, SUV, Hatchback, Passenger |
| Engine        | DoubleÂ Overhead Camshaft, Overhead Camshaft |
| Transmission  | Manual or Automatic |
| Color         | Exterior colour of the vehicle at the time of sale |

#### Dealer & Location Details

| Column Name   | Description |
|---------------|-------------|
| Dealer_Name   | Dealership of Purchase |
| Dealer_No     | Unique identifier assigned to each dealer |
| Dealer_Region | sales territory where the dealer operates |

These fields enable multi-dimensional analysis across time, vehicle characteristics, customer segments, and dealer regions.

### Date Dimension

To enable robust time-intelligence analysis, a dedicated Date Table was created using DAX.  The Date table includes the following derived attributes:

| Column Name   | Description |
|---------------|-------------|
| Year| 2022,2023
| Month| Car Purchase Month of the Year |
| MonthNo.| Jan=1, Feb=2, etc.
|WeekNo.| from 1 to 52
| Year Week| 2022-W1 to 2022-W52 and 2023-W1 to 2023-W52 |
| Year WeekSort| 202201 to 202252, 202301 to 202352 for sorting purpose |


This structure supports:
 - YTD, MTD, and YOY calculations
 - Weekly trend analysis
 - Proper chronological sorting in visuals

### Relationship Configuration

- Relationship: Date[Date] → Car Sales[Date]
- Cardinality: Many-to-One
- Cross-filter direction: Single

This modelling approach enables accurate time-based calculations while avoiding ambiguity and performance issues.

## Data Cleaning & Preparation

Before building the dashboard and analytical measures, to ensure accuracy, consistency, and analytical readiness, performed series of data cleaning and preparation process on the dataset.

### Data Validation & Standardisation

 - Performed Initial checks to validate the integrity of the dataset
 - Verified that each record represented a single car sale using Car_id as a unique identifier
 - Ensured all date values fell within the expected analysis window (2022–2023)

### Handling Missing & Inconsistent Data
Several data quality issues typical of transactional datasets were addressed:
 - Checked for missing or null values in key analytical fields such as Date, Price ($), Company, and Dealer_Region
 - Removed or corrected incomplete records that could distort sales, unit, or average price metrics

### Limitation
Approximately 250 records contained invalid values in the Model column where date values (e.g., 05/09/2020) were incorrectly recorded instead of car model names. Removing these rows risked biasing the analysis, so the data was retained.  As a result, the Model field was excluded from categorical visualisations but made available as a slicer, allowing users to filter the data without compromising the accuracy or clarity of dashboard visuals.

## Key Insights & Findings

### Overall Insight:
The analysis indicates that while sales growth was strong across all dealerships, performance was largely driven by increased volume rather than pricing gains. Variations in pricing behaviour and regional performance present opportunities to optimise sales strategies, improve underperforming regions, and replicate successful practices across the business.

### Analysis Findings

**1) Strong Year-over-Year Sales Growth:**
Total sales increased by $70.8M compared to the previous year, representing a 23.59% YOY growth rate, indicating a significant overall improvement in sales performance.

**2) Decline in Average Vehicle Price:**
Despite the increase in total sales, the average selling price declined by 0.79%, suggesting that revenue growth was primarily driven by higher sales volume rather than increased pricing.

**3) Increase in Units Sold:**
A total of 2.62K more vehicles were sold compared to last year, reflecting a 24.57% increase in units sold, reinforcing the strong demand observed during the year.

**4) Weekly Sales Performance Peaks:**
Week 37 recorded the highest sales of the year, generating more revenue than any other week. Sales volumes in weeks 46, 48, 49, and 50 were also comparably high. This pattern suggests the presence of effective sales strategies, promotions, or market conditions during these periods that could be analysed and replicated to drive future growth.

**5) Body Style Performance:**
SUVs were the top-performing body style, contributing nearly $100M in total sales, followed closely by Hatchbacks with approximately $83M. In contrast, Hardtops underperformed, indicating a potential need to reassess inventory strategy or customer demand for this category.

**6) Colour Preferences:**
Pale White vehicles consistently generated the highest sales across both years, highlighting a clear customer preference. Conversely, Red vehicles underperformed, suggesting lower demand or potential pricing and marketing challenges.

**7) Dealer-Level Performance Variation:**
Dealers in Austin and Janesville achieved the strongest sales performance during the year. In contrast, Middlestown, Pasco, and Greensville lagged behind, indicating opportunities for targeted support, strategy optimisation, or resource reallocation in these regions.

**8) Manufacturer Sales Trends:**
Chevrolet emerged as the top-selling brand, followed closely by Dodge, a trend consistent across most dealerships. However, in Greensville, Middlestown, and Scottside, Ford outperformed Dodge, highlighting regional differences in brand preference.

**9) Pricing vs Volume Dynamics Across Dealerships:**
All dealerships recorded positive YOY sales growth ranging from 7.54% to 32.39%. However, YOY average price growth varied significantly, ranging from -7.85% to 4.11%. This suggests that some dealerships achieved higher sales volumes by selling at lower average prices, potentially reflecting differences in sales strategies, discounting practices, or salesperson effectiveness.

## Recommendations
Based on this analysis, I recommend that by combining inventory optimisation, pricing refinement, and region-specific strategies, CarGO USA can sustain sales growth while improving profitability and operational consistency across dealerships.

Here’s how you can make this happen;

**1) Replicate High-Performing Weekly Sales Strategies:**
Analyse sales activities, promotions, staffing levels, and inventory availability during Week 37 and Weeks 46, 48, 49, and 50, then replicate successful tactics during lower-performing periods. These weeks consistently generated the highest revenue, indicating that specific operational or promotional factors positively influenced sales performance.

**2) Optimise Pricing Strategy Without Sacrificing Volume:**
Review discounting and pricing practices across dealerships, particularly where average prices declined despite strong sales growth, to identify opportunities to improve margins without reducing demand. Sales growth was driven primarily by increased units sold rather than higher prices, suggesting room to refine pricing strategies for better profitability.

**3) Align Marketing Efforts With Customer Colour Preferences:**
Focus marketing campaigns and showroom availability on high-demand colours, particularly Pale White, while evaluating whether underperforming colours such as Red require pricing adjustments or reduced stock levels. Colour-based sales analysis shows consistent customer preferences that can be leveraged to improve conversion rates and reduce slow-moving inventory.

**4) Strengthen Underperforming Dealer Regions:**
Provide targeted support to Middlestown, Pasco, and Greensville dealerships through:
   - Sales training
   - Performance benchmarking
   - Localised promotional strategies

   These regions consistently underperformed relative to others, indicating opportunities for improvement through targeted intervention.

**5) Leverage Best-Practice Dealerships as Performance Benchmarks:**
Use high-performing dealerships such as Austin and Janesville as benchmarks to:
   - Identify successful sales tactics
   - Share best practices across other regions
   - Standardise high-impact processes

   These dealerships demonstrated strong and consistent sales performance, making them ideal reference points for improving overall business results.

**6) Adjust Brand Strategy by Region:**
Align manufacturer partnerships and promotional strategies with regional brand preferences, particularly in areas where Ford outperforms Dodge, such as Greensville, Middlestown, and Scottside. Brand performance varies by region, suggesting that a uniform national strategy may not be optimal.

**7) Balance Sales Volume With Salesperson Effectiveness:**
Investigate whether dealerships with declining average prices are compensating through discount-driven sales and assess the role of salesperson effectiveness in these outcomes. Wide variation in YOY average price growth suggests differences in negotiation strategies, discounting behaviour, and sales execution.

## Tools & Technologies Used
 - Power BI
 - Power Query
 - DAX

## How This Project Demonstrates My Skills
 - Data cleaning
 - Modelling
 - Analysis
 - Visual storytelling
 - Business reasoning



