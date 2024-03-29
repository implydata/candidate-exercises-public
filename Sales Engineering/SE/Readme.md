<h1>Sales Engineering - Applicant Guide</h1>

<h2>Part A: Architecture and User Scenarios</h2>

<h3>Data Analytics Scenario:</h3>

Scenario: A retail e-commerce company wants to improve its customer retention. They have a massive dataset containing customer interactions, purchase history, and demographics. How would you design an analytics solution to identify key factors influencing customer churn and recommend strategies to reduce it? 

<h3>Data Engineering Scenario:</h3>

Scenario: A global manufacturing company needs to integrate data from multiple manufacturing plants worldwide, each with different data formats and systems. They also want to implement real-time monitoring of production data. How would you design an end-to-end data engineering solution to consolidate and process this data efficiently and provide real-time insights to plant managers?

<h3>Data Warehousing Scenario:</h3>

Scenario: A healthcare organization wants to create a centralized data warehouse to store patient records, medical images, and operational data from various hospitals and clinics. They require the ability to efficiently query patient history, support complex reporting, and ensure data security and compliance. How would you design the architecture and data model for this healthcare data warehouse?

<h3>Performance Optimization Scenario:</h3>

Scenario: A popular social media platform experiences significant performance issues with its analytics dashboard, which is slow and unresponsive during peak usage times. How would you address the performance bottlenecks and design an optimized architecture to ensure fast and scalable analytics for users and advertisers?

<h3>Big Data and Scaling Scenario:</h3>

- Scenario 1: A streaming video service wants to implement a recommendation engine that can handle the growing user base and data load. They have millions of users generating real-time data. How would you architect a scalable system that can process and analyze this data to provide personalized content recommendations efficiently?
  
- Scenario 2: A large social media site wants to provide more accurate counts of likes, views/impressions and shares of posts on their site. There can be thousands of such interactions on each post per second (especially if they are posts by popular celebraties). The site uses a batch process to update these counts at a global level, but would like to replace the current architecture with a more near real time architectue, with use of streaming technologies. How would you go about architecting this?

<h2>Part B: Coding Excerise </h2>

<h3>Simple:</h3>

There are three source files. **CityListA.json**, **CityListB.avro**, and **CityListC.csv**.
They each contain data in three columns:

  * name:string
  * code:string
  * Population:long

The goal is to combine the files, eliminating any duplicates and write to a single .CSV file sorted alphabetically by the city name. You can use any technology that you prefer.  The desired solution should be as generic, repeatable, and as automated as possible.  Once the dataset is completed, answer the following questions (and provide an explanation of how you determined your answer with any applicable code):
  1) What is the count of all rows?
  2) What is the city with the largest population?
  3) What is the total population of all cities in Brazil (CountryCode == BRA)?
  4) What changes could be made to improve your program's performance.
  5) How would you scale your solution to a much larger dataset (too large for a single machine to store)?

Your deliverable should be the following:

  * Your code to generate the dataset
  * A runbook with a guide on using your program
  * The dataset generated
  * Answers to the previous questions

<h3>Medium</h3>

Steps to execute:

1. Download the NY Yellow Taxi TLC trip record data for the last 12 months from here: https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page
2. Attempt the following SQL queries in your favourite database, datawarehouse, lake house or query engine:

    - **Total Trips**: Write an SQL query to calculate the total number of trips in the dataset.
    - **Average Fare Amount**: Calculate the average fare amount for all trips.
    - **Peak Hour Analysis**: Determine the hour of the day with the highest number of trips.
    - **Payment Type Analysis**: Find the most common payment type used by passengers.
    - **Longest Trip**: Identify the trip with the longest distance traveled.
    - **Revenue Analysis**: Calculate the total revenue generated by the taxi service, including fare amount and tips.
    - **Payment Type Distribution**: Determine the distribution of payment types for trips originating from each location (PULocationID).
    - **Tip Percentage**: Calculate the average tip percentage (tip_amount / total_amount) for each RatecodeID.
    - **Congestion Surcharge Analysis**: Find the average congestion surcharge for trips with more than one passenger.
    - **Airport Fee Analysis**: Analyze the distribution of airport fees for each VendorID.
    - **Passenger Count Impact**: Investigate how the number of passengers (passenger_count) affects the average fare amount.
    - **Monthly Revenue Trend**: Calculate the monthly revenue trend for the taxi service over the available data.
    - **Trip Count by Location**: Determine the top 10 pickup (PULocationID) and drop-off (DOLocationID) locations with the highest trip counts.
    - **Distance vs. Fare**: Analyze the relationship between trip_distance and fare_amount, and determine whether there's a correlation.
    - **Time Series Analysis**: Analyze the time series data for trip counts, fare amounts, or tip amounts, and identify any trends or seasonality.

**Please note that if you attempt this either with [Druid open source](https://druid.apache.org/docs/latest/tutorials/) or with [Imply Polaris](https://imply.io/imply-fully-managed-dbaas-polaris/), you will get additional brownie points during the evaluation.**

<h3>Complex</h3>

<<< TBD >>>

<h1>Part C: Case Study</h1>
In this exercise we will provide you with a set of customer requirements for Koala Maximization, Ltd. ("Koala" for short), the company that operates the popular web property http://koalastothemax.com/. Your goal will be to suggest how they can deploy Imply to best meet their needs.

<h2>Customer requirements</h2>
Koala has a dataset composed of visits to their web site, annotated with session ID, path visited, and attributes about the visitor like "city" and "browser". They want to build dashboards based on this dataset as well as be able to explore this dataset interactively.

An example data point for a single hit is below:

```
{
  "timestamp": "2016-08-04T18:05:07.054Z",
  "session": "S74650219",
  "remote_address": "172.31.3.170",
  "path": "http://www.koalastothemax.com/img/koalas3.jpg",
  "referrer": "Direct",
  "timezone_offset": "-120",
  "language": "it-IT",
  "city": "Borgo San Lorenzo",
  "region": "Province of Florence",
  "country": "Italy",
  "continent": "Europe",
  "latitude": 43.9555,
  "longitude": 11.3856,
  "browser": "Mozilla",
  "browser_version": "rv:11.0",
  "agent_type": "Browser",
  "agent_category": "Personal computer",
  "os": "Windows",
  "platform": "Windows"
}
```
This hit is part of the session "S74650219". The Koalas To The Max site gets roughly 200 million hits per day. Koala wants to load data in real-time and additionally store one year of historical data.

The most important kind of analysis Koala needs to do is counting how many unique sessions match certain parameters. For example, they need to answer queries like:

  * How many unique sessions were there last month?
  * How many unique sessions are there per day in each country?
  * Koala has one type of hardware available in its datacenter, with the following specs:

2x 8-core HT processors (16 cores total, 32 hardware threads)
64GB memory
600GB SSD disk

<h2>Presentation</h2>

Your challenge is to **present & demo** a recommendation for Koala hitting the following points:

  * How Imply can be used to answer the two sample queries provided by Koala (number of unique sessions in a particular month; number of unique sessions per country in a particular day).
  * How many servers will be necessary for an analytics cluster for one year of this dataset
  * (optional) How these servers should be configured (JVM config, Druid runtime.properties)

Some aspects of your recommendation will need to be based on guesswork. This is totally normal, even for a real pre-sales engagement! Whenever you are guessing, please point out what assumptions you made, and what additional information you would need in order to refine your guess.

<h2>Evaluation</h2>

Like the coding challenge, it is much more important to have a reasonable recommendation for each point that to have the best possible recommendation. We are not looking for perfection. Rather, we are looking for a good starting point that could be improved with more research.

Please include some details about how you arrived at the conclusions in your recommendation. This is even more important to us than the actual recommendations.

**Suggested resources**

You may find these resources helpful when putting together your recommendation:

**Imply documentation**:

Platform documentation at https://docs.imply.io/

Quickstart at https://docs.imply.io/on-prem/quickstart

Clustering documentation at https://docs.imply.io/on-prem/deploy/cluster

Sample configurations, available in the package at https://imply.io/get-started

**Druid documentation**:

Common configuration reference at http://druid.io/docs/latest/configuration/index.html

Broker configuration reference at http://druid.io/docs/latest/configuration/broker.html

Historical configuration reference at http://druid.io/docs/latest/configuration/historical.html

Indexing service configuration reference at http://druid.io/docs/latest/configuration/indexing-service.html
