# Kimia Farma Sales Performance Review (2020–2023)

## 📊 Project Overview
This project analyzes **Kimia Farma sales performance** from **2020 to 2023** using a **Big Data Analytics** approach. The analysis focuses on sales trends, regional performance, and profit growth to support data-driven business insights, especially during the COVID-19 impacted period.

---

## 🎯 Objectives
- Analyze sales trends from 2020–2023  
- Identify provinces with the highest sales  
- Determine provinces with the highest profit growth  

---

## 🗂️ Dataset
The project uses multiple datasets uploaded to **Google BigQuery**:
- `kf_finaltransaction` – sales transactions  
- `kf_product` – product information  
- `kf_kantor_cabang` – branch information  
- `kf_inventory` – inventory data  

All datasets are stored under the `kimia_farma` dataset.

---

## ⚙️ Data Processing
A consolidated analysis table **`kf_analisis1`** is created using SQL by joining transaction, product, and branch tables.  
This table contains calculated business metrics such as gross profit percentage, nett sales, and nett profit.

### SQL Query – Create Analysis Table
```sql
CREATE TABLE `kimia_farma.kf_analisis1` AS
SELECT
  ft.transaction_id,
  ft.date,
  kc.branch_id,
  kc.branch_name,
  kc.kota,
  kc.provinsi,
  kc.rating AS rating_cabang,
  ft.customer_name,
  ft.product_id,
  p.product_name,
  ft.price AS actual_price,
  ft.discount_percentage,

  CASE
    WHEN ft.price <= 50000 THEN 0.10
    WHEN ft.price > 50000 AND ft.price <= 100000 THEN 0.15
    WHEN ft.price > 100000 AND ft.price <= 300000 THEN 0.20
    WHEN ft.price > 300000 AND ft.price <= 500000 THEN 0.25
    WHEN ft.price > 500000 THEN 0.30
  END AS persentase_gross_laba,

  ft.price * (1 - ft.discount_percentage / 100) AS nett_sales,

  (ft.price * (1 - ft.discount_percentage / 100)) *
  CASE
    WHEN ft.price <= 50000 THEN 0.10
    WHEN ft.price > 50000 AND ft.price <= 100000 THEN 0.15
    WHEN ft.price > 100000 AND ft.price <= 300000 THEN 0.20
    WHEN ft.price > 300000 AND ft.price <= 500000 THEN 0.25
    WHEN ft.price > 500000 THEN 0.30
  END AS nett_profit,

  ft.rating AS rating_transaksi

FROM `kimia_farma.kf_finaltransaction` ft
JOIN `kimia_farma.kf_product` p
  ON ft.product_id = p.product_id
JOIN `kimia_farma.kf_kantor_cabang` kc
  ON ft.branch_id = kc.branch_id;
```

---

## 📈 Dashboard
The processed data is visualized into a **Sales Performance Dashboard** showing:
- Yearly sales trends  
- Sales distribution by province  
- Profit and profit growth comparison  

---

## 🛠️ Tools & Technologies
- Google BigQuery  
- SQL  
- Google Sheets / Excel  
- Data Visualization Dashboard  

---

## 👤 Author
**Resha Priyatna**  
Undergraduate Student – Information Science  
📍 Jakarta  
📧 reshapriyatna@gmail.com  
🔗 LinkedIn: https://www.linkedin.com/in/resha-priyatna  

---

## 📌 Notes
This project demonstrates how SQL and Big Data Analytics can be used to transform raw transactional data into actionable business insights.
