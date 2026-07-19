# Lab 6: Market Basket Analysis Using FP-Growth and Apriori

**Student:** Vamsi Krishna Matta  
**Course:** MSCS 634 – Advanced Big Data and Data Mining  
**Lab:** Lab 6  
**Dataset:** Online Retail Dataset  

## Project Overview

This project analyzes retail invoice data to identify products that are frequently purchased together. FP-Growth and Apriori are used to discover frequent itemsets, while association rules are evaluated through support, confidence, and lift.

The notebook follows an FP-Growth-first workflow and then applies Apriori using the same transaction basket and support threshold. This structure supports a direct comparison of pattern counts, rule counts, and execution times.

## Objectives

The objectives of this lab are to:

- Inspect and prepare transactional retail data.
- Remove cancelled and invalid transaction records.
- Explore missing values and country-level transaction activity.
- Create a Boolean invoice-product matrix.
- Identify frequent itemsets using FP-Growth.
- Generate and evaluate association rules.
- Apply Apriori to the same transaction basket.
- Compare algorithm output and execution time.
- Visualize product frequencies, itemset patterns, and rule quality.
- Interpret the business value of the discovered relationships.

## Dataset

The Online Retail dataset contains invoice-level product transactions from an online retailer.

Important columns include:

- `InvoiceNo`: transaction identifier
- `StockCode`: product code
- `Description`: product name
- `Quantity`: purchased quantity
- `InvoiceDate`: transaction date and time
- `UnitPrice`: unit price
- `CustomerID`: customer identifier
- `Country`: customer location

Each invoice may contain multiple products, making the dataset appropriate for market basket analysis.

## Data Preparation

The following preprocessing steps were completed:

- Removed rows with missing product descriptions.
- Removed cancelled invoices.
- Removed zero or negative quantities.
- Removed zero or negative unit prices.
- Standardized product descriptions.
- Focused the analysis on United Kingdom transactions.
- Selected the forty most frequently appearing products.
- Grouped products by invoice.
- Converted the resulting basket into Boolean values.

In the final transaction matrix:

- Rows represent invoices.
- Columns represent products.
- `True` indicates that a product appears in an invoice.
- `False` indicates that it does not.

## FP-Growth Analysis

FP-Growth was applied before Apriori with a minimum support threshold of 0.02.

The algorithm identified:

- Frequent individual products.
- Frequently occurring product pairs.
- Larger multi-product combinations.
- Association rules meeting the selected confidence threshold.

Itemsets were also grouped by size to examine the distribution of single-product and multi-product patterns.

## Association Rules

Rules were generated using a minimum confidence value of 0.50. Rules with lift values greater than one were retained.

The following measures were used:

### Support

Support measures the proportion of invoices containing the complete itemset.

### Confidence

Confidence measures the likelihood that the consequent appears when the antecedent is present.

### Lift

Lift compares the observed relationship with the relationship expected under independence.

A lift greater than one indicates a positive product relationship.

## Apriori Analysis

Apriori was executed using the same Boolean basket and support threshold. This allowed a fair comparison between the two algorithms.

The comparison included:

- Number of frequent itemsets.
- Number of association rules.
- Itemset-size distribution.
- Rule strength.
- Execution time.

## Visualizations

The notebook includes:

- Missing-value visualization.
- Country transaction distribution.
- Frequently purchased products.
- FP-Growth itemset-size distribution.
- Frequent product combinations.
- Confidence-lift-support bubble plot.
- Strongest rules ranked by lift.
- Apriori itemset-size distribution.
- Apriori support chart.
- Apriori confidence-versus-lift plot.
- Runtime comparison.

## Key Findings

The analysis showed that:

- Popular products produced high support.
- Multi-product itemsets provided useful purchasing-pattern information.
- High confidence did not always correspond to high lift.
- Lift was necessary to identify relationships stronger than random occurrence.
- Both algorithms found similar patterns under the same support conditions.
- Runtime differences reflected the distinct computational strategies of FP-Growth and Apriori.

## Business Value

The results can support:

- Product recommendation systems.
- Cross-selling.
- Bundle development.
- Inventory coordination.
- Promotional planning.
- Website product placement.
- Personalized marketing.

## Challenges

The main challenges included:

- Missing and invalid transaction records.
- Large numbers of unique products.
- Sparse transaction data.
- Threshold selection.
- Balancing pattern quality with computational efficiency.
- Avoiding conclusions based only on lift without considering support.

## Technologies Used

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Seaborn
- MLxtend
- OpenPyXL

## Repository Structure

```text
MSCS_634_Lab6_Market_Basket_Analysis/
│
├── Retail_Market_Basket_Analysis_Lab6.ipynb
├── Online Retail.xlsx
├── README.md
└── Result screenshots/