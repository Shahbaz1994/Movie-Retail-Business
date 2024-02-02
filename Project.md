### Task 1: Compile a comprehensive list of staff members, including their first and last names, email addresses, and store identification numbers.

```
SELECT 
	first_name, 
    last_name, 
	email, 
    store_id
FROM staff;
```
| first_name | last_name | email                           | store_id |
|------------|-----------|---------------------------------|----------|
| Mike       | Hillyer   | Mike.Hillyer@sakilastaff.com    | 1        |
| Jon        | Stephens  | Jon.Stephens@sakilastaff.com     | 2        |

### Task 2: Obtain separate counts of inventory items for each of the two stores.

```
SELECT 
	store_id, 
	COUNT(inventory_id) AS inventory_items
FROM inventory
GROUP BY 
	store_id;
```
| store_id | inventory_items |
|----------|------------------|
| 1        | 2270             |
| 2        | 2311             |


### Task 3: Compile separate counts of active customers for each store.

```
SELECT 
	store_id, 
    COUNT(customer_id) AS active_customers
FROM customer
WHERE active = 1
GROUP BY 
	store_id;
```
| store_id | active_customers |
|----------|-------------------|
| 1        | 318               |
| 2        | 266               |

### Task 4: Evaluate data breach liability by generating a count of all customer email addresses stored in the database.

```
SELECT 
	COUNT(email) AS emails
FROM customer;
```

| email |
|-------|
| 599   |

### Task 5: Assess the diversity of the film inventory for future customer engagement. Provide counts of unique film titles and unique film categories at each store.

```
SELECT 
	store_id, 
    COUNT(DISTINCT film_id) AS unique_films
FROM inventory
GROUP BY 
	store_id; 
	
SELECT 
	COUNT(DISTINCT name) AS unique_categories
FROM category;
```
| store_id | unique_films |
|----------|--------------|
| 1        | 759          |
| 2        | 762          |

| unique_categories |
|-------------------|
| 16                |

### Task 6: Evaluate film replacement costs to provide the least expensive, most expensive, and average replacement cost for all films in inventory.
```
SELECT 
	MIN(replacement_cost) AS least_expensive, 
    MAX(replacement_cost) AS most_expensive, 
    AVG(replacement_cost) AS average_replacement_cost
FROM film;
```
| least_expensive | most_expensive | average_replacement_cost |
|-----------------|----------------|---------------------------|
| 9.99            | 29.99          | 19.984000                 |

### Task 7: Implement payment monitoring systems and maximum payment processing restrictions to mitigate the risk of fraud by staff. Provide the average payment processed and the maximum payment processed for enhanced security measures.
```
SELECT
	AVG(amount) AS average_payment, 
    MAX(amount) AS max_payment
FROM payment;
```
| average_payment | max_payment |
|-----------------|-------------|
| 4.200667        | 11.99       |

### Task 8: Enhance understanding of the customer base by providing a list of all customer identification values, along with a count of all-time rentals. Present the list with the highest volume customers at the top.
```
SELECT 
	customer_id, 
    COUNT(rental_id) AS number_of_rentals
FROM rental
GROUP BY 
	customer_id
ORDER BY 
	COUNT(rental_id) DESC;
```
| customer_id | number_of_rentals |
|-------------|-------------------|
| 148         | 46                |
| 526         | 45                |
| 144         | 42                |
| 236         | 42                |
| 75          | 41                |

