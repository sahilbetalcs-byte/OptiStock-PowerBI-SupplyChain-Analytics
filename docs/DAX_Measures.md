# 📊 DAX Measures & Calculated Columns

## Overview
This document outlines all DAX formulas used in the OptiStock Power BI model for inventory analytics, reorder point calculations, and supplier performance tracking.

---

## 📈 Key DAX Measures

### 1. **Total Revenue**
```dax
Total Revenue = SUM('public fact_sales'[revenue])
```
**Purpose:** Calculates total sales revenue across all products and time periods.

---

### 2. **Total Units Sold**
```dax
Total Units Sold = SUM('public fact_sales'[units_sold])
```
**Purpose:** Sums all units sold for demand planning and turnover calculations.

---

### 3. **Current Inventory Value**
```dax
Current Inventory Value = 
VAR LatestSnapshotDate = MAX('public fact_inventory_snapshot'[snapshot_date])
RETURN
SUMX(
    FILTER(
        'public fact_inventory_snapshot',
        'public fact_inventory_snapshot'[snapshot_date] = LatestSnapshotDate
    ),
    'public fact_inventory_snapshot'[stock_on_hand] * RELATED('public dim_product'[unit_cost])
)
```
**Purpose:** Gets the latest inventory value by multiplying current stock × unit cost.
**Used in:** Executive KPI, Working Capital Analysis

---

### 4. **Dead Stock Value** ⚠️
```dax
Dead Stock Value = 
VAR LatestSnapshotDate = MAX('public fact_inventory_snapshot'[snapshot_date])
RETURN
CALCULATE(
    SUMX(
        FILTER(
            'public fact_inventory_snapshot',
            'public fact_inventory_snapshot'[snapshot_date] = LatestSnapshotDate
        ),
        'public fact_inventory_snapshot'[stock_on_hand] * RELATED('public dim_product'[unit_cost])
    ),
    'public dim_product'[Inventory Age Bucket] = "🔴 Dead Stock (90+ days)"
)
```
**Purpose:** Identifies inventory older than 90 days (locked capital).
**Business Insight:** Flags $1.64K for clearance action.

---

### 5. **Inventory Turnover Ratio** 📊
```dax
Inventory Turnover Ratio = DIVIDE([Total Revenue],[Current Inventory Value],0)
```
**Purpose:** Measures how efficiently inventory is converted to sales.
**Formula:** Revenue ÷ Average Inventory Value
**Result:** 72.80 = excellent velocity

---

### 6. **Reorder Point (ROP)** 🚨
```dax
Reorder Point = 
VAR DaysInRange = COUNTROWS('dim_calendar')
VAR AvgDailyUnitsSold = DIVIDE([Total Units Sold], DaysInRange, 0)
VAR LeadTimeDays = 7
VAR SafetyStockUnits = 10
RETURN
    (AvgDailyUnitsSold * LeadTimeDays) + SafetyStockUnits
```
**Purpose:** Calculates optimal reorder threshold to prevent stockouts.
**Formula:** (Average Daily Demand × Lead Time) + Safety Stock
**Result:** 8 of 25 SKUs flagged for reorder

---

### 7. **Reorder Status**
```dax
Reorder Status = 
IF(
    [Current Stock Units] <= [Reorder Point],
    "🚨 Reorder Now",
    "✅ Stock OK"
)
```
**Purpose:** Flags products requiring immediate reorder action.

---

### 8. **Days of Inventory Remaining**
```dax
Days of Inventory Remaining = 
VAR DaysInRange = COUNTROWS('dim_calendar')
VAR AvgDailyUnitsDemand = DIVIDE([Total Units Sold], DaysInRange, 0)
RETURN
    DIVIDE([Current Stock Units], AvgDailyUnitsDemand, 0)
```
**Purpose:** Estimates how many days current inventory will last.
**Used in:** What-If Supplier Delay Simulator

---

### 9. **On-Time Delivery Rate** ✅
```dax
On-Time Delivery Rate = 
DIVIDE(
    CALCULATE(
        COUNTROWS('public fact_purchase_orders'),
        'public fact_purchase_orders'[actual_delivery_date] <= 'public fact_purchase_orders'[promised_delivery_date]
    ),
    COUNTROWS('public fact_purchase_orders'),
    0)
```
**Purpose:** Measures supplier reliability.
**Result:** 63.70% across all suppliers, ranging from 17.02% to 85.00%

---

### 10. **Average Delivery Delay**
```dax
Avg Delivery Delay = 
AVERAGEX(
    'public fact_purchase_orders',
    DATEDIFF(
        'public fact_purchase_orders'[promised_delivery_date],
        'public fact_purchase_orders'[actual_delivery_date],
        DAY
    )
)
```
**Purpose:** Calculates average days late for supplier orders.

---

### 11. **Simulated Days Remaining** ⚡
```dax
Simulated Days Remaining = [Days of Inventory Remaining] - [Simulated Supplier Delay Value]
```
**Purpose:** What-If analysis for supplier delay impact.
**Example:** If supplier delays 4 days, how does it affect stockout risk?

---

### 12. **Simulated Supplier Delay Value**
```dax
Simulated Supplier Delay Value = SELECTEDVALUE('Simulated Supplier Delay'[Simulated Supplier Delay], 0)
```
**Purpose:** Interactive What-If parameter (0-10 day slider).

---

### 13. **Estimated Reorder Cost**
```dax
Est Reorder Cost = 
CALCULATE(
    [Current Inventory Value],
    FILTER(
        'public fact_inventory_snapshot',
        'public fact_inventory_snapshot'[stock_on_hand] <= [Reorder Point]
    )
)
```
**Purpose:** Calculates capital needed for restocking flagged SKUs.
**Result:** $1.54K identified for budgeting

---

## 🔧 Calculated Columns

### 1. **ABC Class**
```dax
ABC Class = 
VAR CurrentRank = 
    RANKX(ALL('public dim_product'), [Total Revenue], , DESC)
VAR CumulativeRevenue = 
    SUMX(
        FILTER(
            ALL('public dim_product'),
            RANKX(ALL('public dim_product'), [Total Revenue], , DESC) <= CurrentRank
        ),
        [Total Revenue]
    )
VAR GrandTotalRevenue = 
    CALCULATE([Total Revenue], ALL('public dim_product'))
VAR CumulativePct = 
    DIVIDE(CumulativeRevenue, GrandTotalRevenue, 0)
RETURN
    IF(
        CumulativePct <= 0.8, "Class A",
        IF(CumulativePct <= 0.95, "Class B", "Class C")
    )
```
**Purpose:** Pareto analysis - classifies products by revenue contribution.
- **Class A:** Top 80% of revenue (high priority)
- **Class B:** Next 15% of revenue (medium priority)
- **Class C:** Bottom 5% of revenue (low priority)

---

### 2. **Inventory Age Bucket**
```dax
Inventory Age Bucket = 
VAR DaysSinceRestock = 'public dim_product'[Days Since Last Restock]
RETURN
    IF(
        ISBLANK(DaysSinceRestock), "No Data",
        IF(
            DaysSinceRestock <= 30, "🟢 Fresh (0-30 days)",
            IF(
                DaysSinceRestock <= 90, "🟡 Slow-moving (31-90 days)",
                "🔴 Dead Stock (90+ days)"
            )
        )
    )
```
**Purpose:** Segments inventory by age for health analysis.
- **🟢 Fresh:** Recently restocked, good liquidity
- **🟡 Slow-moving:** Consider promotions
- **🔴 Dead Stock:** Immediate clearance action

---

### 3. **Dashboard Title**
```dax
Dashboard Title = 
"Inventory & Sales Analytics Dashboard - " &
IF(
    HASONEVALUE('public dim_product'[ABC Class]),
    SELECTEDVALUE('public dim_product'[ABC Class]),
    "All Categories"
)
```
**Purpose:** Dynamic title that changes based on ABC Class filter.

---

## 🎓 Key Concepts Used

✅ **RANKX** - Ranking products by revenue for ABC analysis
✅ **SUMX** - Complex calculations with conditions
✅ **VAR** - Variables to improve readability and performance
✅ **FILTER** - Conditional aggregations
✅ **CALCULATE** - Context modification
✅ **DATEDIFF** - Date calculations for delivery delays
✅ **SELECTEDVALUE** - Interactive parameters for What-If analysis

---

## 📊 Performance Tips

- **Implicit measures** avoid: Use explicit DAX measures for consistency
- **Variables (VAR)** improve readability and performance
- **Aggregation tables** could speed up large datasets
- **Incremental refresh** recommended for fact tables >1M rows

---

**Last Updated:** August 2026
