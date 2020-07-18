<h1>Applicant Guide</h1>

<h2>Part A: Coding Excerise </h2>

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

<h2>Part B: Case Study</h2>
In this exercise we will provide you with a set of customer requirements for Koala Maximization, Ltd. ("Koala" for short), the company that operates the popular web property http://koalastothemax.com/. Your goal will be to suggest how they can deploy Imply to best meet their needs.

<h3>Customer requirements</h3>
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

<h3>Your recommendation</h3>
Your challenge is to write a recommendation for Koala hitting the following points:

  * How many servers will be necessary for an analytics cluster for one year of this dataset
  * How these servers should be configured (JVM config, Druid runtime.properties)
  * How Imply can be used to answer the two sample queries provided by Koala (number of unique sessions in a particular month; number of unique sessions per country in a particular day).

Some aspects of your recommendation will need to be based on guesswork. This is totally normal, even for a real customer engagement! Whenever you are guessing, please point out what assumptions you made, and what additional information you would need in order to refine your guess.

<h3>Evaluation</h3>

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
