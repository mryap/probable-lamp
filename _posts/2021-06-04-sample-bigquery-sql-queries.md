
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
