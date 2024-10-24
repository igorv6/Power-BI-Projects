# INTRODUCTION

I collected a dataset with a collection of products sold between 2020-2021 from different retailers, the dataset contains below columns:
- Retailer
- Retailer ID
- Invoice date
- Region
- State
- City
- Product
- Price per unit
- Units Sold
- Total Sales
- Operating Profit
- Operating Margin
- Sales Method

I'm going to perform my analysis only about 2021 years, with the goals to show Retails and Products performance.

### PREPARING PHASE

#### Clean, transforming and organize data in Power Query
First thing to do: Import the dataset into Power BI, I want to use Power Query to trasform, organize and clean the dataset.
Once imported, I check the quality of data using the Visualize function in Power Query. No error or empty rows.

![image](https://github.com/user-attachments/assets/56145344-d9f4-40cd-b9c1-88d302219984)

As we can see from the picture, I change the data type for this values, converting them into Fixed Decimal Number.
Second thing, I'm going to create new table dimensions from the Fact table imported, duplicating it and deleting the column not related to our new tables. Creating new table dimensions let us have better performance for our analysis.
I created 4 new table, adding a new column for ID and removing duplicates. Now I have 5 tables: Sport Product ( Fact Table), Product, Retailer, Geography and Sales Method.
Now it's time to to merge the ID of each dimension table with the Fact table in order to be able to create the right relationship during the data modelling phase.
Now that our Fact Table contains the columns ID from the dimension table, I can start creating the Start schema.

#### Data Modelling
Power Bi has already settled the relation between Fact Table and the table dimensions that I have created:

![image](https://github.com/user-attachments/assets/4a53f1a4-dab7-4eed-a222-19fac4766ebd)

Relations are settled so I create the Date Table in order to be able to use Time Intelligence Function available in Power Bi.
Here the Dax measures used to create my dashboard:

```
Total Orders = COUNT(Sport_products[Invoice Date])

Total Sales = SUM(Sport_products[Total Sales])

Total Transaction = COUNTROWS(Sport_products)

Total Profit = sum(Sport_products[Operating Proft])

Best City Per Sales = TOPN(1,ALL(dim_region[City]),[Total Sales], DESC)

Top product for Sales = TOPN(1,ALL(dim_product[Product]), [Total Sales],DESC)
```
### Analyzing
Here my finding about my questions:

Retailers Performance
- Retailer with the highest number of sales is FootLocker with $18M, followed by Sport Direct with $17M. Walmart presents the lowest sales $4M.
- FootLocker has fulfilled more orders 2.296, followed by Sport Direct 1926
- The State where Retailers made more sales is California ($ 5.146.474) while the Region with more sales is the Midwest ($5.756.738)
- The Sales channel preferred by customer is In-store with $9,6M of sales followed by Online channel with $9,4M. Outlet shows sales for $7,8M
- Trend of sales shows the highest during July and the end of the year on December while the minimum peak is on March

Product Performance:
- Best Products for sales are Men's Street Footwear with $17M of sales followed by Women's apparel $12M. The latest product by sales is Women's Athletic Footwear
- Best city for sales is Charleston
- Men's Athletic Footwear is the product with more orders although order quantities differ little among retailers
- Men's products are more profitable ($14.48M)  than women's product ($12.39M)

- The retailer with the highest number of sales is FootLocker, achieving $18 million, followed by Sport Direct with $17 million. Walmart reported the lowest sales at $4 million. 
- FootLocker has fulfilled more orders, totaling 2,296, while Sport Direct follows with 1,926.
- The state where retailers made the most sales is California, with $5,146,474, while the region with the highest sales is the Midwest, totaling $5,756,738.
- The preferred sales channel for customers is in-store, accounting for $9.6 million in sales, followed closely by the online channel with $9.4 million. Outlet sales amounted to $7.8 million.
- Sales trends indicate the highest activity occurs in July and December, with a minimum peak in March.

Product Performance:
- The best-selling products are Men's Street Footwear, which generates $17 million in sales, followed by Women's Apparel with $12 million.
- The lowest sales are recorded for Women's Athletic Footwear. The best city for sales is Charleston.
- Men's Athletic Footwear has the highest number of orders, although order quantities are relatively similar among retailers.
- Men's products are more profitable, generating $14.48 million compared to $12.39 million for women's products.

### Dashboard Retailers Perfomance
![image](https://github.com/user-attachments/assets/a52db7f2-5f6b-4ce5-b9f5-a388e965660c)

### Dashboard Product analysis
![image](https://github.com/user-attachments/assets/3f19868d-28b6-4856-a1ad-3366a99fde30)


















