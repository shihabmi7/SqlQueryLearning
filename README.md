# Sample Database schema & SQL Query for MSSQL Server

This DB schema is provided by www.sqlservertutorial.net for Learning MSSQL Server. 

This is for practicing common queries. 

# Select

Key word DISTINCT removes the duplicates
```SQL
SELECT DISTINCT
    city
FROM
    sales.customers
ORDER BY
    city;
```


# Aggregate Function

```SQL
SELECT category_id, AVG(list_price) as avg_price_for_this_cat
  FROM [BikeStores].[production].[products]
  where category_id !=1
  group by category_id
```

```SQL 
SELECT category_id, AVG(list_price) as avg_price_for_this_cat
  FROM [BikeStores].[production].[products]
  group by category_id
  having AVG(list_price) > 3000
```

```SQL 
SELECT 
	SUM(list_price) as sum,
	avg(list_price) as avg,
	MAX(list_price) as high_price,
	min(list_price) as min_price
FROM [BikeStores].[sales].[order_items]
```

```SQL 
SELECT count(*) as row_count
  FROM [BikeStores].[sales].[order_items]

```

The following example returns the city in California which has more than ten customers:

```SQL 
SELECT
    city,
    COUNT (*)
FROM
    sales.customers
WHERE
    state = 'CA'
GROUP BY
    city
HAVING
    COUNT (*) > 10
ORDER BY
    city;
````

# Join

## Inner Join

```SQL 
SELECT product_name, model_year, brand_name, category_name
  FROM [BikeStores].[production].[products] as p
  Inner Join [BikeStores].[production].brands as b
  on p.brand_id = b.brand_id
  inner join [BikeStores].[production].categories as c
  on p.category_id  = c.category_id

```
## Left Outer Join

```SQL 
SELECT *
  FROM [BikeStores].[sales].[stores] as s
  left outer join  [BikeStores].[sales].staffs as st
  on s.store_id = st.store_id
```

## Right Outer Join 

```SQL 
SELECT *
  FROM [BikeStores].[sales].[staffs] s
  right outer join [BikeStores].[sales].stores st
  on s.store_id = st.store_id

```

