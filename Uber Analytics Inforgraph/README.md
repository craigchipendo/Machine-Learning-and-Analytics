# Uber Ride Analytics

## Overview
This project analyzes operational and financial patterns in Uber ride data using R and produces an infographic-style summary of key insights. The analysis focuses on revenue realized vs. revenue lost, revenue distribution by payment method, vehicle-type performance, and cancellation behavior over time of day and weekday. The final outputs are a set of ggplot2 charts and a composite infographic (`Inforgraph.jpg`) suitable for presentations and executive summaries.

## Data
The project uses the **Uber Ride Analytics Dataset 2024** (Kaggle). The raw dataset contains:

- Booking value
- Ride distance
- Booking status
- Date and time
- Vehicle type
- Payment method

The R Markdown script performs robust cleaning to handle inconsistent column names, string `"null"` values, and multiple missing-value encodings, and then derives standardized variables such as `vehicle_type`, `booking_value`, `distance`, and `booking_status`.

## Repository Structure

- `Uber_analytics_viz.Rmd`  
  R Markdown report that:
  - Cleans and normalizes the input data  
  - Engineers time-based features (hour, weekday, month)  
  - Flags completed vs. cancelled bookings  
  - Aggregates metrics for vehicle performance, revenue, and cancellations  
  - Generates all charts used in the infographic via **ggplot2** and **gt**

- `Inforgraph.jpg`  
  Final infographic combining the main charts and the vehicle performance table into a single visual summary.

(If you are using a different folder layout, adjust the paths in the Rmd accordingly.)

## Data Processing Pipeline

### 1. Normalization and Cleaning
- Standardizes alternative column names (e.g., `Vehicle.Type` vs `Vehicle Type`).
- Converts various “missing” tokens (`"null"`, `"NA"`, `"N/A"`, `"-"`, `"."`, empty strings) to proper `NA`.
- Parses booking value as numeric (`booking_value`) and converts ride distance to numeric (`distance`).
- Normalizes booking status text and creates a logical `completed` flag for completed rides.

### 2. Vehicle-Level Aggregation
For each `vehicle_type` the script computes:

- `total_booking`: total booking value  
- `success_booking`: booking value from completed rides only  
- `avg_distance`: average trip distance  
- `total_distance`: total distance travelled  

It then adds emoji icons and a `vehicle_display` label and builds a formatted **gt** table titled **Vehicle Performance Summary**.

### 3. Time Feature Engineering
- Combines raw `Date` and `Time` strings and parses them into a POSIXct timestamp using multiple candidate formats.
- Derives:
  - `hour` (0–23)  
  - `weekday_name` (Monday–Sunday)  
  - `month` and `month_name`
- Creates an `is_cancelled` flag from a configurable set of statuses (e.g., *Cancelled by Driver*, *Cancelled by Customer*, *No Driver Found*, *Incomplete*).

### 4. Cancellation Metrics
Using a helper function `count_rate()`, the script computes:

- **Counts** and **cancellation rates** by:
  - Hour of day  
  - Weekday  
  - Month  
- A complete “weekday × hour” grid for the cancellation-rate heatmap, ensuring all combinations are present.

## Visualizations

The following visuals are generated and then assembled into the infographic:

1. **Revenue Realized vs. Revenue Lost**  
   - Bar chart comparing total revenue from completed bookings vs. potential revenue lost due to cancellations.  
   - Highlights the magnitude of revenue leakage relative to realized revenue.

2. **Total Revenue by Payment Method**  
   - Bar chart showing revenue by payment type (e.g., cash, credit card, wallet, UPI).  
   - Useful for understanding payment mix and informing payment-strategy decisions.

3. **Vehicle Performance Summary (gt Table)**  
   - Styled table summarizing, per vehicle type:
     - Total booking value  
     - Successful booking value  
     - Average distance travelled  
     - Total distance travelled  
   - Uses emoji icons and suffix formatting (K, M) for readability.

4. **Cancellations by Hour vs. Average Waiting Time**  
   - Column chart of cancellation counts by hour of day.  
   - Overlaid line showing average waiting time (minutes), revealing how cancellations change with wait time.

5. **Cancellation Rate Heatmap (Weekday × Hour)**  
   - Heatmap where color intensity encodes cancellation rate (%) for each weekday–hour combination.  
   - Identifies high-risk windows (for example, specific evening hours on certain weekdays) where operational improvements could reduce cancellations.

## How to Run

1. Open `Uber_analytics_viz.Rmd` in **RStudio** (or another R Markdown-capable environment).
2. Make sure the Uber dataset is available at the path expected in the Rmd. Update the `read_csv()`/`readr` call if necessary.
3. Install or load the required packages
4. In the Rmd, set the `SAVE` flag:
- `SAVE <- FALSE` to generate plots only in the knitted report.  
- `SAVE <- TRUE` to also write PNG files to the `charts/` directory.

5. Knit the document to PDF or HTML. This will:
- Execute the full data-cleaning and transformation pipeline.  
- Generate all charts and the **Vehicle Performance Summary** table.  
- Optionally save individual chart images.

## Using the Infographic

The combined infographic is intended for:

- Executive briefings on Uber ride performance and cancellations.  
- Product and operations reviews focused on vehicle mix, pricing, and service reliability.  
- Demonstrating end-to-end data wrangling and visualization capability in R (from raw CSV to polished infographic).




