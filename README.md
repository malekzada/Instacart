
# 📊 Instacart Grocery Basket Analysis  
![instacart](https://github.com/user-attachments/assets/e6f54daa-5fcd-4812-93fb-b2fc3c421c38)

---

## 🧾 Executive Summary

Comprehensive analysis of Instacart’s 2017 online grocery shopping dataset: The goal is to uncover actionable insights into customer behavior, product trends, and operational patterns that can support strategic decisions in marketing and operations. Key questions address peak shopping times, customer segmentation, spending behavior, and product popularity.

### 🔍 Key Findings:
- **Peak Ordering Times:** The busiest period for orders is between **9 AM and 2 PM**, with loyal and average customers being most active during early hours.
- **Top Performing Departments:** The **Produce** and **Dairy & Eggs** departments lead in total order volume.
- **Customer Segments:** Customers were segmented into **new**, **average**, and **loyal** groups based on order frequency. Loyalty levels significantly influence shopping patterns.
- **Demographic Insights:** Older customers (age 60+) and families/couples exhibit higher spending power. There's a slight positive correlation between **age and income**.
- **Product Popularity:** The top 5 products reveal concentrated customer preferences, useful for targeted promotions.

Based on these findings, several strategic recommendations and next steps are provided to improve customer targeting, advertising effectiveness, and product availability.

---

## ❓ Business Questions

- What are the busiest days and hours for customer orders?
- When do customers tend to spend the most money?
- Which product departments have the highest order frequency?
- What are the spending habits across different customer demographics?
- How do customer loyalty levels and regional or demographic characteristics affect purchasing patterns?

---

## 🗂️ Dataset Overview

The dataset is an open-source release from Instacart containing detailed transactional and demographic data:

| Dataset                    | Records     |
|---------------------------|-------------|
| Customers                 | 206,209     |
| Orders                    | 3,421,083   |
| Order-Products Prior      | 32,434,489  |
| Products                  | 49,693      |

---

## 🧪 Methodology

- **Tools:** Python (Jupyter Notebooks), Pandas, NumPy, Matplotlib, Seaborn, SciPy, OS.
- **Process:**
  - Data cleaning and consolidation into a single dataset.
  - Feature engineering: deriving new columns like `loyalty_tag`, `income_class`, and `age_group`.
  - Descriptive statistics and visualization for behavior profiling.
  - Categorization of customer types and spending analysis.

---

## 📈 Key Analyses & Visualizations

### 1. Loyalty Segments by Hour of Day
- Loyal and average customers are more active during early hours (especially 9 AM–2 PM).  
![loyal_hours](https://github.com/user-attachments/assets/64b1103a-12d4-44b9-8b81-fcb750752c67)

### 2. Top Performing Departments
- **Produce** and **Dairy & Eggs** are the most ordered categories.  
![departments](https://github.com/user-attachments/assets/89cdf7b1-caa8-438a-a576-45e5131858b5)

### 3. Most Popular Products
- The five most frequently purchased products were identified to help focus promotional strategies.  
![top products](https://github.com/user-attachments/assets/f0328a4e-7c05-4623-83f5-ce0e5e7cbf87)

### 4. Spending Power by Age
- There's a mild positive correlation between age and income; noticeable increase after age 40.  
![age and spending](https://github.com/user-attachments/assets/e807ed64-091a-4f67-81ef-319c2a45bd95)

### 5. Customer Profile Spending
- Elderly customers and couples contribute more significantly to total spending than singles.  
![customer profile spending](https://github.com/user-attachments/assets/948a15d3-0a1a-4e40-b300-72ebe6a384ed)

---

## ✅ Recommendations

- Schedule marketing ads during **off-peak hours** (outside 9 AM–2 PM) to reduce competition with organic orders.
- Prioritize inventory and marketing in **Produce**, **Dairy & Eggs**, and **Snacks** departments.
- Increase **loyalty-building initiatives** for new customers through targeted retention programs.
- Customize product suggestions and promotions based on **customer age**, **income**, and **household status**.

---

## 🔄 Next Steps

- Collaborate with marketing to tailor campaigns for each loyalty and demographic segment.
- Explore **product bundling trends** to optimize cross-sell opportunities.
- Conduct **stakeholder feedback sessions** for data-driven strategy refinement.

---

## 📁 Project Structure

```
├── 01 Project Management
│   └── A4_Data_Immersion_Project_Brief
├── 03 Scripts
│   └── Instacart Project Analysis (Python Scripts)
├── 05 Sent To Client
│   └── A4_final_report_template (Excel summary)
├── Visualizations
│   └── Graphs and charts used in the analysis
```

---

## 🧩 Libraries Used

- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **SciPy**
- **OS**

---

## 📚 Data Sources

- [Customers Dataset](https://s3.amazonaws.com/coach-courses-us/public/courses/data-immersion/A4/A4_Data_Assets/customers.zip)  
- [Orders & Products](https://s3.amazonaws.com/coach-courses-us/public/courses/data-immersion/A4/A4_Data_Assets/4.3_orders_products.zip)  
- [Departments](https://s3.amazonaws.com/coach-courses-us/public/courses/data-immersion/A4/A4_Data_Assets/4.4_departments.zip)  
- [Order Products Prior](https://s3.amazonaws.com/coach-courses-us/public/courses/data-immersion/A4/A4_Data_Assets/4.6_orders_products_prior.zip)  
- [Instacart Data Dictionary](https://gist.github.com/jeremystan/c3b39d947d9b88b3ccff3147dbcf6c6b)

> Source: “The Instacart Online Grocery Shopping Dataset 2017” – www.instacart.com/datasets/grocery-shopping-2017 (Accessed via Kaggle, 10/05/2025)
