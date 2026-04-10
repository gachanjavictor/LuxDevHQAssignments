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
- Create a measure to sum all `SalesAmount`.

### 2. Profit Margin Calculation
**Formula:**
- Create measures by:
  - Product
  - Region
  - Time period

### 3. Currency Conversion
- Research exchange rates (USD, EUR, GBP, etc.)
- Create a DAX measure to standardize currency.

**Example:**  
- If `EUR → USD = 1.1`, convert all EUR sales accordingly.

### 4. Handling Missing or Incorrect Values
Consider:
- Missing data
- Negative profit values

**Questions:**
- Should you exclude extreme values?
- Or adjust them using business logic?

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
