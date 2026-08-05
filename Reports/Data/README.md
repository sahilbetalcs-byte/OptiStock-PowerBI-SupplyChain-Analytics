# 📁 Data Files

Source datasets for OptiStock analytics project.

## CSV Files

- **dim_product.csv** (25 products)
  - Product master data with ABC class and categories
  
- **dim_supplier.csv** (6 suppliers)
  - Supplier information with reliability metrics
  
- **fact_sales.csv** (500+ transactions)
  - Sales transactions with revenue and units sold
  
- **fact_purchase_orders.csv** (100+ records)
  - Purchase orders with actual vs promised delivery dates
  
- **fact_inventory_snapshot.csv** (365 days)
  - Daily inventory snapshots with stock levels

## Data Model

Files follow Star Schema design:
- Fact tables: sales, purchase orders, inventory snapshots
- Dimension tables: product, supplier, calendar
