# 🚗 Uber 2024 Analytics Dashboard - Power BI

[![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![DAX](https://img.shields.io/badge/DAX-0078D4?style=for-the-badge&logo=microsoftexcel&logoColor=white)](#)

## 📊 Project Overview

A comprehensive **management/operations dashboard** built for analyzing Uber's business performance using Power BI. This project transforms raw booking data into actionable insights for stakeholders, focusing on revenue optimization, cancellation analysis, and service quality metrics.

### 🎯 **Key Objectives**
- Analyze performance, cancellations, and demand patterns
- Track revenue streams across different vehicle types and locations  
- Monitor service quality through customer and driver ratings
- Identify operational bottlenecks and improvement opportunities

---

## 📈 **Dashboard Highlights**

### **Key Metrics (2024)**
- **Total Revenue**: ₹51.85M
- **Total Bookings**: 150K
- **Cancelled Bookings**: 38K
- **Average Customer Rating**: 4.40
- **Average Driver Rating**: 4.23

---

## 🗂️ **Data Structure**

**Data Source**: Single fact table `Uber_2024_Revenue` containing:

| **Category** | **Columns** |
|--------------|-------------|
| **Core Info** | date, time, booking_id, booking_status, booking_value, ride_distance |
| **Customer Data** | customer_id, customer_rating |
| **Vehicle Info** | vehicle_type, pickup_location, pickup_drop |
| **Cancellations** | cancellation_by_customer, cancellation_reason_by_customer, cancellation_by_driver, cancellation_reason_by_driver |
| **Service Quality** | incomplete_rides, incomplete_ride_reason, driver_rating, payment_method |
| **Metrics** | avag_vtat, avag_ctat |

---

## 🔍 **13 Key Performance Indicators (KPIs) Analyzed**

### **Revenue & Financial Analysis**
✅ Revenue distribution by vehicle type  
✅ Payment method breakdown and preferences  
✅ Top/Bottom performing drivers by revenue  
✅ High booking value customer identification  

### **Operational Excellence**
✅ Cancellation patterns by vehicle type  
✅ Booking status trends over time  
✅ Location-based booking analysis  
✅ Distance coverage by vehicle type  

### **Service Quality & Customer Experience**
✅ Customer and driver rating analysis  
✅ Cancellation and incomplete ride reasons  
✅ Regular customer identification (5+ bookings)  
✅ Time-based booking and cancellation patterns  

---

## 📱 **Dashboard Structure**

### **Page 1: Overview**
- **Total Revenue, Bookings, and Cancellations** (KPI Cards)
- **Monthly Revenue and Booking Trends** (Line Chart)
- **Booking Status Distribution** (Bar Chart)
- **Payment Method Revenue Analysis** (Horizontal Bar Chart)

### **Page 2: Vehicle Analysis**
- **Revenue by Vehicle Type** (Bar Chart)
- **Distance Coverage by Vehicle** (Column Chart)  
- **Vehicle Type Booking Share** (Tree Map)
- **Cancellation Analysis by Vehicle** (Stacked Bar Chart)

### **Page 3: Customer Insights**
- **Customer Rating Distribution** (Gauge Chart)
- **Payment Method Preferences** (Bar Chart)
- **Customer Cancellation Trends** (Line Chart)
- **Cancelled Rides by Customer** (Bar Chart)

### **Page 4: Driver Insights**
- **Driver Rating Analysis** (Gauge Chart)
- **Driver Cancellation Patterns** (Pie Chart)
- **Top Revenue-Generating Drivers** (Table)
- **Monthly Driver Cancellation Trends** (Line Chart)

---

## 🧮 **DAX Measures Implemented**

```dax
// Core Financial Metrics
Total Revenue = SUM('Uber_2024_Revenue'[booking_value])
Total Bookings = COUNTROWS('Uber_2024_Revenue')
Avg Revenue per Booking = DIVIDE([Total Revenue], [Total Bookings])

// Cancellation Analysis
Cancelled Bookings = CALCULATE(COUNTROWS('Uber_2024_Revenue'), 'Uber_2024_Revenue'[booking_status] = "Cancelled")
Customer Cancellations = CALCULATE(COUNTROWS('Uber_2024_Revenue'), 'Uber_2024_Revenue'[cancellation_by_customer] = "Yes")
Driver Cancellations = CALCULATE(COUNTROWS('Uber_2024_Revenue'), 'Uber_2024_Revenue'[cancellation_by_driver] = "Yes")

// Customer Segmentation
Regular Customers = CALCULATE(COUNTROWS('Uber_2024_Revenue'), [Customer Booking Count] > 5)

// Performance Metrics
Booking Share % = DIVIDE([Total Bookings], CALCULATE([Total Bookings], ALL('Uber_2024_Revenue')))
Total Distance = SUM('Uber_2024_Revenue'[ride_distance])

// Advanced Analysis
Lost Revenue from Driver Cancellations = CALCULATE([Total Revenue], 'Uber_2024_Revenue'[cancellation_by_driver] = "Yes")
```

---

## 🛠️ **Technical Implementation**

### **Tools & Technologies**
- **Microsoft Power BI Desktop** - Dashboard Development
- **DAX (Data Analysis Expressions)** - Custom Measures & Calculations
- **Power Query** - Data Transformation & Cleaning

### **Key DAX Functions Utilized**
- `SUM()`, `COUNT()`, `COUNTROWS()` - Aggregation functions
- `CALCULATE()`, `FILTER()` - Context modification
- `DIVIDE()` - Safe division with error handling
- `RANKX()` - Ranking calculations
- `ALL()` - Context removal for percentage calculations

---

## 📊 **Key Insights Discovered**

### **Revenue Analysis**
- **Auto vehicles** generate the highest revenue (₹12.87M)
- **UPI payments** dominate with ₹23M in transactions
- **Go Mini** vehicles show strong performance in the compact segment

### **Cancellation Patterns**
- **Customer cancellations (72%)** significantly outweigh driver cancellations (28%)
- **Auto vehicles** have the highest cancellation rates
- Seasonal patterns observed in monthly cancellation trends

### **Service Quality**
- **Customer rating average**: 4.40/5.0
- **Driver rating average**: 4.23/5.0
- Strong correlation between rating and booking frequency

---

## 📁 **Repository Structure**

```
📁 Uber-2024-Analytics-Dashboard/
├── 📄 Uber_2024_Analytics.pbix          # Main Power BI file
├── 📁 Screenshots/
│   ├── 🖼️ Overview_Page.jpg
│   ├── 🖼️ Vehicle_Analysis.jpg
│   ├── 🖼️ Customer_Insights.jpg
│   └── 🖼️ Driver_Insights.jpg
├── 📄 README.md                          # Project documentation
└── 📄 Data_Dictionary.md                 # Column descriptions
```

---

## 🚀 **How to Use**

### **Prerequisites**
- Microsoft Power BI Desktop (Latest Version)
- Basic understanding of Power BI interface

### **Steps**
1. **Download** the `.pbix` file from this repository
2. **Open** the file in Power BI Desktop  
3. **Interact** with filters and slicers to explore different dimensions
4. **Refresh** data connection if using live data sources

### **Navigation Guide**
- Use the **sidebar navigation** to switch between dashboard pages
- Apply **date filters** to analyze specific time periods
- Click on **visual elements** to cross-filter other charts
- Hover over **data points** for detailed tooltips

---

## 💡 **Learning Outcomes**

### **Power BI Skills Developed**
✅ **Data Modeling** - Structured single-table analysis approach  
✅ **DAX Proficiency** - Built 10+ custom measures with complex logic  
✅ **Visual Design** - Created intuitive, management-ready dashboards  
✅ **Page Navigation** - Implemented seamless multi-page user experience  
✅ **KPI Mapping** - Translated business requirements into measurable metrics  

### **Business Intelligence Insights**
✅ **Revenue Optimization** - Identified high-performing vehicle segments  
✅ **Operational Efficiency** - Pinpointed cancellation reduction opportunities  
✅ **Customer Analytics** - Segmented users based on behavior patterns  
✅ **Performance Monitoring** - Established baseline metrics for ongoing tracking  

---

## 🏆 **Project Impact**

This dashboard enables **data-driven decision making** for:
- **Operations Teams** - Optimize vehicle allocation and reduce cancellations
- **Marketing Teams** - Target high-value customer segments effectively  
- **Finance Teams** - Track revenue streams and payment method preferences
- **Management** - Monitor overall business health through comprehensive KPIs

---

## 👨‍💼 **About the Developer**

**Afzal Hussain S** - Data Analytics Professional  
📍 Tamil Nadu, India  
🎓 Data Analytics Intern at Kritilab  
💼 Specialized in Power BI, SQL, Python, and Geospatial Analysis

### **Connect With Me**
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/afzalhussains)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/AfzalHussainS)

---

## 📄 **License**

This project is available under the MIT License. Feel free to use this as a reference for your own Power BI projects.

---

⭐ **If you found this project helpful, please consider giving it a star!**
