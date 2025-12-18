# Capstone-project
Using AWS services a I fully completed the Capstone project.

The Capstone Project

The main goal of this capstone project was to build a complete data engineering solution using various AWS services to 
analyze fisheries data. Specifically, I needed to:

1. Set up a development environment using AWS Cloud9
2. Process and transform data from CSV format to Apache Parquet format
3. Create data infrastructure using S3, AWS Glue, and Athena
4. Analyze fishing data from different ocean areas
5. Build queries and views to extract meaningful insights about fishing patterns

I worked with three main data files: SAU-GLOBAL-1-v48-0.csv, SAU-HighSeas-71-v48-0.csv and SAU-EEZ-242-v48-0.csv.

Firstly, I set up a development environment using AWS Cloud9.
![Environment](Picture1.png)

Then I made two S3 Bucket, namely data-source-11144 and query-source-11144. This way I prepaired the storage place.
 ![Buckets](Picture2.png)

In order to get the data, I used the Cloud9 environment's terminal. I downloaded them using 3 commands such as:
 ![code](Picture3.png)


Now all the 3 datasets are available for me to analyze and examine the data structure using head and wc commands.

  ![code](Picture4.png)
   ![code](Picture5.png)
 


To have these in my already created S3 Bucket, I will convert the 2 csv-s (SAU-GLOBAL-1-v48-0.csv, SAU-HighSeas-71-v48-0.csv) 
into parquet format and upload it to the right place.

  ![code](Picture6.png)
  
  ![code](Picture7.png)
  
  ![code](Picture8.png)
 
 

In the next step, I created a database called fishdb manually and filled the table with the 2 files using AWS Glue Crawler called fishcrawler.
 
 ![code](Picture9.png)

Now I have metadata about my 2 dataset and I can see the schema of it.

Then I configured Athena to output query results to the query-source-11144 bucket.
I run several queries to check my table's data. I created a challenge view and a MackerelsCatch view as well.
 
  ![code](Picture10.png)
  
  ![code](Picture11.png)
  
  ![code](Picture12.png)
  
  ![code](Picture13.png)
 
 

The query gives Fiji’s yearly open-sea revenue since 2001. It bounces around 65–70 million USD, with no clear up or down trend. Biggest dips were 2003 and 2010; peaks in 2004 and 2017.



But I have only two csv-s' data, so I need to add the 3rd one using Cloud9 terminal in the same way as I did in the other cases.
 
 ![code](Picture14.png)
 
I needed to rename two columns before the usual formatting and uploading.

 ![code](Picture15.png)
 
 ![code](Picture16.png)
 

Then I reran the queries to have all the data needed.

 ![code](Picture17.png)


Now I can see 3 results instead of only 2, it means I successfully added the data.
 
 ![code](Picture18.png)
 
 ![code](Picture19.png)
 

I got the result that the USA dominates with around 860 t, followed by Fiji with 602 t, the rest territories are under 130 t.
Geographic spread is wide (East Asia, Pacific islands, USA), but “Unknown Fishing Country” appears, indicating data-quality gaps.

  ![code](Picture20.png)
  
  ![code](Picture21.png)
  
  ![code](Picture22.png)
 
 

I can see the maximum fishing commerce in each year where the country is China. The Pacific, Western Central has the greatest amount.

I wrote further 3 queries:


Query 1:
![code](Picture23.png)

![code](Picture24.png)


The query shoes that Indonesia makes the most money from fishing by the checking the total catch value, followed by China and Japan. It is understandable since these are arounded by sea. 

Query 2:
 ![code](Picture25.png)
 
 ![code](Picture26.png)
 
We can see the total value and total tonnes by the year and ocean area. For example, in 2000 open seas has 198 countries fishing, while Fiji EEZ has 18 countries. I can see the total tonnes and value of these as well in each year.
This ratio can be seen in the other years as well meaning the international waters are a way busier. 


Query 3:
 ![code](Picture27.png)
 
 ![code](Picture28.png)
 
I wanted to check the number of species and the total tonnes in each country. Fiji catches the most variety of fish (67 different types) even though it is a small country. Big countries like 
Japan focuses on fewer types but much larger quantities.



Conclusion:

Overall, with this project I successfully uploaded 3 CSV files to AWS Cloud and analyzed them using Athena, building a complete data solution 
that processes fisheries data and generates meaningful insights about global fishing trends.



