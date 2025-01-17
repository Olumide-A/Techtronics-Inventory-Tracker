# Techtronics Inventory Management Tracker

## Table of Contents
1. [Problem Statement](#problem-statement)
2. [Objective](#objective)
3. [Solutions Implemented](#solutions-implemented)
    1. [Data Cleaning and Preparation](#data-cleaning-and-preparation)
    2. [Stock Level Indicator](#stock-level-indicator)
    3. [Data Validation](#data-validation)
    4. [Tracker Sheet Design](#tracker-sheet-design)
    5. [Conditional Formatting](#conditional-formatting)
    6. [Reorder Spend Calculation](#reorder-spend-calculation)
4. [Key Features of the Tracker](#key-features-of-the-tracker)
5. [Impact and Value](#impact-and-value)
6. [Link to the Tracker](#link-to-the-tracker)

## Problem Statement
Effective inventory management is critical for retail businesses to ensure stock availability, reduce operational costs, and avoid missed sales opportunities. For Techtronics, an electronics and gadget store, the challenge lay in accurately tracking inventory levels, identifying stock shortages promptly, and making informed reorder decisions. The absence of an efficient system meant that manual checks and scattered data made it difficult to ensure optimal stock levels.

## Objective
To design a dynamic and user-friendly inventory management tracker in Google Sheets that:
- Provides real-time visibility into stock availability.
- Automates the identification of products requiring restocking.
- Calculates the expected reorder spend to enable strategic restocking decisions.
- Enhances decision-making efficiency through clear visual cues and filtering capabilities.

## Solutions Implemented

### 1. Data Cleaning and Preparation
- **Column Optimization**: Removed unnecessary columns to focus on essential inventory data.
- **Data Type Standardization**: Converted the unit price column to a currency format to enhance clarity.
- **Quantity Available Calculation**: Introduced a formula to calculate the remaining stock for each product.

### 2. Stock Level Indicator
- **Logic Implementation**: Created a new column with a stock level indicator using the IFS formula:
    ```excel
    =IFS(F2=0,TRACKER!$C$3,F2<=50,TRACKER!$C$2,F2>50,TRACKER!$C$1)
    ```
- **Thresholds**:
    - **Available**: Stock > 50
    - **Running Low**: Stock ≤ 50
    - **Out of Stock**: Stock = 0

### 3. Data Validation
- Ensured data integrity by checking for duplicate Product IDs using:
    ```excel
    =IF(COUNTIF(B:B, B2) > 1, "Duplicate", "Unique")
    ```
    This confirmed that each product ID in the dataset was unique, preventing errors in inventory tracking.

### 4. Tracker Sheet Design
- **Dropdown Menu**: Implemented a dropdown menu to select stock availability statuses for easier filtering.
- **Dynamic Inventory Filtering**: Used the FILTER formula to extract relevant data based on stock availability:
    ```excel
    =FILTER('RAW INVENTORY'!$A$2:$H$86,'RAW INVENTORY'!$H$2:$H$86=A2)
    ```
    This allowed for quick identification of products within specific availability categories.

### 5. Conditional Formatting
- Applied color-coded formatting to the stock level column to visually prioritize restocking needs:
    - **Red**: Out of Stock
    - **Yellow**: Running Low
    - **Green**: Available

### 6. Reorder Spend Calculation
- Added a Reorder Spend column to calculate the expected cost of restocking items that are running low or out of stock:
    ```excel
    =IF(H6="Available","NIL",IF(H6=0,"",E6*G6))
    ```
    - For items marked as "Available," the spend is set to "NIL."
    - For "Running Low" or "Out of Stock," the formula multiplies the reorder quantity by the unit price.
- **Aggregate Calculation**: Summed up the reorder spend for all applicable items using:
    ```excel
    =SUM(reorder spend)
    ```
    This provided a quick view of the total cost required for strategic restocking.

## Key Features of the Tracker
- **Automated Stock Monitoring**: The tracker dynamically updates stock levels and provides insights into product availability.
- **Actionable Alerts**: Visual cues highlight critical stock levels, enabling quick response to inventory needs.
- **Cost Analysis**: The reorder spend feature supports budget-conscious decision-making by estimating the cost of replenishment.
- **User-Friendly Design**: Dropdowns, filters, and conditional formatting simplify navigation and data analysis.

## Impact and Value
The Techtronics Inventory Management Tracker has significantly streamlined the store’s inventory processes by:
- Reducing time spent on manual stock checks.
- Ensuring products are adequately stocked, minimizing stockouts and lost sales.
- Providing clarity on financial commitments for restocking.
- Enhancing overall efficiency and accuracy in inventory management.

## Link to the Tracker
To explore the full tracker, visit Techtronics Inventory Management Tracker.

---

This project demonstrates my ability to apply data analytics and Google Sheets functionalities to solve real-world inventory challenges effectively. It showcases skills in data cleaning, formula design, dynamic filtering, and decision-making support systems.

