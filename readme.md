**How many users are there?**
<br>50

`SELECT COUNT(*) FROM users;`

---
**What are the 5 most expensive items?**
1. Small Cotton Gloves
2. Small Wooden Computer
3. Awesome Granite Pants
4. Sleek Wooden Hat
5. Ergonomic Steel Car

`SELECT title FROM items ORDER BY price DESC LIMIT 5;`

---
**What's the cheapest book?**
<br> Ergonomic Granite Chair

`SELECT title FROM items WHERE category LIKE '%book%' ORDER BY price;`

**Does that change for "category is exactly 'book'" versus "category contains 'book'"?**
<br>No

`SELECT title FROM items WHERE category = 'Books' ORDER BY price;`

---

**Who lives at "6439 Zetta Hills, Willmouth, WY"?**
<br> Corrine Little

`SELECT users.first_name, users.last_name FROM users INNER JOIN addresses WHERE addresses.user_id = users.id AND addresses.street = '6439 Zetta Hills';`



**Do they have another address?**
<br>54369 Wolff Forges Lake Bryon, CA

`SELECT addresses.street, addresses.city, addresses.state FROM users INNER JOIN addresses WHERE addresses.user_id = users.id AND users.first_name = 'Corrine' AND users.last_name = 'Little';`

---

**Correct Virginie Mitchell's address to "New York, NY, 10108".**

`UPDATE addresses SET city = 'New York', zip = '10108' WHERE state = 'NY' AND user_id IN (SELECT id FROM users WHERE first_name = 'Virginie' AND last_name = 'Mitchell');`

---

**How much would it cost to buy one of each tool?**
<br>$46,477

`SELECT SUM(price) FROM items WHERE category LIKE '%tools%';`

---

**How many total items did we sell?**
<br>2,125

`SELECT SUM(quantity) FROM orders;`

---

**How much was spent on books?**
<br>$1,081,352

`SELECT SUM(items.price * orders.quantity) FROM items INNER JOIN orders WHERE orders.item_id = items.id AND items.category LIKE '%Book%';`

---

**Simulate buying an item by inserting a User for yourself and an Order for that User.**

`INSERT INTO users (first_name, last_name, email) VALUES ('Amber', 'Smith', 'smithambera@gmail.com');`

`INSERT INTO orders VALUES (null, 51, 66, 6, datetime());`
