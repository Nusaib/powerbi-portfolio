@ -0,0 +1,34 @@
# 📊 Week 2 Portfolio – Relationships & Basic DAX

## 📌 This Week's Topics
- DAX Measures (`SUM`, `DISTINCTCOUNT`)
- Derived Metric (`DIVIDE`)
- Interactive visualization & dashboard

## 📂 File
- `PowerBI_Week2_Dataset.xlsx` – practice dataset (Customers, Dates, Products & Sales)
- `PowerBI_Week2_Worksheet.xlsx` – step-by-step instructions for Relationships & Basic DAX
- `dashboard_week2.png` – hresulting visualization dashboard

## 📸 Dashboard Preview
![Dashboard Week 2](dashboard_week2.gif)

## 📝 Penjelasan Dashboard
1. **Slicer (Year, Month, Category)** → for dynamic filtering.   
2. **Total Sales by Product (Bar Chart)** → compare sales values across products.  
3. **Sales per Month (Area Chart)** → trend of monthly sales with running total.
4. **Sales Distribution by Category (Pie Chart)** → contribution of Electronics vs Accessories categories.
5. **Customer's Contribution (Bar Chart)** → comparison of sales contributions across customers.
6. **KPI Cards** → key headline metrics.  
7. **Sales per Customer Table** → total sales and average transaction per customer.

## ✅ Week 2 Progress
- Understand basic ETL (cleaning, removing duplicates, merging queries).  
- Able to create many-to-one relationships.
- Successfully created simple DAX measures.
- Built an interactive dashboard with slicers and basic visuals.
- Add formatting to visual.  

---

## ✅ DAX Measures
```DAX
Total Sales = SUM(Sales[Amount])
Total Qty = SUM(Sales[Quantity])
Total Customers = DISTINCTCOUNT(Sales[CustomerID])
Total Transactions = DISTINCTCOUNT(Sales[SaleID])
Total Product = DISTINCTCOUNT(Sales[ProductID])

Avg Order Value = DIVIDE([Total Sales], [Total Transactions])
Avg Sales per Cust = DIVIDE([Total Sales], [Distinct Customers])
Avg Sales per Unit = DIVIDE([Total Sales], [Total Qty])

Customer Rank = 
RANKX( ALL(Customers[CustomerName]), [Total Sales], , DESC )

% of Total Sales = 
DIVIDE( [Total Sales],
        CALCULATE([Total Sales], ALL(Customers)) )


Running Total Sales =
CALCULATE([Total Sales], FILTER(ALL(Dates), Dates[Date] <= MAX(Dates[Date])))
```

---

📅 **Next Week (Week 3):** Advanced DAX – Time Intelligence (TOTALYTD, SAMEPERIODLASTYEAR, Growth %).