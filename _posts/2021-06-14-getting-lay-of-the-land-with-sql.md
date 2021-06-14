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

[A sql qeury link you can access to](
https://console.cloud.google.com/bigquery?sq=948256378521:df2fcf4476e24af78b7bfd619370349d
)

### Querying table metadata in Google BigQuery?

A term for what I am doing is known as Querying table metadata in Google BigQuery

When it comes to query table metadata, there are many potential solutions, ranging from simple view in Google Cloud Console to more Python's [client libraries](https://mryap.github.io/probable-lamp/bigquery/python/2021/06/12/check-dataset-existence-bigquery.html).  

Imagine you given access to a huge dataset containing many tables in BigQuery
- How do you identify which tables are the most updated? 
- When was each table created? 
- What columns are present in each table? 

All of these questions can be answered with metadata.

