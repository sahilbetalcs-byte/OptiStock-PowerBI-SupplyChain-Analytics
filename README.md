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
![Executive Overview](https://github.com/sahilbetals-byte/OptiStock-PowerBI-SupplyChain-Analytics/raw/main/executive_overview_1_.png)
*Displays core KPIs: $658.37K sales revenue, 72.80 inventory turnover, $1.64K dead stock, ABC class analysis*

---

### 2️⃣ Inventory Health & Aging Analysis
![Inventory Health](https://github.com/sahilbetals-byte/OptiStock-PowerBI-SupplyChain-Analytics/raw/main/inventory_health_aging__2_.png)
*ABC classification and aging analysis to identify dead stock, fresh inventory, and slow-moving products*

---

### 3️⃣ Replenishment & Supplier Performance (with What-If Simulator)
![Reorder Simulator](https://github.com/sahilbetals-byte/OptiStock-PowerBI-SupplyChain-Analytics/raw/main/replenishment_supplier_performance_3_.png)
*Interactive What-If slider for supplier delay scenarios, ROP flags, and on-time delivery tracking*

---

### 4️⃣ Product-Level Deep Dive
![Product Drill](https://github.com/sahilbetals-byte/OptiStock-PowerBI-SupplyChain-Analytics/raw/main/product_level_deep_dive_4_.png)
*Detailed SKU analysis with quarterly performance, revenue trends, and supplier metrics*

---

## 🖥️ Dashboard Pages (4 Interactive Views)

### 1️⃣ **Executive Overview**
- High-level KPIs: Sales Revenue, Inventory Value, Turnover Ratio, Lost Sales
- ABC Class filter for product segmentation
- Monthly revenue trends
- **Who uses it:** CFO, Supply Chain Director

### 2️⃣ **Inventory Health & Aging Analysis**
- Dead stock value tracking
- Inventory age breakdown (Fresh/Slow-moving/Dead)
- Stock level by product
- ABC Classification
- **Who uses it:** Inventory Manager, Finance Analyst

### 3️⃣ **Replenishment & Supplier Performance** ⭐ *Hero Feature*
- Dynamic Reorder Point (ROP) flags
- Products requiring immediate restocking
- **What-If Supplier Delay Simulator** (interactive slider)
- Supplier on-time delivery rates
- Estimated reorder costs
- **Who uses it:** Procurement Manager, Supply Chain Planner

### 4️⃣ **Product-Level Deep Dive**
- Detailed SKU performance
- Quarterly units sold
- Revenue trends
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
- `dim_product` - Product master (ABC class, category)
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
- **Fresh (0-30 days):** Recent restocks
- **Slow-moving (31-90 days):** Potential clearance candidates
- **Dead Stock (90+ days):** Urgent action items

*Result: Identified $1.64K in dead stock for immediate clearance.*

### 3. **Dynamic Reorder Point (ROP) Logic**
Custom DAX formula that calculates optimal reorder threshold:
- **Automated flag:** SKUs below ROP highlighted in red
- **Action:** Identified 8 of 25 SKUs requiring immediate reorder
- **Capital planning:** Calculated $1.54K in reorder cost

### 4. **What-If Supplier Delay Simulator** ⚡
Users can simulate supplier delays (0-10 days) and instantly see:
- Simulated Days of Inventory Remaining
- Stockout risk indicators
- Visual alerts (Red = critical, Yellow = warning, Green = safe)

### 5. **360° Product Drill-Through**
Seamless navigation from executive KPI → detailed SKU diagnostics:
- Revenue trends by month & quarter
- Supplier performance for specific products
- Inventory availability & reorder status

---

## 📁 Repository Structure
