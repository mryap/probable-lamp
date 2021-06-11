---
toc:true- branch: master- badges: true- comments: true
layout: post
categories: [bigquery, fastpages]
title: Sample BigQuery sql queries
author: Yap Shiao Shyan
---


The [dataset](https://accounts.google.com/ServiceLogin/signinchooser?service=cloudconsole&passive=1209600&osid=1&continue=https%3A%2F%2Fconsole.cloud.google.com%2Fbigquery%3Fp%3Dbigquery-public-data%26d%3Dgoogle_analytics_sample%26t%3Dga_sessions_20170801%26page%3Dtable%26ref%3Dhttps%3A%2F%2Fconsole.cloud.google.com%2Fmarketplace%2Fproduct%2Fobfuscated-ga360-data%2Fobfuscated-ga360-data%3Fproject%253Dlexical-script-761%2526login%253Dtrue%2526ref%253Dhttps%3A%25252F%25252Fsupport.google.com%25252F&followup=https%3A%2F%2Fconsole.cloud.google.com%2Fbigquery%3Fp%3Dbigquery-public-data%26d%3Dgoogle_analytics_sample%26t%3Dga_sessions_20170801%26page%3Dtable%26ref%3Dhttps%3A%2F%2Fconsole.cloud.google.com%2Fmarketplace%2Fproduct%2Fobfuscated-ga360-data%2Fobfuscated-ga360-data%3Fproject%253Dlexical-script-761%2526login%253Dtrue%2526ref%253Dhttps%3A%25252F%25252Fsupport.google.com%25252F&flowName=GlifWebSignIn&flowEntry=ServiceLogin) provides 12 months (August 2016 to August 2017) of obfuscated Google Analytics 360 data from the Google Merchandise Store, a real ecommerce store that sells Google-branded merchandise, in BigQuery. It’s a great way analyze business data and learn the benefits of using BigQuery to analyze Analytics 360 data 

![]({{site.baseurl}}/images/Screenshot_2021-06-05 SQL workspace – BigQuery – 2021 – Google Cloud Platform.png)

## Average number of transactions per purchaser for July 2017
What is the average number of transactions per purchaser?
Calculate the average number of transactions per purchaser for July 2017. 

```
SELECT
  (SUM (total_transactions_per_user) / COUNT(fullVisitorId) ) AS avg_total_transactions_per_user
FROM (
  SELECT
    fullVisitorId,
    SUM (totals.transactions) AS total_transactions_per_user
  FROM
    `bigquery-public-data.google_analytics_sample.ga_sessions_*`
  WHERE
    _TABLE_SUFFIX BETWEEN '20170701'
    AND '20170731'
    AND totals.transactions IS NOT NULL
  GROUP BY
    fullVisitorId )
```
## Total number of transactions generated per device browser
What is the total number of transactions generated per device browser?
Identify the top 5 browsers used for making transactions in July 2017, listed in descending order by total transactions.

```
SELECT
  device.browser,
  SUM ( totals.transactions ) AS total_transactions
FROM
  `bigquery-public-data.google_analytics_sample.ga_sessions_*`
WHERE
  _TABLE_SUFFIX BETWEEN '20170701'
  AND '20170731'
GROUP BY
  device.browser
ORDER BY
  total_transactions DESC
```
[Share query URL on BigQuery](https://console.cloud.google.com/bigquery?sq=416461284595:33e0e2cdec00434285d6717f9f555a4b)

## find out the first time each customer visited the site 
```
select
  extract(date from timestamp_seconds(min(visitStartTime))) as cohort_month,
  fullVisitorId
from `bigquery-public-data.google_analytics_sample.ga_sessions_*`
group by fullVisitorId
```
[Share query URL on BigQuery](https://console.cloud.google.com/bigquery?sq=416461284595:dcdee4c6233848018c8c33d0f2f57822)

