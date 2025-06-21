# Railway-Operational-Analysis
### INTRODUCTION
A railway operation project focuses on optimizing the planning, management, and execution of train movements and railway services. These projects are crucial for ensuring efficiency, safety, and customer satisfaction in rail transport systems. They include information about the date of purchase, time of purchase, purchase type, payment method, ticket class, ticket time, price, and departure station.

**Table of Contents**
- Project Overview
- Project scope
- Business objectives 
- Document purpose 
- Use case
- Skills Demonstrated
- Data Source
- Data Connection Details
- Data Profiling
- Data Modelling
- Data cleaning and processing 
- Data Analysis and insight
- Data Visualization 
- Recommendation 
- Conclusion

**Project Overview**

This project focuses on analyzing a comprehensive dataset of over 31,000 railway ticket transactions to uncover operational patterns, customer behavior, and service performance. The dataset includes key attributes such as purchase type, ticket price, journey timings, payment methods, rail card usage, delays, and refund requests.
By performing in-depth data cleaning, transformation, and analysis, the goal is to provide actionable insights that help railway operators enhance service quality, reduce delays, and optimize pricing strategies.

**Project Scope**

This project analyzes train ticket transactions, journey patterns, delays, and payment behavior to identify actionable insights that can improve customer service, scheduling, and revenue optimization

  **Business Objectives**
  
- Identify peak travel periods and common routes.
- Understand payment methods and ticket pricing trends.
- Investigate causes and patterns of delays.
- Recommend ways to improve customer satisfaction and reduce refund requests.

**Purpose of the Document**

To provide a comprehensive breakdown of the data analysis project based on railway transaction data, including data preparation, analysis, visualization, and recommendations

**Use Case Overview**

- Target Audience: Railway operation managers and data-driven decision makers.
- Use Case: Improve scheduling efficiency, reduce delays, optimize pricing, and enhance the customer experience.

**Demonstrated Skills**

**Data Connection in Power BI**
- Data wrangling and cleaning
- Exploratory data analysis
- Data visualization using Power BI
- Handling missing data
- Deriving business insights from transactional data

**Data Source Identification**

**Source:** A [Maven Analytics CSV](https://mavenanalytics.io/data-playground?order=date_added%2Cdesc&search=uk&tags=Transportation) dataset titled railway.csv representing 31,653 railway ticket transactions, including: Transaction details, Payment methods, Journey schedule, delays, and Refund requests

**Details of Data Connection**

To connect to an Excel file in Power BI, you’ll need to specify the file's location and set up your data import settings. Here’s a collaborative guide on the steps involved in establishing a data connection in Power BI.

  **Open the Power BI Desktop application.** 

  - Launched Power BI Desktop on the Computer.

  ![](https://github.com/Abdulquadri2025/Railway-Operational-Analysis/blob/main/First%20Page.png)

  **Get Data**

- Click on the “Blank report” tab in the Power BI Desktop.
- Click on the “Home” tab in the Power BI Desktop
- Select “Get Data” to initiate the Data import process.

  ![](https://github.com/Abdulquadri2025/Railway-Operational-Analysis/blob/main/To%20get%20Data.png)

  **Choose Excel and specify the File Location.**

- In the “Get Data” window, select “Excel Workbook” as the data source.
- Navigate to the location where the Excel file is stored.
- Select the Excel file you want to import and click “Open.”

  ![](https://github.com/Abdulquadri2025/Railway-Operational-Analysis/blob/main/To%20select%20from%20file.png)

  **Preview and Transform:**
  
- Select the Table to be inserted
- Power BI displayed a preview of the data from the Excel file.
- Review the data to ensure it is displayed correctly
- Click on transform data.

  ![](https://github.com/Abdulquadri2025/Railway-Operational-Analysis/blob/main/Transforming%20Data.png)


**Data Profiling Process**
  
  - Total Records: 31,653
	- Columns: 18
	- Missing Values:
	- Actual Arrival Time: ~6% missing
	- Reason for Delay: ~87% missing (only populated for delayed journeys)
	- Unique Values:
	- 12 Departure Stations
	- 32 Arrival Destinations
	- 3 Payment Methods
	- 3 Journey Status types (On Time, Delayed, Cancelled)
 
 **Data Modeling Techniques:**

Data modeling in Power BI plays a vital role in organizing and structuring data to establish meaningful relationships between different tables. By developing a well-designed data model, we can enhance the accuracy and insightfulness of our reports, ensuring they meet our objectives effectively.

![](https://github.com/Abdulquadri2025/Railway-Operational-Analysis/blob/main/Relationships.png)

Active relationships are created between tables by using common fields, or keys, and the relationship diagram is reviewed to confirm that all connections are accurately defined. In Power BI, an active relationship acts as the default link between tables, facilitating filtering and calculations. When establishing a relationship between two tables, Power BI automatically designates it as active unless specified otherwise. Typically, active relationships are essential for most calculations and visualizations, allowing for seamless data interactions and insights.

**Data Cleaning and Processing Procedures**

- Converted date/time fields to proper date time formats.
- Handled missing Actual Arrival Time values by tagging them as “Missing” for non-delayed journeys.
- Standardized categorical fields like payment methods, ticket classes, and delay reasons.
  
  **Created Columns**
  
Two columns were added to enhance the dataset and enable more detailed analysis. These new columns include:
  **Day Name:** This column represents the Day name on which revenue trends over time by day.
In Power BI, the Day Name Column was created on the sales table and obtained by creating a column that gives the day name.

DAX code for creating the Day Name column
			Day Name FORMAT= (Sales [Date],” DDD”)


  **Day Number:** This column represents the weekday number for which sales and revenue trends are reported by day number.
In Power BI, the Day Number Column was created on the sales table and obtained by creating a column that gives the Day Number.

DAX code for creating the Day Number column
			Day Number FORMAT= WEEKDAY (sales [Date]. [Date])


  **Created Measures**

The following measure was created using various DAX code to aid our analysis for better and more detailed results.
  **Total Profit:** This metric reflects the overall profit generated from each railway ticket. It was determined by multiplying the profit per ticket by the total quantities sold and summarizing the results in Power BI. This approach allows for a comprehensive view of ticket profitability.

DAX code for calculating Total Profit
	Total Profit=SUMX (‘sales’, ‘sales [unit]*RELATED (‘product’ [profit]))

**Data Analysis and Insights Gained**
 
**Delays:**
  - Most delays occurred on routes like London King's Cross → York, Manchester, → Birmingham.
	- Main delay reasons: Signal Failure, Weather, Technical Fault.
**Ticket Pricing:**
	- Price ranges from £1 to £267.
	- Average ticket price: ~£23.
	- Online purchases tend to have lower average ticket prices than in-store purchases.
**Refund Requests:**
	- ~3.5% of transactions involved refund requests.
	- Refunds are more likely on delayed or cancelled journeys.
**Popular Routes:**
	- Most traveled: Manchester Piccadilly → Birmingham New Street
	- Departure time peak: 08:00 - 10:00
**Payment Behavior:**
	- Most users pay via credit card, followed by contactless.
	- Rail card usage: 66% used a rail card, reducing the average price by ~20%.

**Data Visualization Strategies:**

![](https://github.com/Abdulquadri2025/Railway-Operational-Analysis/blob/main/DashBoard%201.png)

![](https://github.com/Abdulquadri2025/Railway-Operational-Analysis/blob/main/DashBoard%202.png)

**Recommendations for Improvement**

**Operational Efficiency:**
	- Investigate recurring issues at stations with high delay frequency.
	- Improve signal and rail infrastructure to reduce technical faults.
**Customer Communication:**
	- Provide real-time updates for high-delay routes.
	- Introduce delay-based compensation alerts.
**Sales Optimization:**
	- Promote rail card usage for customer retention.
	- Expand online ticketing incentives to reduce operational load at stations.

**Conclusion:**

The data reveals clear trends in journey behavior, delays, and pricing that can be leveraged to improve operations and customer satisfaction.
Thank You for Reading
I am keen on the data analyst role within an organization where I can contribute my skills effectively, embrace additional responsibilities, and continue to learn and grow. I aspire to be part of a team where my efforts can add significant value to the organization and where I can develop alongside it.
You can reach me at aregbeabdulquadri@gmail.com

**THANK YOU**



















  













