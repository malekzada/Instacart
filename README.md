# Instacart Grocery Basket Analysis  
![instacart](https://github.com/user-attachments/assets/e6f54daa-5fcd-4812-93fb-b2fc3c421c38)

### About Instacart  
Instacart, an online grocery store that operates through an app. Instacart already has very good sales, but they want to uncover more information about their sales patterns.

### Executive Summary:
This repository focuses on intensive analysis of Instacart company's Sales and customers based on 'The instacart online grocery shopping dataset 2017'. The analysis focuses on providing insights on customer behavior, purchasing patterns, best performing days/hours, popularity of certain products, performance of different departments, spending behavior in different regions. Furthermore, it includes creating multiple different categories of customers like loyalty flags, income classes, and age groups to answer important key questions of stakeholders. At the end, different recommendations are given based on the insights uncovered in this analysis.

#### Key Questions  
● The sales team needs to know what the busiest days of the week and hours of the day are (i.e., the days and times with the most orders) in order to schedule ads at times when there are fewer orders.  
● They also want to know whether there are particular times of the day when people spend the most money, as this might inform the type of products they advertise at these times.  
● Instacart has a lot of products with different price tags. Marketing and sales want to use simpler price range groupings to help direct their efforts.  
● Are there certain types of products that are more popular than others? The marketing and sales teams want to know which departments have the highest frequency of product orders.  
● The marketing and sales teams are particularly interested in the different types of customers in their system and how their ordering behaviors differ. For example:  
  ○ What’s the distribution among users in regards to their brand loyalty (i.e., how often do they return to Instacart)?  
  ○ Are there differences in ordering habits based on a customer’s loyalty status?  
  ○ Are there differences in ordering habits based on a customer’s region?  
  ○ Is there a connection between age and family status in terms of ordering habits?  
  ○ What different classifications does the demographic information suggest? Age? Income? Certain types of goods? Family status?  
  ○ What differences can you find in ordering habits of different customer profiles? Consider the price of orders, the frequency of orders, the products customers are ordering, and anything else you can think of.

#### Dataset  
The dataset used in this analysis is from Open-Source dataset by Instacart which includes data on Customers, Orders, Departments, and Products.  
● Customers _(206,209 Rows)_  
● Orders _(3,421,083 Rows)_  
● Orders Products Prio _(32,434,489)_  
● Products _(49,693)_  

#### Analysis Criteria and Methods Used  
● Data cleaning using **Python** _(Jupyter notebooks_).  
● Data Analysis using Python and relevant libraries (_pandas, NumPy, os, matplotlib, scipy, and seaborn_).  
● All of the data sets merged into **A single data set**.  
● Conducting descriptive analysis after importing of datasets.  
● Deriving new columns relevant to the analysis. (_age group, income class, loyalty flag_).  
● Visualizing important data using python.

## Analysis  
- The line chart shows the behavior of different loyalty segments at different hours of the day.  
- Loyal and average customers seem to be more active during the early hours of the day.  
- It is also evident that the busiest hours of the day remain between 9 AM to 2 PM.  
![loyal_hours](https://github.com/user-attachments/assets/64b1103a-12d4-44b9-8b81-fcb750752c67)

###### Python Code: _Derive loyalty_tag column_
```
df.loc[df['max_orders']> 40, 'loyalty_tag'] = 'loyal_customer'
df.loc[(df['max_orders']<=40) & (df['max_orders']>10), 'loyalty_tag'] = 'average_customer'
df.loc[df['max_orders']<=10, 'loyalty_tag'] = 'new_customer'
```
###### Python Code: _Visualization_
```
custom_color = {'#5dade2','#2ecc71','#f1c40f'}

line_loyalty = sns.lineplot(data=df_loyalty_hours, x='order_hour_of_day', y='order_count', hue='loyalty_tag', palette= custom_color)
plt.gca().yaxis.set_major_formatter(ticker.StrMethodFormatter('{x:,.0f}'))
plt.xlabel("Hour of the Day")
plt.ylabel("Number of Orders")
plt.title("Order behavior of different loyalty segment")
plt.savefig(os.path.join(path, '02 Data', 'Prepared Data', 'loyalty behavior.png'), dpi=300, bbox_inches='tight')
```

- The chart shows the best performing departments based on the number of orders.  
- Produce and dairy eggs are among the top 2 departments dominating the charts.  
![departments](https://github.com/user-attachments/assets/89cdf7b1-caa8-438a-a576-45e5131858b5)
###### Python Code: _Visualization_
```
bar_department_orders = df_department_orders['department'].value_counts().sort_values(ascending=True).plot.barh(color=['#2ecc71'], figsize=(13,6))
plt.ylabel("Departments")
plt.xlabel("Number of Orders")
plt.title("Performance of Each department based on number of orders")
```
- The Top 5 products chart shows the most popular products between customers.
![top products](https://github.com/user-attachments/assets/f0328a4e-7c05-4623-83f5-ce0e5e7cbf87)  
###### Python Code: _Visualization_  
```
custom_color = ['#312581', '#00b215', '#e53939', '#03396c', '#fff547']

plt.figure(figsize=(10,6))
bar_top_5_products = sns.barplot(
    data=df_product_department_1,
    x='count',
    y='product_name',
    palette=custom_color)
plt.gca().xaxis.set_major_formatter(ticker.StrMethodFormatter('{x:,.0f}'))
plt.ylabel("Products")
plt.xlabel("Number of Orders")
plt.title("Top 5 Products")
plt.savefig(os.path.join(path, '02 Data', 'Prepared Data', 'top products.png'), dpi=300, bbox_inches='tight')
plt.show()
```
- The scatterplot shows that there is a slightly positive relation between the age and spending power.  
- There spending power of a proportion of the customers increase after the age of 40.
![age and spending](https://github.com/user-attachments/assets/e807ed64-091a-4f67-81ef-319c2a45bd95)
###### Python Code: _Visualization_  
```
scatter_spending_power = sns.scatterplot(data = df_spending_power,x = 'age', y = 'income', color= '#2ecc71')
plt.gca().yaxis.set_major_formatter(ticker.StrMethodFormatter('{x:,.0f}'))
plt.xlabel("Age")
plt.ylabel("Income")
plt.title("Spending Power: Age vs. Income")
plt.savefig(os.path.join(path, '02 Data', 'Prepared Data', 'age and spending.png'), dpi=300, bbox_inches='tight')
```
- The spending behavior across different demographics vary greatly. Elder customers over 60 take up a decent portion of the spending.  
- Couples spend way more than Single Adults.
![customer profile spending](https://github.com/user-attachments/assets/948a15d3-0a1a-4e40-b300-72ebe6a384ed)
###### Python Code: _Visualization_  
```
bar_customer_spending_behavior = df_customer_spending_behavior.plot(kind='barh', figsize=(12, 6), color=['#e74c3c', '#f1c40f', '#82e0aa',
    '#2ecc71', '#239b56', '#186a3b'])
plt.gca().xaxis.set_major_formatter(ticker.StrMethodFormatter('{x:,.0f}'))
plt.xlabel("Spending")
plt.ylabel("Customer Profile")
plt.title("Spending by Customer Profile")
plt.savefig(os.path.join(path, '02 Data', 'Prepared Data', 'customer profile spending.png'), dpi=300, bbox_inches='tight')
```

## Recommendations
● Focusing ads between 9 AM to 2 PM for optimal results.  
● Produce, Dairy Eggs and snacks are among the top product departments with the majority of the sales. Have sufficient stock of products in those departments.  
● A decent percentage of customer are new customers so more attention should be given to building customer loyalty.  

## Next Steps
● Work with the marketing department to tailor marketing campaigns toward different segments of customers.  
● Collect data on what products are ordered together.  
● Get feedback from stakeholders.  

#### Project Folders
01. 01 Project Management  
     - A4_Data_Immersion_Project_Brief: Project brief including objectives, key questions, analysis criteria, tasks and deliverables.  
02. 03 Scripts  
     - Instacart Project Analysis: includes python scripts used to uncover instacart insights.  
03. 05 Sent To Client  
     - A4_final_report_template: Brief Excel file including steps taken to derive the insights and changes made to cleanup the data sets.  
04. Visualizations: includes visualizations of the insights derived from the data set.

### CODE
- Libraries Used: Pandas, Numpy, OS, Seaborn, Scipy, matplotlib.pyplot

## Sources and Links:
[Customer Data Set](https://s3.amazonaws.com/coach-courses-us/public/courses/data-immersion/A4/A4_Data_Assets/customers.zip)  
[Orders and Products Data set](https://s3.amazonaws.com/coach-courses-us/public/courses/data-immersion/A4/A4_Data_Assets/4.3_orders_products.zip)  
[Department Data Set](https://s3.amazonaws.com/coach-courses-us/public/courses/data-immersion/A4/A4_Data_Assets/4.4_departments.zip)  
[Orders Products Prior](https://s3.amazonaws.com/coach-courses-us/public/courses/data-immersion/A4/A4_Data_Assets/4.6_orders_products_prior.zip)  
[Instacart Data Dictionary](https://gist.github.com/jeremystan/c3b39d947d9b88b3ccff3147dbcf6c6b)

Source: “The Instacart Online Grocery Shopping Dataset 2017”, Accessed from www.instacart.com/datasets/grocery-shopping-2017 via Kaggle on 10/05/2025.

