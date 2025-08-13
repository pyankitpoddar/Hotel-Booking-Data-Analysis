# 🏨 Hotel Booking Data Analysis

## 📌 Project Overview
This project analyzes hotel booking performance data for multiple **Atliq Hotels** properties across different cities and time periods.  
It combines booking transactions, property details, room capacities, and calendar attributes to measure **occupancy percentages**, **revenue performance**, and **guest behavior**.

The goal is to prepare **clean, structured datasets** for business decision-making related to **occupancy trends, revenue analysis, and cancellation patterns**.

---

## 📂 Data Sources

The notebook works with several datasets (merged during processing):

1. **Bookings Data**
   - Columns: `booking_id`, `property_id`, `booking_date`, `check_in_date`, `checkout_date`, `no_guests`, `room_category`, `booking_platform`, `ratings_given`, `booking_status`, `revenue_generated`, `revenue_realized`
   - Contains booking-level transactions for all properties.

2. **Property Details**
   - Columns: `property_id`, `property_name`, `category`, `city`
   - Provides meta-information about hotel properties.

3. **Room Capacity / Occupancy Data**
   - Columns: `property_id`, `check_in_date`, `room_category`, `successful_bookings`, `capacity`
   - Enables occupancy percentage calculations.

4. **Date Dimension**
   - Columns: `date`, `mmm yy`, `week no`, `day_type`  
     (e.g., weekend vs weekday, week number, month-year)

---

## 🛠️ Data Cleaning & Preparation

Key preprocessing & transformation steps performed:

- **Negative Guest Counts** → Detected cases (e.g., `-3`, `-17`) needing validation or anomaly tagging.
- **Large Revenue Outliers** → Noted revenue values in millions, possible data entry scaling issues.
- **Merging Datasets**:
  - Booking data with property details
  - Booking data with calendar info
  - Occupancy metrics with room metadata
- **Calculated Fields**:
  - `occ_pct` (Occupancy %): `(successful_bookings / capacity) * 100`
  - Room Class mapping (e.g., `RT1` → Standard)
  - Monthly, weekly breakdowns (`mmm yy`, `week no`)
  - Weekend vs weekday segmentation
- **Data Type Fixes**:
  - Converted date strings to `datetime`
  - Uniform date formats (`YYYY-MM-DD`)

---

## 📊 Metrics & Insights Generated

1. **Occupancy Analysis**
   - By property
   - By room category
   - By date/week/month
   - Weekend vs weekday performance

2. **Revenue Analysis**
   - `revenue_generated` vs `revenue_realized`
   - High-value transactions flagged for review
   - Loss from cancellations & no-shows

3. **Guest Behavior**
   - Ratings distribution by booking platform
   - No. of guests per booking & anomalies

4. **Operational Efficiency**
   - Overbookings & capacity utilization
   - City-level performance comparison

---

## 📈 Example Findings

- Properties like **Atliq Bay** and **Atliq Exotica** posted **90%+ occupancy** on certain dates.
- Some records had **occupancy above 100%**, indicating overbooking or data errors.
- Revenue discrepancies noted when `revenue_generated` >> `revenue_realized`.
- Weekend bookings tend to have slightly higher occupancy rates than weekdays.


---

## 📦 Final Outputs

Generated datasets ready for visualization.

1. **Property-Level Occupancy Table**
2. **City-Wise Revenue Trends**
3. **Room Category Performance Table**
4. **Date Dimension Mapping Table**



