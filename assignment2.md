# Assignment 2  
## Data Analysis Dashboard Project  

### Project Title
**Jumia Product Performance Dashboard: Analyzing Pricing, Discounts, and Customer Reviews**

---

## Project Objective
The objective of this project is to design and build an interactive Excel dashboard that analyzes the performance of products listed on Jumia. Students will explore how pricing, discounts, reviews, and ratings influence product performance and customer engagement.  

The final dashboard should support data-driven decision-making in an e-commerce context.

---

## Dataset Overview
The dataset contains product-level data with the following columns:

- **Product** – Name of the product  
- **Current Price** – Current selling price in Kenyan Shillings (KSh)  
- **Old Price** – Original price before discount in Kenyan Shillings (KSh)  
- **Discount** – Discount percentage applied to the product  
- **Reviews** – Number of customer reviews  
- **Rating** – Average customer rating out of 5  

---

## Data Cleaning and Preparation
- Check for and handle missing values, especially in the **Reviews** and **Rating** columns  
- Identify and remove duplicate product entries  
- Convert price columns into numeric format by removing `"KSh"`, commas, and text  
  - Use **Split Text to Columns** (Data tab) or **Find and Replace (`Ctrl + H`)**  
- Ensure the **Discount** column is numeric and properly formatted as a percentage  
  - Use Find & Replace, `LEFT/RIGHT` functions, or Text to Columns  
- Convert the **Rating** column from text format (e.g., `"4.5 out of 5"`) into numeric values  
- Convert negative reviews to positive  

---

## Data Enrichment
Create the following additional columns:

- **Discount Amount (KSh)**  
  `= Old Price - Current Price`

- **Rating Category**
  - *Poor* → ratings below 3  
  - *Average* → ratings between 3 and 4.4  
  - *Excellent* → ratings of 4.5 and above  

- **Discount Category**
  - *Low Discount* → discounts below 20%  
  - *Medium Discount* → discounts between 20% and 40%  
  - *High Discount* → discounts above 40%  

---

## Data Analysis

### Descriptive Analysis
- What is the average current price, old price, discount percentage, and rating?  
- Which product is the most expensive and which is the least expensive?  
- What is the average rating and discount by discount category?  
- How are products distributed across rating categories?  

---

### Trend and Relationship Analysis
- Analyze the relationship between discount percentage and number of reviews  
- Analyze the relationship between rating and number of reviews  
- Determine whether higher discounts lead to increased customer engagement  
- Determine whether higher-rated products tend to have more reviews  

---

### Product Performance Analysis
- Identify the **top 10 products with the highest discounts**  
- Identify the **top 10 products with the most reviews**  
- Identify the **top 5 highest-rated** and **bottom 5 lowest-rated products**  
- Compare high-discount and low-discount products based on:
  - Average rating  
  - Number of reviews  

---

## Dashboard Design

### Dashboard Requirements
Create a single interactive Excel dashboard containing the following sections:

---

### Overview
- Total number of products  
- Average rating  
- Average discount percentage  
- Total number of reviews  

---

### Product Performance
- Top products by rating  
- Top products by number of reviews  
- Top products by discount percentage  

---

### Trend Analysis
- Visualizations showing:
  - Discount percentage vs reviews  
  - Rating vs reviews  

---

### Product Categories
- Breakdown of products by rating category  
- Breakdown of products by discount category  

---

## Visualization Guidelines
- Use **Pivot Tables** as the primary data source  
- Use appropriate charts:
  - Bar charts  
  - Column charts  
  - Pie or donut charts  
  - Scatter plots  
- Apply **conditional formatting** to highlight:
  - High discounts  
  - Low ratings  
- Include **slicers** for:
  - Rating category  
  - Discount category  
  - Price range (where applicable)

#SOLUTIONS
## Data Cleaning and Preparation
- Check for and handle missing values, especially in the **Reviews** and **Rating** columns
  
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d0832c16-ba56-4bd6-97e3-a1c69ff54ca6" />
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/fd8d6ea6-93dc-4a06-a924-f9bcdf0ced54" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/10f9653c-bdc7-452e-ab51-e79691ac6425" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/da617328-fb99-47c7-b31e-04a064d7fbfa" />

- Identify and remove duplicate product entries

  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d420590b-768a-4f46-9d4c-096b1c6e3edb" />
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0a29722e-5b7f-4911-976c-b6ff8f241d98" />

- Convert price columns into numeric format by removing `"KSh"`, commas, and text  
  - Use **Split Text to Columns** (Data tab) or **Find and Replace (`Ctrl + H`)**
  
