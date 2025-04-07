
# 🚚 Porter Booking Analysis Dashboard (Google Sheets)

This dashboard visualizes and analyzes **Porter booking data** used to transport **breakdown vehicles** to the nearest hub. It was built using **Google Sheets**, leveraging pivot tables, filters, and dynamic `QUERY` formulas to provide comprehensive insights into daily operations.

## 📊 Dashboard Highlights

The dashboard provides insightful visualizations and tables across the following dimensions:

- 📍 **Hub Location**: Number of bookings and total Porter amount spent per hub.
- 🛠️ **Issue Type**: Analysis of common breakdown issues (e.g., Motor, IOT, Controller).
- 🚗 **Vehicle Type**: Booking patterns by different electric bike types.
- 👨‍🔧 **Advisor Name**: Who raised the most bookings.
- 🧰 **Technician Name**: Technician-wise job count.
- 📅 **Booking Day**: Trends based on the day of the week.

Each view supports performance tracking and helps understand workload distribution and cost efficiency.

## 🔍 Data Source & Transformation

The raw data includes details like:
- Request date, vehicle number, issue type
- Hub and drop locations
- Porter amount charged
- Advisor and technician names

To power the dashboard, formulas such as `QUERY()` were used extensively. For example:

```
=QUERY('Raw Data'!$A2:$V, 
"SELECT G, COUNT(G), AVG(I), SUM(L)
 WHERE G IS NOT NULL 
 AND P >= DATE '"&TEXT(C2,"yyyy-mm-dd")&"' 
 AND P <= DATE '"&TEXT(C3,"yyyy-mm-dd")&"' 
 AND V = TRUE
 GROUP BY G 
 ORDER BY COUNT(G) DESC 
 LABEL 
   G 'Hub Location', 
   COUNT(G) 'Number of Cases', 
   AVG(I) 'Avg. Distance in KM', 
   SUM(L) 'Porter Amount'")
```

This dynamic filtering allows the dashboard to be **date-range specific**, with switchable **daily, monthly, and custom time filters**.

## 📁 Files and Screenshots

The repository includes:
- Screenshots of pivot tables and filters
- Raw data structure for reference
- Visualizations for trends by category

## ✅ Features

- **Interactive Filters**: Switch between views for daily/monthly/between-date analysis.
- **Automated Calculations**: Unique date counts, weekday breakdowns, booking totals.
- **Clear Visual Insight**: Tables + charts show top contributors and cost centers.
- **Scalable Design**: Easily extendable to include more data or additional hubs.

## 📌 Use Case

Perfect for:
- **Operations managers** analyzing booking behavior
- **Fleet coordinators** planning porter logistics
- **Data analysts** exploring hub performance & breakdown causes


