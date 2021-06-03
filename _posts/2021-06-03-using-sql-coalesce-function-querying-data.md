A Null value is a field with no value.

The Coalesce SQL function returns first non-null expression among its arguments. Null plus anything equals zero and it like zero times anything equals zero. 
For example, when we have to combine e.g. a street name with a postal code, additional address line, etc. 
If one of those has a Null value, the whole thing is going to be Null.

As a data analyst, you will end up with a dataset that has some nulls that you'd prefer to contain actual values. This happens frequently in numerical data (displaying nulls as 0 is often preferable), and when performing outer joins can result in some unmatched rows.

If there is no NULL value, then the first value is returned:
```
SELECT COALESCE('A', 'B', 'C') AS result

```
The output will be A

If there is a NULL value then the first non-null value is returned:
```
SELECT COALESCE(NULL, NULL, 'C') AS result
```
The output will be C

## BigQuery

## PostgregSQL

In PostgreSQL, COALESCE is a system in-built function that can be considered one of the conditional expressions available.
Checkout how to use `COALESCE` in `PostgreSQL` at https://www.enterprisedb.com/postgres-tutorials/how-use-coalesce-postgresql

## SaaS
