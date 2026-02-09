# Kimia Farma Sales Performance Review (2020--2023)

## 📊 Project Overview

This project analyzes **Kimia Farma sales performance** from **2020 to
2023** using a **Big Data Analytics** approach. The analysis focuses on
sales trends, regional performance, and profit growth to support
data-driven business insights, especially during the COVID-19 impacted
period.

## 🎯 Objectives

-   Analyze sales trends from 2020--2023\
-   Identify provinces with the highest sales\
-   Determine provinces with the highest profit growth

## 🗂️ Dataset

The project uses multiple datasets uploaded to **Google BigQuery**: -
`kf_finaltransaction` -- sales transactions\
- `kf_product` -- product information\
- `kf_kantor_cabang` -- branch information\
- `kf_inventory` -- inventory data

All datasets are stored under the `kimia_farma` dataset.

## ⚙️ Data Processing

A consolidated analysis table **`kf_analisis1`** is created using SQL by
joining transaction, product, and branch tables.\
Key calculations include: - Gross profit percentage based on product
price range - Nett sales (price after discount) - Nett profit (nett
sales × gross profit percentage) - Branch rating and transaction rating

## 📈 Dashboard

The processed data is visualized into a **Sales Performance Dashboard**
showing: - Yearly sales trends\
- Sales distribution by province\
- Profit and profit growth comparison

## 🛠️ Tools & Technologies

-   Google BigQuery\
-   SQL\
-   Google Sheets / Excel\
-   Data Visualization Dashboard

## 👤 Author

**Resha Priyatna**\
Undergraduate Student -- Information Science\
Jakarta\
Email: reshapriyatna@gmail.com\
LinkedIn: https://www.linkedin.com/in/resha-priyatna

## 📌 Notes

This project demonstrates the use of SQL and Big Data Analytics to
transform raw transactional data into actionable business insights.
