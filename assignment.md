# Assignment

## Brief

Write the SQL DML statements for the following questions.

## Instructions

Paste the answer as SQL in the answer code section below each question.

### Question 1

Select the minimum and maximum price per sqm of all the flats.

```sql
SELECT
    MIN(resale_price / floor_area_sqm) AS min_price_per_sqm,
    MAX(resale_price / floor_area_sqm) AS max_price_per_sqm
FROM
    resale_flat_prices_2017;
```

### Question 2

Select the average price per sqm for flats in each town.

```sql
SELECT
	town, AVG(resale_price / floor_area_sqm) AS price_per_sqm,
FROM
    resale_flat_prices_2017
GROUP BY town;
```

### Question 3

Categorize flats into price ranges and count how many flats fall into each category:

- Under $400,000: 'Budget'
- $400,000 to $700,000: 'Mid-Range'
- Above $700,000: 'Premium'
  Show the counts in descending order.

```sql
SELECT
    CASE
        WHEN resale_price < 400000 THEN 'Budget'
        WHEN resale_price <= 700000 THEN 'Mid-Range'
        ELSE 'Premium'
    END AS price_category,
    COUNT(*) AS number_of_flats
FROM
    resale_flat_prices_2017
GROUP BY
    price_category
ORDER BY
	price_category;
```

### Question 4

Count the number of flats sold in each town during the first quarter of 2017 (January to March).

```sql
-- Included Month for fun
SELECT
    town, month,
    COUNT(*) AS number_of_flats_sold
FROM
    resale_flat_prices_2017
WHERE
    month BETWEEN '2017-01' AND '2017-03'
GROUP BY
    town, month
ORDER BY town, month;
```

## Submission

- Submit the URL of the GitHub Repository that contains your work to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
