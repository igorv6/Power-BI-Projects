# INTRODUCTION

We have a dataset with a collection of products sold between 2020-2021 from different retailers, the dataset contains below columns:
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

I'm going to perform my analysis with the goals to show Retails and Products performance.

For the Retails company, I want to find below insights:
- Trends of sales
- Profit and operating margin
- Geographic analysis
- Performance comparison between 2020 and 2021

For Product performance, I want to find below insights:
- Trend of Sales per Categories
- Categories most sold
- Categories most profitable
- Trend of sales by season

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

### Data Modelling












