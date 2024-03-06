# Sales Analysis Of An Acquisition Target Retailer


## Table of Contents

 - [Project Overview](#project-overview)
 - [Data Sources](#data-sources)
 - [Tools](#tools)
 - [Data Exploration](#data-exploration)
 - [Column Creation](#column-creation)
 - [Data Analysis](#data-analysis)
 - [Results](#results)
 - [Limitations](#limitations)
 - [Recommendations](#recommendations)
 - [References](#references)




## Project Overview

This project was carried out in order to aid a mega store's decision on whether or not to acquire a retailer to boost it's shares.

The key objective was to:
  1. Read in Data from multiple csv files
  
  2. Explore data containing millions of rows
  
  3. Create new columns to aid in analysis
  
  4. Filter, sort, and aggregate the data to pinpoint and summarize the important information
  
  5. Build plots to communicate key insights
  
  6. Give my thoughts where I deem fit and give my recommendation at the end

This is a snapshot of one the chart that answered a paricular question during the analysis.


<img width="451" alt="Top10_Households_by_Sales" src="https://github.com/EMMY9ICE/DATA-ANALYSIS-PROJECTS/assets/101521067/ad5bbf86-349f-4423-84d8-9c8c0695db34">


## Data Sources

Two main data sets was used in this project, they are "project_transactions.csv" and "products.csv" files. 
The "project_transactions.csv" file contains informations about the sales value of the households, with a unique household key and product ID as well as discounts on products.
The "products.csv" data includes more detailed description of the products of the target retailer


## Tools

- Python - Python was the sole analytical tool used throughout this project, its libraries like Pandas and Numpy was used to explore the data, perform aggregations and show plots

- Jupyter Notebook - Jupyter Notebook was used to create interactive notebook documents that contain equations, visualizations and other computational outputs. Jupyter Notebook is a preffered tool by data analyst, data scientists and students to document and demonstrate coding workflows and Python codes can as well be written on it.

- Anaconda Navigator - In this project, the Anaconda Navigator was used to launch Jupyter Notebook.
Anaconda Navigator is a desktop graphical user interface (GUI) included in Anaconda distribution that allows users to launch applications and manage conda packages, environments and channels without using command-line commands.
 - [Download_Anaconda](https://anaconda.com)



## Data Exploration

In the beginning stages of the data exploration, the following task was performed:

  1. Read in the data sets and explore it.

  2. Take a look at the raw data, the datatypes, and cast columns to appropiate data types to optimize memory usage.

  3. Check for missing data

  4. Check the number of unique households and products in the data, as this gives a clue of our customer size and product range




## Column Creation

In this stage of the project, new columns were created in order to aid the analysis process.

 We did the following:

  1. Create a column that captures the total_discount by row.

  2. Create a column of percentage disount (positive).

  3. If the percentage discount is greater than 1, set it equal to 1. If it is less than 0, set it to 0 (as instructed by the mega store)

  4. Drop the individual discount columns (RETAIL_DISC, COUPON_DISC, COUPON_MATCH_DISC).

  5. Overwrite the existing transaction DataFrame after making the modifications above.


# Data Analysis

The Data Analysis phase involved:
  1. Calculating statistical figures, like the total sales, total discount and overall percentage discount of the data.
     Below is an example of some of a code written
      ```Python
      transactions.loc[:, "SALES_VALUE"].sum()
      ```

  2. Performing household analysis on the data to determine for example, the top 10 households by sales value and visualizing it with a simple bar plot.
     Below is an example of a code written.
       ```Python
      (transactions
       .groupby("household_key")
       .agg({"SALES_VALUE": "sum"})
       .sort_values(by="SALES_VALUE", ascending=False)
       .iloc[:10]
      )
       ```

  3. Analyzing the "products.csv" data set in comparison to the "project_transacions.csv" data set so as to determine some key insights.
     For example, look up the names of the top 10 products by sales in the products.csv dataset.
     Below is an example of a code written.
        ```Python
        products.query("PRODUCT_ID in @top10_pd_by_sales.index").loc[:, ["COMMODITY_DESC", "SUB_COMMODITY_DESC"]]
        ```


##  Results

In this phase one of the analysis of the target retailers data, we have been able to take a deep dive into the businesses data, answered important statistical question, illustrated sales of various sorts by charts and draw insights from the business data.

The results of the analysis points to the fact that :

1. The business has good sales relative to the number of household
2. The top selling products are not even the most discounted, so there is a good discount strategy in place.


## Limitations

By the data sets given and the analysis performed, we still have no clue on what age group of people or what income range of people are buying what products exactly, in a later phase of this project when we have all datas to work with, we will be able to determine these factors which is also worth considering when making acquisition.
This will give more insights about those purchasing the products of the target retailer, their age bracket and income range. This will further help our clients decide whether or not to go ahead with the acquistiton of the retail.


## Recommendations

Based on this phase of analysis, It is abvious that the target retailer is doing business with the right strategy and acquiring them is a good decison, but we will need more analysis to further strengthen this decision and back up our claim from this project analysis analysis.


## References

Data Sets from Udemy: Python for Data Analysis; Numpy and Pandas Masterclass by Mavin Analytics

