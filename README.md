

# Capstone Project - Fisheries Data Engineering with AWS

## Project Overview

Using AWS services, I fully completed the Capstone project. The main goal was to build a complete data engineering solution using various AWS services to analyze fisheries data. Specifically, I needed to:

1. Set up a development environment using AWS Cloud9
2. Process and transform data from CSV format to Apache Parquet format  
3. Create data infrastructure using S3, AWS Glue, and Athena
4. Analyze fishing data from different ocean areas
5. Build queries and views to extract meaningful insights about fishing patterns

I worked with three main data files: SAU-GLOBAL-1-v48-0.csv, SAU-HighSeas-71-v48-0.csv and SAU-EEZ-242-v48-0.csv.

## Implementation Steps

### Environment Setup

Firstly, I set up a development environment using AWS Cloud9. This gave me a cloud-based IDE with all the tools I needed to work with AWS services efficiently.

![Environment](Picture1.png)

### Data Storage Preparation

Then I made two S3 buckets, namely data-source-11144 and query-source-11144. This way I prepared the storage place for my datasets and query results separately.

![Buckets](Picture2.png)

### Data Acquisition

In order to get the data, I used the Cloud9 environment's terminal. I downloaded them using 3 commands as shown below:

![Data Download](Picture3.png)

Now all the 3 datasets are available for me to analyze and examine the data structure using head and wc commands.

![Data Exploration](Picture4.png)
![Data Statistics](Picture5.png)

### Data Format Conversion

To have these in my already created S3 bucket, I converted the 2 csv files (SAU-GLOBAL-1-v48-0.csv, SAU-HighSeas-71-v48-0.csv) into parquet format and uploaded it to the right place. This conversion helps with better query performance and storage efficiency.

![Parquet Conversion](Picture6.png)
![Data Processing](Picture7.png)
![File Upload](Picture8.png)

### Database Schema Creation

In the next step, I created a database called fishdb manually and filled the table with the 2 files using AWS Glue Crawler called fishcrawler.

![Database Creation](Picture9.png)

Now I have metadata about my 2 datasets and I can see the schema of it.

### Query Configuration

Then I configured Athena to output query results to the query-source-11144 bucket. I ran several queries to check my table's data. I created a challenge view and a MackerelsCatch view as well.

![Query Testing](Picture10.png)
![Result Validation](Picture11.png)
![View Creation](Picture12.png)
![Data Validation](Picture13.png)

### First Analysis Results

The query gives Fiji's yearly open-sea revenue since 2001. It bounces around 65–70 million USD, with no clear up or down trend. Biggest dips were 2003 and 2010; peaks in 2004 and 2017.

![Economic Analysis](Picture14.png)

This shows me that Fiji's fishing revenue is quite volatile and affected by various external factors like global economic conditions, fish stock variations, and possibly environmental changes.

### Adding the Third Dataset

But I have only two csv files' data, so I needed to add the 3rd one using Cloud9 terminal in the same way as I did in the other cases.

![Third Dataset Download](Picture15.png)

I needed to rename two columns before the usual formatting and uploading to ensure consistency across all datasets.

![Column Renaming](Picture16.png)
![Data Processing](Picture17.png)

Then I reran the queries to have all the data needed.

### Comprehensive Analysis Results

Now I can see 3 results instead of only 2, it means I successfully added the data.

![Multi-dataset Results](Picture18.png)
![Geographic Distribution](Picture19.png)

I got the result that the USA dominates with around 860 t, followed by Fiji with 602 t, the rest territories are under 130 t. Geographic spread is wide (East Asia, Pacific islands, USA), but "Unknown Fishing Country" appears, indicating data-quality gaps.

This is interesting because it shows me that despite being a small island nation, Fiji plays a significant role in global fishing, especially in the Pacific region.

### Maximum Fishing Commerce Analysis

I can see the maximum fishing commerce in each year where the country is China. The Pacific, Western Central has the greatest amount.

![Commerce Analysis](Picture20.png)
![Pattern Analysis](Picture21.png)
![Yearly Trends](Picture22.png)

### Additional Analytical Queries

I wrote further 3 queries to get more insights:

#### Query 1: Economic Performance Analysis

![Economic Query](Picture23.png)
![Economic Results](Picture24.png)

The query shows that Indonesia makes the most money from fishing by checking the total catch value, followed by China and Japan. It is understandable since these are surrounded by sea and have extensive coastlines for fishing operations.

This makes perfect sense as these countries have both the geographic advantages and the economic investment in modern fishing fleets and processing facilities.

#### Query 2: Temporal and Spatial Analysis

![Temporal Analysis](Picture25.png)
![Pattern Results](Picture26.png)

We can see the total value and total tonnes by the year and ocean area. For example, in 2000 open seas has 198 countries fishing, while Fiji EEZ has 18 countries. I can see the total tonnes and value of these as well in each year. This ratio can be seen in the other years as well meaning the international waters are a way busier.

This tells me that international waters attract much more fishing activity than exclusive economic zones, which makes sense given the regulatory differences and the vastness of open ocean areas.

#### Query 3: Species Diversity Analysis

![Diversity Analysis](Picture27.png)
![Diversity Results](Picture28.png)

I wanted to check the number of species and the total tonnes in each country. Fiji catches the most variety of fish (67 different types) even though it is a small country. Big countries like Japan focuses on fewer types but much larger quantities.

This is fascinating because it shows how small island nations can compete by specializing in diverse species while larger nations might focus on high-volume production of specific fish types for maximum efficiency.


## Conclusion

Overall, with this project I successfully uploaded 3 CSV files to AWS Cloud and analyzed them using Athena, building a complete data solution that processes fisheries data and generates meaningful insights about global fishing trends.

