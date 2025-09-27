# Hotel-Booking-Dashboard-Using-Power-BI
This project presents an interactive Hotel Booking Analytics Dashboard built in Power BI.
The dashboard helps hotel management gain insights into bookings, cancellations, customer preferences, and revenue trends.

The dataset includes booking details such as stay duration, room type, customer demographics, payment methods, and revenue.

**🎯 Objectives**


Track total bookings, revenue, occupancy rate, and cancellation rate

Analyze room type performance and revenue contribution

Understand customer behavior (new vs returning, stay duration)

Identify preferred payment methods and meal plans

Explore regional insights (city & country performance)


**📊 Dashboard Features**
**🔹 Page 1: Hotel Performance Overview**


KPIs: Total Bookings, Total Revenue, Avg Stay Duration, Cancellation Rate

Monthly Booking Trend

Room Type vs Revenue

Booking Status (Confirmed, Cancelled, No-show)


**🔹 Page 2: Customer & Market Insights**


New vs Returning Customers

Most Preferred Payment Method & Meal Plan (DAX measures)

Revenue by City & Country

Revenue by Payment Method

Avg Stay Duration by Month

Meal Plan Bookings

🛠️ Tools & Technologies

Power BI (Data Modeling, DAX, Visualization)

Excel (Dataset Preparation)

DAX Measures for KPIs (Cancellation Rate, Most Preferred Payment, etc.)


**🧮 Key DAX Measures**
Total Bookings = COUNTROWS(Bookings)


Total Revenue = SUM(Bookings[Total Revenue])

Cancelled Bookings = CALCULATE(COUNTROWS(Bookings), Bookings[Booking Status] = "Cancelled")

Cancellation Rate % = DIVIDE([Cancelled Bookings], [Total Bookings], 0)

Most Preferred Payment =
VAR PaymentSummary =
    SUMMARIZE(Bookings, Bookings[Payment Method], "TotalRevenue", SUM(Bookings[Total Revenue]))
VAR TopPayment = TOPN(1, PaymentSummary, [TotalRevenue], DESC)
RETURN MAXX(TopPayment, Bookings[Payment Method])

