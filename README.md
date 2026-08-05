# 📦 OptiStock Analytics — End-to-End Inventory & Supplier Performance Dashboard

An interactive Power BI Business Intelligence solution for inventory optimization, proactive replenishment decisions, and supplier delay risk analysis.

---

## 🎯 Business Problem

Every business faces this challenge:
- **Stockouts** → Lost sales & unhappy customers
- **Overstocking** → Dead inventory & wasted capital
- **Supplier delays** → Unpredictable supply chain disruptions

Most BI dashboards only show *what happened*. **OptiStock shows what could happen** — enabling data-driven decisions before crises occur.

---

## 📊 Business Impact (What This Dashboard Achieved)

| Metric | Value | Business Insight |
|--------|-------|------------------|
| **Total Sales Revenue Tracked** | $658.37K | Complete visibility into sales performance |
| **Inventory Turnover Ratio** | 72.80 | Healthy stock velocity & working capital efficiency |
| **Dead Stock Identified** | $1.64K | Preventable losses flagged for action |
| **SKUs Requiring Reorder** | 8 out of 25 | Proactive stockout prevention |
| **Estimated Reorder Cost** | $1.54K | Clear capital planning |
| **On-Time Delivery Rate** | 63.70% | Supplier reliability benchmark |
| **Supplier Coverage** | 6 suppliers analyzed | Diversification & risk assessment |

---

## 📸 Dashboard Preview

### 1️⃣ Executive Overview Dashboard
![Executive Overview](executive_overview(1).png)

**Displays core KPIs:** $658.37K sales revenue, 72.80 inventory turnover, $1.64K dead stock, ABC class analysis
- High-level metrics with color-coded indicators
- ABC Class filter for product segmentation
- Monthly revenue trends showing seasonal patterns

---

### 2️⃣ Inventory Health & Aging Analysis
![Inventory Health](inventory_health_aging%20(2).png)

**ABC classification and aging analysis to identify dead stock, fresh inventory, and slow-moving products**
- Dead Stock Value: $1.64K (28% of inventory)
- Fresh Inventory: 60% (0-30 days)
- Slow-Moving: 12% (31-90 days)

---

### 3️⃣ Replenishment & Supplier Performance (with What-If Simulator)
![Reorder Simulator](replenishment_supplier_performance(3).png)

**Interactive What-If slider for supplier delay scenarios, ROP flags, and on-time delivery tracking**
- Dynamic Reorder Point (ROP) flags: 8 of 25 SKUs requiring reorder
- What-If Supplier Delay Simulator (0-10 day range)
- Estimated Reorder Cost: $1.54K
- Supplier on-time delivery rates: Prime Logistics (85%), EuroSupply (38.67%)

---

### 4️⃣ Product-Level Deep Dive
![Product Drill](product_level_deep_dive(4).png)

**Detailed SKU analysis with quarterly performance, revenue trends, and supplier metrics**
- Current Inventory Value: $198.00
- Total Revenue: $26.17K
- Days of Inventory Remaining: 12.68

---

## 🖥️ Dashboard Pages (4 Interactive Views)

### 1️⃣ **Executive Overview**
- High-level KPIs: Sales Revenue ($658.37K), Inventory Value ($9.04K), Turnover Ratio (72.80), Lost Sales ($4.33K)
- ABC Class filter for product segmentation
- Monthly revenue trends (Peak: Feb-Mar $70K, Low: Jun-Jul $45K)
- **Who uses it:** CFO, Supply Chain Director

### 2️⃣ **Inventory Health & Aging Analysis**
- Dead stock value tracking ($1.64K identified)
- Inventory age breakdown: 60% Fresh, 12% Slow-moving, 28% Dead Stock
- Stock level by product with aging buckets
- ABC Classification (Class A: 78%, B: 16%, C: 6%)
- **Who uses it:** Inventory Manager, Finance Analyst

### 3️⃣ **Replenishment & Supplier Performance** ⭐ *Hero Feature*
- Dynamic Reorder Point (ROP) flags - 8 of 25 SKUs flagged
- Products requiring immediate restocking
- **What-If Supplier Delay Simulator** (interactive 0-10 day slider)
- Supplier on-time delivery rates: Prime Logistics (85%), EuroSupply (38.67%)
- Estimated reorder costs ($1.54K)
- **Who uses it:** Procurement Manager, Supply Chain Planner

### 4️⃣ **Product-Level Deep Dive**
- Detailed SKU performance
- Quarterly units sold analysis
- Revenue trends by month & quarter
- Supplier performance by product
- **Who uses it:** Product Manager, Demand Planner

---

## 🛠️ Technical Architecture

### **Data Model: Star Schema**

**Fact Tables:**
- `fact_sales` - Transaction-level sales data
- `fact_purchase_orders` - Supplier orders & delivery dates
- `fact_inventory_snapshot` - Daily inventory levels

**Dimension Tables:**
- `dim_product` - Product master (ABC class, category, cost)
- `dim_supplier` - Supplier master (lead times, reliability)
- `dim_calendar` - Date dimension (for trend analysis)

---

## 💡 Key Features

### 1. **ABC Classification Analysis**
Automatically segments products into 3 categories based on revenue contribution:
- **Class A:** High-value SKUs (78% of revenue)
- **Class B:** Medium-value SKUs (16% of revenue)
- **Class C:** Low-value SKUs (6% of revenue)

### 2. **Inventory Aging & Dead Stock Detection**
Identifies slow-moving and dead inventory:
- **Fresh (0-30 days):** 60% of inventory - recent restocks
- **Slow-moving (31-90 days):** 12% of inventory - consider promotions
- **Dead Stock (90+ days):** 28% of inventory - $1.64K locked up

### 3. **Dynamic Reorder Point (ROP) Logic**
Custom DAX formula that calculates optimal reorder threshold:
- **Formula:** (Average Daily Demand × Lead Time) + Safety Stock
- **Result:** Identified 8 of 25 SKUs requiring immediate reorder
- **Capital Planning:** Calculated $1.54K in reorder cost

### 4. **What-If Supplier Delay Simulator** ⚡
Users can simulate supplier delays (0-10 days) and instantly see:
- Simulated Days of Inventory Remaining
- Stockout risk indicators (Red/Yellow/Green alerts)
- Visual conditional formatting for risk assessment

### 5. **360° Product Drill-Through**
Seamless navigation from executive KPI → detailed SKU diagnostics:
- Revenue trends by month & quarter
- Supplier performance for specific products
- Inventory availability & reorder status

---


