# FMCG Sales, Inventory & Promotion Analysis

## Company Overview

**CenturaFoods Ltd.** is a fictional Fast-Moving Consumer Goods (FMCG) company that produces and distributes a range of packaged food products, including tomato paste, powdered milk, spaghetti, and seasoning cubes. With operations across key Nigerian cities such as Lagos, Abuja, Port Harcourt, Kano, and Ibadan, CenturaFoods is committed to delivering affordable and nutritious products to a wide customer base through retail, wholesale, and distributor channels.
This project simulates CenturaFoods' core operations, focusing on sales tracking, inventory management, product return analysis, and promotional impact, using fictitious data that reflects real-world challenges faced by FMCG businesses.

## Project Description

This project analyzes key operations of CenturaFoods Ltd. through a comprehensive Power BI report. The focus is on understanding sales trends, inventory levels, product returns, and the impact of promotions across five major Nigerian cities.
The dataset covers a period of one month and is simulated to reflect real-world FMCG business challenges and decision-making scenarios. Through the use of key performance indicators (KPIs), interactive visuals, and data-driven insights, the project supports decision-making in the following areas:

- Sales performance tracking across products and regions
- Inventory health monitoring to avoid stockouts and overstocking
- Return analysis to identify quality or logistics issues
- Evaluation of promotional effectiveness across SKUs

The Power BI report is organized into multiple analytical pages, offering both high-level summaries and detailed insights. It is designed to be user-friendly and relevant for various business stakeholders, including executives, sales managers, supply chain teams, and marketing analysts.

## Business Problems & Problem Statements

### Business Problems
CenturaFoods faces several operational challenges that impact efficiency, sales performance, and decision-making:

- Inconsistent sales performance across regions and product lines
- Overstocking and frequent stockouts due to limited inventory visibility
- High rates of product returns with limited root cause analysis
- Difficulty measuring the true impact of promotions on sales
- Lack of centralized reporting for different business units

### Problem Statements
This project aims to answer the following key business questions:

- How can we compare sales performance across regions and product categories?
- Which products or regions are experiencing frequent stockouts or overstock situations?
- What patterns can be identified in product returns, and where are they most frequent?
- Do promotional activities lead to a measurable increase in sales?
- How can we present this information clearly for different business teams?

## Business Objectives

This project aims to support data-driven decision-making at **CenturaFoods Ltd.** by analyzing sales trends, inventory health, product returns, and promotional performance. The Power BI report is designed to provide insights that can guide strategic planning and improve operational efficiency.

The specific business objectives include:

- **Monitoring sales performance** across products, SKUs, and regions to identify top- and underperforming areas.  
- **Tracking inventory levels** to detect and prevent stockouts or overstocking situations.  
- **Analyzing product return patterns** to uncover potential quality or distribution issues.  
- **Delivering a detailed report** tailored to executives, sales managers, supply chain teams, and marketing analysts.  
- **Establishing a data foundation** for future demand forecasting and operational planning.

## Dataset Description

The dataset used in this project is a simulated FMCG business dataset created to mimic real-world operations of **CenturaFoods Ltd.** It covers a 1-month period (July 2025) and includes daily records of product sales, inventory levels, returns, and promotional activities across five major Nigerian cities: Lagos, Abuja, Port Harcourt, Kano, and Ibadan.

The dataset was generated to reflect realistic patterns in sales and inventory movement across multiple products and SKUs within the FMCG sector. It forms the basis for all visualizations, KPIs, and insights presented in the Power BI report.

**Rows:** 776

**Columns:** 10

**File Format:** Excel (.xlsx)

**File Name:** FMCG_Sales_Inventory_Data_July2025.xlsx

You can find the dataset [**here**](https://github.com/Rolakamin/FMCG-Sales-Inventory-Promotion-Analysis/blob/main/FMCG_Sales_Inventory_Data_July2025.xlsx).


### Data Dictionary

| Column Name     | Description                                              |
| --------------- | -------------------------------------------------------- |
| Date            | Transaction date for each sales and inventory record     |
| Region          | The location/market where the sale occurred              |
| Product         | Name of the product (e.g. Tomato Paste, Spaghetti)       |
| SKU             | Unique product identifier or variant                     |
| Units Sold      | Quantity of product sold on that specific date           |
| Unit Price      | Price per unit of the product                            |
| Sales Value     | Total revenue for that entry (Units Sold × Unit Price)   |
| Inventory Level | Number of units available in stock at the end of the day |
| Returned Units  | Number of units returned by customers                    |
| Promotion       | Indicates whether a promotion was active (Yes or No)     |

**Note:**
**All data used in this project is fictitious and created solely for learning and portfolio purposes. It does not represent actual business data from any real-world company.**

## Data Cleaning

The dataset used in this project was already well-structured and required minimal cleaning. The following steps were carried out during the preparation phase in Power Query:

- Column data types were reviewed and corrected where necessary (e.g., currency fields set to decimal).
- Minor formatting adjustments were applied to ensure smooth data loading and accurate calculations.
- No missing values or duplicate records were found.

The dataset was considered clean and ready for direct use in analysis and reporting.

## Tools

The following tools were used to develop this project:

- **Power BI**: For building interactive report and visualizing data  
- **Power Query**: For light data transformation and data type adjustments within Power BI  
- **DAX (Data Analysis Expressions)**: For creating calculated measures and KPIs



## Data Analysis

## Data Analysis

The following KPIs were defined and calculated using DAX in Power BI. They are grouped based on business areas and aligned with CenturaFoods Ltd.’s sales, inventory, promotional, and returns monitoring objectives.

### Sales Performance

1. **Total Sales Value**
   
**Definition**: Total revenue generated from all product sales during the analysis period. 

DAX:
```
Total Sales Value = SUM(FMCG_data[Sales Value])
```

2. **Total Units Sold**
   
**Definition**: Total number of units sold across all SKUs.

**DAX**:
```
Total Units Sold = SUM(FMCG_data[Units Sold])
```

3. **Average Daily Sales**
   
**Definition**: Average revenue generated per day during the analysis period.

**DAX**:
```
Average Daily Sales = 
AVERAGEX(
    VALUES(FMCG_data[Date]),
    [Total Sales Value]
)
```

4. **Average Sales per Transaction**
   
**Definition**: The average value of each sales transaction.

**DAX**:
```
Average Sales per Transaction = 
DIVIDE([Total Sales Value], COUNTROWS(FMCG_data))
```

### Inventory Monitoring

1. **Average Inventory Level**

**Definition**: The mean inventory held across all locations and products during the period.

**DAX**:
```
Average Inventory Level = AVERAGE(FMCG_data[Inventory Level])
```

2. **Inventory Turnover**

**Definition**: Number of times inventory was sold and replaced during the month.

**DAX**:
```
Inventory Turnover = 
DIVIDE([Total Units Sold], [Average Inventory Level])
```

### Promotion Analysis

1. **Promo Sales**

**Definition**: Total revenue from transactions where a promotion was applied

**DAX**:
```
Promo Sales = 
CALCULATE([Total Sales Value], FMCG_data[Promotion] = "Yes")
```

2. **Non-Promo Sales**

**Definition**: Total revenue from transactions without any promotion.

**DAX**:
```
Non-Promo Sales = 
CALCULATE([Total Sales Value], FMCG_data[Promotion] = "No")
```

3. **Promotion Uplift (%)**

**Definition**: The percentage change in sales due to promotions, compared to non-promotional sales.

**DAX**:
```
Promotion Uplift % = 
DIVIDE([Promo Sales] - [Non-Promo Sales], [Non-Promo Sales], 0)
```

### Returns

1. **Total Returned Units**

**Definition**: Total quantity of products returned during the analysis period.

**DAX**:
```
Total Returned Units = SUM(FMCG_data[Returned Units])
```

2. **Unit Return Rate**

**Definition**: Percentage of sold units that were returned.

**DAX**:
```
Unit Return Rate = 
DIVIDE([Total Returned Units], [Total Units Sold], 0)
```

All DAX measures were stored in a dedicated DAX_Measures table in Power BI, grouped into folders such as Sales Performance, Inventory, Promotions, and Returns for better organization.










## Data Analysis

This section outlines the key metrics, KPIs, and a report developed to analyze CenturaFoods' operations and support business decision-making.

### Key Metrics & KPIs

The following KPIs were created using DAX in Power BI to track performance across sales, inventory, returns, and promotions:

- **Total Sales Value** – The total revenue generated (Units Sold × Unit Price)
- **Total Units Sold** – Sum of product units sold across all records
- **Return Rate** – Percentage of sold units that were returned  
  > _Formula: Returned Units ÷ Units Sold_
- **Average Daily Sales** – Average sales value per day over the period  
- **Inventory Turnover Rate** – Measures how quickly inventory is sold  
  > _Formula: Units Sold ÷ Average Inventory_
- **Promotion Uplift %** – Sales improvement during promotions  
  > _Formula: (Promo Sales - Non-Promo Sales) ÷ Non-Promo Sales_
- **Inventory Days Remaining** – How long current inventory will last based on sales rate

> All calculations were done using DAX measures within Power BI, and formatted for clarity using ₦ (Naira) currency.

---

### Report Structure

The Power BI report is structured across five analytical pages:

#### **1. Executive Summary**
- Total sales, units sold, return rate
- Sales trend (line chart)
- Sales by region (map or bar chart)
- Top-performing products

#### **2. Sales Analysis**
- Sales by product and SKU
- Sales by region
- Daily trend visualizations
- Filters: Region, product, promotion

#### **3. Inventory Monitoring**
- Inventory levels vs. units sold
- Inventory turnover rate
- Inventory days remaining
- Low stock alerts (based on threshold)

#### **4. Returns Analysis**
- Return rate by product and region
- Return trend over time
- High-return products flag

#### **5. Promotion Impact**
- Sales during promotions vs. non-promotions
- Promotion uplift % by product
- Sales trend filtered by promotion status

---

### Insights & Observations

(Insert your own insights from the dashboard here. You can fill this in once you're done analyzing your visuals.)_

Example placeholders:
- Spaghetti performed best in Lagos, especially during promotions (↑25% sales uplift)
- Tomato Paste had high return rates in Port Harcourt — quality or logistics issue?
- Milk Powder showed strong consistent sales but low promotion responsiveness

---







