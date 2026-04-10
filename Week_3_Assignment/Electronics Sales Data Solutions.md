# Power BI Project: Electronics Sales Data

## Objective
This project is designed to guide you through the entire Power BI workflow for a real-world scenario involving dirty sales data. You’ll be tasked with cleaning, analyzing, and modeling the data to create a comprehensive dashboard and a detailed report that includes key business insights.  

The dataset includes various real-world challenges such as inconsistent data, missing values, and currency discrepancies. Your goal is to transform this data into something useful for decision-making in an electronics retail business.

---

## Instructions

## Step 1: Data Cleaning
Data cleaning is often the most time-consuming part of any analytics project. It's essential to ensure that your data is both accurate and consistent.

### 1. Ensure Consistency in Data Types
Some columns might have inconsistent data types.  
- Example:  
  - `OrderDate` → should be a date  
  - `SalesAmount` → should be numeric  
- Check for text values that don’t match expected formats.

### 2. Check for Spelling Errors
Look for inconsistencies in:
- Product names  
- Country names  
- Customer emails  

**Example:**  
- "Samsung Galaxy S21"  
- "Samsung GAlaxy S21"  

**Tip:** Filter product names to standardize them.

### 3. Missing or Incomplete Data
Check for empty or missing values in:
- `Profit`
- `SalesAmount`
- `ShippingCost`

Decide whether to:
- Remove
- Impute
- Fill missing values

### 4. Pseudonyms and Invalid Entries
Some entries may include:
- "Anonymous"
- "N/A"

**Example:**  
- A row with `CustomerName = "N/A"` in a paid transaction should be flagged.  
- Ensure pseudoblanks are handled consistently.

### 5. Ensure Correct Data Formats
Standardize formats for:
- Dates (`OrderDate`, `DeliveryDate`)
- Currency (`USD`, `EUR`)

**Example:**  
- "USD", "usd", "US Dollar" → **standardize to "USD"**

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
