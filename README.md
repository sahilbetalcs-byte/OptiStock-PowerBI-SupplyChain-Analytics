# 📦 OptiStock Analytics — End-to-End Inventory & Supplier Performance Dashboard

**An interactive Power BI Business Intelligence solution for inventory optimization, proactive replenishment decisions, and supplier delay risk analysis.**

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

## 📊 Dashboard Preview

### 1️⃣ Executive Overview
![Executive Overview](images/executive_overview.png)

### 2️⃣ Inventory Health & Aging Analysis
![Inventory Health & Aging Analysis](images/inventory_health_aging.png)

### 3️⃣ Replenishment & Supplier Performance ⭐
![Replenishment & Supplier Performance](images/replenishment_supplier_performance.png)

### 4️⃣ Product-Level Deep Dive
![Product-Level Deep Dive](images/product_level_deep_dive.png)

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

### 3️⃣ **Replenishment & Supplier Performance** ⭐ 
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
---

## 🚀 How to Use This Dashboard

### **For Power BI Analysts:**
1. Download `Optistock_Analytics.pbix`
2. Open in Power BI Desktop
3. Explore 4 dashboard pages
4. Use slicers to filter by date, ABC class, supplier
5. Test the What-If Supplier Delay slider to run scenarios

### **For Supply Chain Teams:**
1. **Mon-Wed:** Check Executive Overview for weekly KPIs
2. **Thu:** Review Inventory Health for dead stock & aging products
3. **Fri:** Use Replenishment page to finalize weekly purchase orders
4. **As needed:** Use Supplier Delay Simulator for contingency planning

---

## 📚 Tech Stack & Skills Demonstrated

| Tool | Usage |
|------|-------|
| **Power BI Desktop** | Data modeling, DAX, drill-through, What-If parameters |
| **DAX** | ROP logic, aging buckets, ABC classification |
| **SQL** | Data extraction & transformation |
| **Power Query** | ETL & data cleaning |
| **Excel** | Data preparation & validation |

**Supply Chain Concepts:**
- Reorder Point (ROP) Logic
- ABC Analysis (Pareto principle)
- Inventory Aging & Dead Stock Management
- Supplier Performance Metrics
- What-If Scenario Analysis

---

## 🎓 Key Insights from Analysis

✅ **60% of inventory is fresh stock** (0-30 days) — good velocity
⚠️ **12% is slow-moving** (31-90 days) — consider promotions
🚨 **28% is dead stock** (90+ days) — $1.64K locked up

✅ **Prime Logistics is most reliable** (85% on-time delivery)
⚠️ **EuroSupply has lower reliability** (38.67%) — build safety stock

✅ **Peak sales months:** February & March (~$70K revenue)
⚠️ **Lowest sales:** June-July (~$45K) — seasonal pattern

---

## 🤔 Questions This Dashboard Answers

- ❓ What products should we reorder immediately?
- ❓ How much dead capital is locked in inventory?
- ❓ Which suppliers are reliable?
- ❓ What happens if a supplier delays?
- ❓ Which products generate the most revenue?
- ❓ Are we at risk of stockouts?

---

## 📊 Data Files Description

**dim_product.csv** - Product master data (25 products)
**dim_supplier.csv** - Supplier information (6 suppliers)
**fact_sales.csv** - Sales transactions (500+ records)
**fact_purchase_orders.csv** - Purchase orders (100+ records)
**fact_inventory_snapshot.csv** - Daily inventory (365 days)

---

## 👤 Author
**Sahil Betals** | Data Analyst | Power BI Developer  
📧 GitHub: [@sahilbetals-byte](https://github.com/sahilbetals-byte)  

---

**Last Updated:** August 2026  
**Version:** 1.0
