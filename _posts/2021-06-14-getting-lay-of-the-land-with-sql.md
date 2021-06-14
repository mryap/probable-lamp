SQL is becoming a common skill requirement across industries.

Employers require their data analysts, data scientists and product managers (or anyone handling data) to at least be familiar with SQL. 
This is because SQL remains the language of data. So, in order to be data driven, people need to know how to access and analyze data.

One way to handle data is 'point and click'. For that to happen, Jira ticket need to be raised to seek developer resources to build the user interface layer on top of the datasets. 

Even if there is a detail documentation, I always wants to get a lay of the land like

- list tables in bigquery dataset with sql

Such as 
```
SELECT * 
FROM publicdata.samples.__TABLES__
WHERE starts_with(table_id, 'github') 
```
Note that data tables in BigQuery are template-suffix based. i.e. `bigquery-public-data.bbc_news.fulltext`

- How large are the tables within a given dataset?


![]({{site.baseurl}}/images/Screenshot_2021-06-14 SQL workspace – BigQuery – Cohort Analysis – Google Cloud Platform.png)

