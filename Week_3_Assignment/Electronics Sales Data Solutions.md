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
Structure your data for efficient analysis.

### 1. Create Dimension Tables
Examples:
- Customer Information  
- City  
- Product Categories  
- Sales Representatives  
- Time  

**Example:**  
- **Product Dimension**
  - `ProductName`
  - `Category`

### 2. Fact Table
Contains:
- `OrderID`
- `SalesAmount`
- `Profit`
- `Quantity`
- `Discount`

Link fact table to dimension tables.

**Question:**  
- How will relationships be defined between:
  - Customer
  - Product
  - Time

### 3. Time Dimension
Include:
- Year
- Quarter
- Month
- Week
- Day
- Date

Enables:
- Monthly sales
- Yearly growth analysis

---

## Step 4: Building the Dashboard

Create an interactive Power BI dashboard.

### 1. Key Visualizations
Use only what is necessary:

- **KPI Cards**
  - Total Sales
  - Total Profit
  - Profit Margin  

- **Bar/Column Chart**
  - Sales by product
  - Sales by region
  - Sales by category  

- **Line Chart**
  - Trends over time  

- **Pie Chart**
  - Sales distribution by currency or region  

- **Map Visual**

### 2. Slicers
Allow filtering by:
- Region
- Customer
- Time period
- Product category  

**Example:**  
- Year slicer for comparing yearly sales

---

## Step 5: Creating the Report

### 1. Executive Summary
Summarize:
- Sales performance
- Top products
- Profitability

### 2. Detailed Analysis
Include:
- Sales by region
- Profit margins by product
- Yearly trends

### 3. Visual Insights
Use charts and slicers to answer:
- What are the top-performing products?
- Which region has the highest profit margin?
- How have sales trended over time?

### 4. Recommendations
Provide actionable insights:
- Which products to promote
- How to improve low-performing regions

---

## Example Questions to Guide Analysis
- How do exchange rate fluctuations affect sales?
- How should repeat customers be handled?
- Should missing data be excluded or estimated?

---

## Power BI Report Structure

### 1. Pages in a Report
- Multiple pages (like slides)
- Each page focuses on a specific analysis

### 2. Main Page (Dashboard)
- KPI cards
- Slicers
- Key visuals
- High-level insights

### 3. Additional Pages
Example structure:
- Page 1: KPIs & trends  
- Page 2: Product performance  
- Page 3: Geographic analysis  
- Page 4: Customer/store analysis  

### 4. Page Navigation
- Use buttons like:
  - "Next Page"
  - "Back to Dashboard"

---

## Steps to Create Pages

### 1. Create a New Page
- Click "+" in Power BI Desktop  
- Rename appropriately

### 2. Design Dashboard Page
- KPI cards  
- Charts (bar, pie, line)  
- Slicers  

### 3. Create Additional Pages
- Focus each page on a single topic

### 4. Add Interactivity
- Buttons for navigation  
- Drill-down features  

### 5. Final Structure
- Page 1 → Overview  
- Other pages → Detailed insights  

---

## Navigation Between Pages
- Click tabs at the bottom  
- Use navigation buttons for smoother UX  

---

## Conclusion
This project challenges you to apply the full Power BI workflow:
- Data cleaning  
- Data modeling  
- DAX calculations  
- Dashboard creation  

By the end, you will have built a comprehensive Power BI report that delivers actionable insights into an electronics sales business.
