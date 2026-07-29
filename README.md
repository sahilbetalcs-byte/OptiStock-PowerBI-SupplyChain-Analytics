# 📦 OptiStock Analytics — End-to-End Inventory, Replenishment & Supplier Performance Dashboard

An interactive, end-to-end Power BI Business Intelligence solution designed to optimize inventory management, improve working capital utilization, automate replenishment using dynamic Reorder Points (ROP), and simulate supplier delay risks.

---

## 💡 Business Problem
Businesses face a constant operational challenge:
- **Stockouts** result in lost sales and degraded customer experience, while also reducing potential revenue.
- **Overstocking** increases holding costs and locks up critical working capital in dead inventory.

Standard BI dashboards often rely solely on historical reporting. **OptiStock Analytics** addresses this gap by offering proactive decision-support tools that allow supply chain teams to identify operational risks and test scenarios *before* stockouts occur.

---

## 🖥️ Dashboard Pages

1. **Executive Overview** — High-level sales, inventory, turnover, and lost-sales KPIs.
2. **Inventory Health & Aging** — ABC classification, inventory aging, dead-stock analysis, and inventory health insights.
3. **Replenishment & Supplier Analysis** — Dynamic ROP analysis, estimated reorder cost, supplier performance, and the What-If Delay Simulator.
4. **Product-Level Drill-Through** — Detailed SKU-level revenue, demand, inventory, and supplier insights.

---

## 🛠️ Key Features & Insights

### 1. Executive Overview & Inventory Health Analysis
- Tracks core KPIs: **Total Sales Revenue**, **Current Inventory Value**, **Inventory Turnover Ratio**, **Total Lost Sales**, and **Dead Stock Value**.
- Utilizes **ABC Analysis** and **Inventory Aging** to prioritize high-value SKUs and flag stagnant stock.

### 2. Dynamic Reorder Point (ROP) & Supplier Analysis
- Implemented custom DAX logic to flag products dropping below calculated replenishment thresholds.
- Identified **8 out of 25 SKUs** requiring immediate restocking.
- Calculates estimated reorder costs to provide clear visibility on required replenishment capital.
- **Supplier Performance Tracking:** Analyzes supplier reliability and delivery performance to identify potential supply-side risks.

### 3. ⚡ What-If Supplier Delay Simulator (Hero Feature)
- Features an interactive **What-If Parameter** allowing users to simulate delivery delays in real time.
- Dynamically updates:
  - **Simulated Days of Inventory Remaining**
  - **Potential Stockout Risk Indicators**
  - **Visual Conditional Formatting** (Red/Yellow/Green alerts)

### 4. 360° Product Drill-Through
- Enables seamless drill-through from high-level executive KPIs to detailed SKU-level diagnostics (Quarterly Revenue, Units Sold, Supplier Reliability).

---

## ⚙️ Tech Stack & Concepts
- **Tools:** Power BI Desktop, DAX, Power Query, SQL, Microsoft Excel
- **Concepts:** Supply Chain Analytics, Reorder Point (ROP) Logic, What-If Analysis, Data Modeling, ABC Classification, Inventory Aging, Conditional Formatting

---

## 📊 Project Artifacts
- **Interactive Report (.pbix):** Included in this repository for full model exploration.
- **Executive PDF Summary:** Available in the root folder as `OptiStock_Executive_Report.pdf`.
