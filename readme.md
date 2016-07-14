1. How many users are there?

50

SELECT count(*) FROM users;

2. What are the 5 most expensive items?

    1.Small Cotton Gloves
    2. Small Wooden Computer
    3. Awesome Granite Pants
    4. Sleek Wooden Hat
    5. Ergonomic Steel Car

SELECT title FROM items ORDER BY price DESC LIMIT 5;
