# Crime Analysis Dashboard – README

## Overview
The Crime Analysis Dashboard is an interactive Tableau workbook that summarizes crime incidents across multiple European countries between September 2021 and November 2023. It provides a consolidated view of crime volume, temporal patterns, geographic distribution, crime types, and resolution performance to support both strategic and operational decision‑making in a policing context.

<img
  width="2127"
  height="1201"
  alt="OLTP diagram"
  src="./Crime Analysis Dashboard.png"
/>

## Data Sources

- **Fact table – `Crimes-Data.xlsx`**  
  Each row is a single crime incident with fields including `Crime ID`, `Crime Date`, `Country`, `Crime Type ID`, `Resolved` (0/1), `People Involved`, and `Crime DateTime`.

- **Lookup table – `Other-Data.xlsx`**  
  Maps `Crime Type ID` values to readable descriptions such as *Violence and Sexual Offences*, *Anti‑Social Behaviour*, and *Vehicle Crime*, plus supporting metadata used for labels and grouping.

### Key derived fields in Tableau

- `Year`, `Month`, `Weekday` from `Crime Date`.  
- Hourly buckets (e.g., `9:00 PM–11:59 PM`) from `Crime DateTime`.  
- Resolution metrics: resolved flag, resolution rate, unresolved share.  
- Top‑N crime‑type ranking driven by a parameter and index calculation.

## Target Users and Use Cases

**Primary users**

- Senior leadership and command staff.  
- Crime and intelligence analysts.  
- Operational planners and shift supervisors.

**Core use cases**

- Track year‑over‑year and month‑to‑month changes in crime volume.  
- Compare countries and crime types to prioritize interventions and specialist units.  
- Identify high‑risk time windows (hour, weekday, month) for staffing decisions.  
- Monitor resolution rates and unresolved backlogs by country and period.

## Dashboard Layout and Visuals

### 1. Yearly Crimes Bar Chart (Top Left)
Shows total crimes by year with labels and variance indicators.  
**Questions answered:** “How has total crime volume changed each year?” “Which year is highest or lowest?”  
**Why bars:** A shared baseline makes annual totals and year‑over‑year differences instantly comparable, which is ideal when there are only a few discrete years.

### 2. Headline KPIs (Below Yearly Bars)
Displays total number of crimes and key resolution metrics (overall resolution rate and unresolved share).  
**Questions answered:** “What is the current total crime load?” “What proportion of incidents are resolved vs unresolved?”  
**Why KPIs:** Large single‑value indicators surface critical numbers without axes, supporting quick briefings and performance checks.

### 3. Monthly Trend Line (Top Center)
Line graph of crimes by month across the analysis window, with month‑over‑month percentage changes.  
**Questions answered:** “How does crime fluctuate month to month?” “When do peaks and dips occur?”  
**Why line:** Emphasizes continuity and seasonality, making spikes (e.g., October) and sustained changes obvious.

### 4. Resolution Narrative Text (Center)
Short narrative summarizing the overall resolution rate and unresolved share.  
Provides a plain‑language interpretation of the KPI figures for non‑technical stakeholders.

### 5. Crime by Country Map (Top Right)
Proportional‑symbol map showing number of crimes per country, with larger/red bubbles for top countries.  
**Questions answered:** “Which countries have the highest crime volumes?” “How do countries compare spatially?”  
**Why map:** Uses geography; bubble size and position make regional hotspots and outliers more intuitive than a table.

### 6. Crime by Type Bar Chart with Top‑N (Right Middle)
Horizontal bars by crime type (e.g., Violence and Sexual Offences, Anti‑Social Behaviour), controlled by a Top‑N parameter slider.  
**Questions answered:** “Which crime categories are most common?” “How concentrated is crime in the top few offense types?”  
**Why bars:** A sorted bar chart clearly ranks categories by volume, supporting prioritization and specialist deployment.

### 7. Crime by Time Range Bar Chart (Bottom Left)
Horizontal bars for hourly buckets (e.g., `9:00 PM–11:59 PM`, `12:00 AM–2:59 AM`).  
**Questions answered:** “At what times of day are crimes most frequent?” “How much higher are late‑night incidents versus early morning?”  
**Why horizontal bars:** Facilitate comparison across many time buckets with readable labels and a shared baseline, highlighting night‑time concentration.

### 8. Month–Weekday Heatmap (Bottom Center)
Grid of weekday vs month, colored by crime count.  
**Questions answered:** “Which weekday–month combinations are highest?” “Do weekday patterns vary across the year?”  
**Why heatmap:** Displays two categorical time dimensions simultaneously; color intensity quickly exposes hotspots without scanning many numbers.

## Interactivity

- **Crime Date Range filter**  
  Global filter that restricts all views to a selected period (e.g., single year, quarter, or operation window) to assess initiatives or seasonal changes.

- **Country filter & map selection**  
  Dropdown and map click for focusing on one or more countries. Supports cross‑country benchmarking and jurisdiction‑specific deep dives into trends and patterns.

- **Resolved (1) / Unresolved (0) slider**  
  Filters incidents by resolution status to analyze unresolved backlogs or evaluate clearance performance on resolved cases.

- **Marks as global filters**  
  Clicking a year bar, country bubble, or crime‑type bar filters all other charts, enabling drill‑down paths such as `2023 → Italy → violent crimes`.

- **Heatmap metric/subset toggles**  
  Parameter‑driven toggles (where configured) switch the heatmap between counts and rates or focus it on specific crime types, revealing whether hotspots are volume‑driven or offense‑specific.

- **Top‑N crime parameter**  
  Slider controlling how many leading crime types are displayed (e.g., top 5 vs top 10), useful for concise executive summaries or detailed analytical views.

## How to Use

1. Start at the **yearly bar chart** and **headline KPIs** to understand overall volume and resolution levels.  
2. Set the **date range**, **country**, and **resolved/unresolved** filters to the scope relevant to your question.  
3. Use the **country map** and **crime type bars** to identify high‑volume locations and offense categories, refining with the Top‑N slider as needed.  
4. Examine the **time‑range bars** and **month–weekday heatmap** to locate operational hotspots for patrol and investigative planning.  
5. Drill into specific segments by clicking marks and adjusting parameters, then export views or screenshots for reports and presentations.
