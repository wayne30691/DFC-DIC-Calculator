# 📦 DFC & DIC Calculator  
**Days of Forecast Coverage (DFC)** and **Days of Inventory Coverage (DIC)**

---

## 🧭 Overview
This project estimates how long current inventory will last before reaching zero, based on either **forecasted demand** or **actual depletion**.  
It supports both **forecast-based** and **consumption-based** perspectives for supply-chain and commercial planning.

- **DFC (Days of Forecast Coverage):**  
  Estimates how many days the current inventory can support the *forecasted* daily demand.  
- **DIC (Days of Inventory Coverage):**  
  Estimates how many days the current inventory can last against *actual* daily depletion.

This model can be integrated into **Power BI** for interactive visualization or run as a **Python script** for automated calculations.

---

## ⚙️ Formula

### 🧮 DFC – Days of Forecast Coverage
\[
\text{DFC} = \frac{\text{Current Inventory (9L)}}{\text{Forecasted Daily Sales (9L/day)}}
\]

### 🧮 DIC – Days of Inventory Coverage
\[
\text{DIC} = \frac{\text{Current Inventory (9L)}}{\text{Actual Average Daily Depletion (9L/day)}}
\]

Both values indicate how many days it would take for the inventory to reach zero under given conditions.

---

## 🧰 Features
- Supports both **monthly** and **daily** granularity  
- Works with data from **Snowflake**, **Excel**, or **Salesforce**  
- Compatible with **Power BI DirectQuery** and **Python pandas** workflows  
- Optional alerts for low-coverage SKUs (e.g., < 30 days)

---

## 📊 Example

| SKU | Current Inventory (9L) | Forecasted Daily Sales | DFC (Days) | Actual Daily Depletion | DIC (Days) |
|-----|------------------------|------------------------|-------------|-----------------------|-------------|
| AR2004 | 9,000 | 300 | 30 | 360 | 25 |
| CH1001 | 15,000 | 400 | 38 | 350 | 43 |

Interpretation:
- SKU AR2004: 30 days of stock under forecasted demand, 25 days under actual depletion.
- SKU CH1001: inventory can sustain ~38 days (forecast) or 43 days (actual).

---

## 🧩 Architecture
- **Data Source:** Snowflake / Excel / Salesforce  
- **ETL:** Power Query / Python (pandas)  
- **Calculation Layer:** DAX or Python  
- **Visualization:** Power BI (with filters by brand, SKU, region)

---

## 🚀 Usage
1. Connect data source in Power BI or Python.  
2. Refresh inventory and sales/depletion data.  
3. Run DFC / DIC calculation script.  
4. Review dashboard output:
   - Coverage trend over time  
   - Low-coverage SKU alerts  
   - YOY / MOM coverage comparisons  

---

## 🧮 Example Python Snippet
```python
df['DFC'] = df['Inventory_9L'] / (df['Forecast_9L'] / df['Days'])
df['DIC'] = df['Inventory_9L'] / (df['Actual_Sales_9L'] / df['Days'])
