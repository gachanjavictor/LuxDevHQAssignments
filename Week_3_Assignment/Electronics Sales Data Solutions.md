# Power BI Project: Electronics Sales Data
# Questions And Solutions

## Instructions

## Step 1: Data Cleaning
Data cleaning is often the most time-consuming part of any analytics project. It's essential to ensure that your data is both accurate and consistent.

### 1. Ensure Consistency in Data Types
Some columns might have inconsistent data types. For example, the `OrderDate` column should be a **date** and `SalesAmount` should be a **numeric** type. Check for any text values that don’t match the expected format.
### Solution
The dataset was checked to ensure all columns were in the correct data type.

<img width="960" height="540" alt="Date datatype" src="https://github.com/user-attachments/assets/57f084b2-e3f8-432e-a93a-614a185cf49b" />
<img width="960" height="540" alt="Text datatype" src="https://github.com/user-attachments/assets/4655d02f-7477-443c-8038-75f055451178" />
<img width="960" height="540" alt="Numeric datatype" src="https://github.com/user-attachments/assets/d103168e-b963-4885-b8a9-626d52b565ee" />


### 2. Check for Spelling Errors
You'll likely find some inconsistencies in **product names**, **country names**, or even **customer emails**. For example, "Samsung Galaxy S21" might have variations like "Samsung Galaxy S21" and "Samsung GAlaxy S21" in the dataset. Tip: Filter for product names to help standardize them.

### Solution
The dataset was checked for incorrect spellings in the columns with text.

<img width="517" height="692" alt="Products" src="https://github.com/user-attachments/assets/d4e97613-cd4f-4e38-a8e7-c0f2a933fead" />
<img width="518" height="664" alt="Cities" src="https://github.com/user-attachments/assets/4869575d-583b-4f25-bffd-b3295a90e104" />

### 3. Missing or Incomplete Data
Look for empty cells or missing values in columns such as `Profit`, `SalesAmount`, and `ShippingCost`. It's important to decide whether to remove, impute, or fill these gaps.

### Solution
The dataset was checked for missing data. There were no empty cells.
<img width="752" height="67" alt="image" src="https://github.com/user-attachments/assets/c8259802-5f08-42c2-aba8-7fef681a4f25" />

### 4. Pseudonyms and Invalid Entries
Sometimes, customers or sales representatives might be recorded as "Anonymous" or "N/A." These entries need to be cleaned or handled to avoid inconsistencies in analysis.
For example:
- A row with `CustomerName = "N/A"` in a paid sales transaction should be flagged for review and ensure all pseudoblanks are consistent if any.

### Solution
This was answered along with question 2.

### 5. Ensure Correct Data Formats
Ensure that columns such as **dates** (OrderDate, DeliveryDate) and **currency** (USD, EUR) are consistently formatted. You might need to standardize date formats across the dataset.
**Example:**  
- If Currency has values like "`USD`", "`usd`", "`US Dollar`", unify them to a single standard format, e.g., "`USD`".

### Solution
This was answered along with questions 1 and 2.

---

## Step 2: Data Analysis
After cleaning, extract insights and calculate key business metrics using DAX.

### 1. Calculate Total Sales
What is the total revenue from all products? You should create a measure that sums up `SalesAmount` for all rows in your cleaned dataset

### Solution

<img width="960" height="540" alt="Total revenue dax expression" src="https://github.com/user-attachments/assets/925ab0dd-8500-4221-adee-300bf9b2efc9" />
<img width="960" height="540" alt="Total revenue card" src="https://github.com/user-attachments/assets/bef99d17-60ea-4d55-b967-ec394eb22a42" />

### 2. Profit Margin Calculation
Profit margin is critical for understanding the profitability of your business. The formula to calculate profit margin is:
`Profit Margin=profit/SalesAmount × 100`
You need to create a **measure** that calculates this for each transaction and possibly by **product**, **region**, or **time period**.

### Solution

<img width="960" height="540" alt="Profit margin DAX expression" src="https://github.com/user-attachments/assets/d7460abd-08b8-4764-bd74-ecd056ddcc76" />
<img width="960" height="540" alt="Profit margin and slicers" src="https://github.com/user-attachments/assets/1860f038-1c53-4cfb-af92-362471da038f" />

### 3. Research Market Rates for Currency Conversion
The dataset uses different currencies (USD, EUR, GBP, etc.). You will need to research the current market exchange rates for the currencies used in the dataset. Using this data, create a DAX measure that converts all currencies to USD (or whichever currency you prefer). The rates can be obtained from various online sources.

Example:
- If you find the current exchange rate of **EUR to USD** is **1.1**, use this to convert all **EUR sales** into **USD**.

### Solution
The current exchange rate was found to be as follows:
- USD to CAD: 1 USD = 1.38 CAD
- CAD to USD: 1 CAD = 0.72 USD

I used these rates to create a currency conversion table and created a relationship between it and the main table:

<img width="960" height="540" alt="Currency conversion table" src="https://github.com/user-attachments/assets/5842f534-9fe4-4083-92ca-ee186f24c579" />

I then used a DAX expression with the `RELATED` function to create new columns and convert columns with currency data to USD:

<img width="960" height="540" alt="Currency columns in USD" src="https://github.com/user-attachments/assets/ff31315e-4ba5-4f5a-a631-55e7056358f5" />

### 4. Handling Missing or Incorrect Values
What happens when some rows have missing data, or when certain sales figures are too low (e.g., a negative profit)? How will you treat these cases in your analysis?

**Question to consider**:
- Should you exclude transactions with missing or extreme values, or should you adjust these values based on your business knowledge?

### Solution
It is important to understand the dataset to determine how missing or incorrect values should be handled. For example, a negative value in the profit column may not necessarily be an incorrect value, as it may indicate a loss.
It is best not to adjust values unless there is certainty that the changes will not make the analysis incorrect.

---

## Step 3: Data Modeling
Modeling in Power BI is about structuring your data efficiently, so that it can be easily analyzed and visualized.
### 1. Create Dimension Tables:
You'll need to create **dimension tables** to categorize and group your data. Think of dimension tables as lookup tables that store information like **Customer Information**, **City**, **Product Categories**, **Sales Reps**, and **Time**.

**Example:**  
- **Product Dimension**: Contains columns for `ProductName`, `Category`. This will help in analyzing which products perform the best.

### 2. Fact Table
The fact table will store transactional data such as `OrderID`, `SalesAmount`, `Profit`, `Quantity`, and `Discount`.  It's important to link your fact table to the dimension tables using **relationships**.

**Question to consider:**  
- How will the fact table relate to the **customer**, **product**, and **time** tables? Create the appropriate **relationships** in Power BI.

### 3. Time Dimension
A **Time Dimension** is crucial for time-based analysis. This table should include columns 
for `Year`, `Quarter`, `Month`, `Week`, `Day`, and `Date`. This will allow you to create **time-based aggregations** and trends (e.g., monthly sales, yearly growth).

### Solution

<img width="960" height="540" alt="Schema" src="https://github.com/user-attachments/assets/c7c51850-4370-458e-a226-3962e1ea80a4" />

---

## Step 4: Building the Dashboard

Your goal here is to create an interactive Power BI dashboard that allows stakeholders to gain valuable insights from the data. 

### 1. Key Visualizations
Examples: use only what you deem necessary or important for your dashboard. 
Consider the following visualizations that can bring out meaningful insights:
- **KPI Cards**: Display key metrics such as **Total Sales**, **Total Profit**, and **Profit Margin** etc.
- **Bar Chart/ Column**- Show **sales by product**, **sales by region**, or **sales by category**.
- **Line Chart**: Display **sales trends over time** (monthly, quarterly).
- **Pie Chart**: Show the **sales distribution by currency**, or **sales by region**.
- **Map Visual**

### 2. Slicers
Use **slicers** to allow users to filter the dashboard by **region**, **customer**, **time period**, and **product category**. This will make your dashboard interactive. 
**Example**: 
- A slicer for **year** will allow users to analyze sales data for different years.

### Solution

<img width="960" height="540" alt="Electronic sales data dashboard" src="https://github.com/user-attachments/assets/12d36692-d3b5-40b6-8afe-aae9d24d0651" />

---

## Step 5: Creating the Report
Once your dashboard is built, create a **detailed report** with all the necessary insights. Here are the key components to include:

### 1. Executive Summary:
Provide a brief summary of key insights, such as overall sales performance, top-performing products, and profitability.

### 2. Detailed Analysis:
Include in-depth analysis for specific metrics. For example, provide a detailed breakdown of **total sales by region**, **profit margins by product**, and **yearly trends**. 

### 3. Visual Insights:
Use charts, tables, and slicers to highlight trends and make the report interactive. Ensure the report answers questions like: 
- What are the top-performing products?
- Which region has the highest profit margin?
- How has sales been trending over the last year?

### 4. Recommendations:
Based on the data, provide business recommendations, such as:
- Which products should be promoted based on high sales and profit margins?
- How should the company address regions with lower profitability? 

---

## Example Questions to Guide Analysis
- How do exchange rate fluctuations affect sales?
- How should repeat customers be handled?
- Should missing data be excluded or estimated?

### Solution
- Report Page 1 (Dashboard):
<img width="960" height="540" alt="Electronic sales data dashboard" src="https://github.com/user-attachments/assets/59b2b600-f5ce-4868-99d6-e1eeb537a846" />

- Report Page 2 (Product Details)
<img width="960" height="540" alt="Product details report" src="https://github.com/user-attachments/assets/1aeab45c-7199-4e41-a87f-cf90d88347a7" />

- Report Page 3 (Customer Information)
<img width="960" height="540" alt="Customer Information Report" src="https://github.com/user-attachments/assets/17beae4b-940d-4cb5-a18f-7a50b248c605" />

- Report Page 4 (Geographical Information)
<img width="960" height="540" alt="Geographical information" src="https://github.com/user-attachments/assets/398c45e5-c81c-43f7-a453-751fbb3aad06" />
