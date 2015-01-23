### MYSQL 


``SELECT DISTINCT state FROM customers``  
**DISTINCT** ➔ Removes all duplicate results from query  

``SELECT name, id FROM customers LIMIT 5``  
**LIMIT** ➔ Limits the result to only first 5 IDs

``SELECT name, id FROM customers LIMIT 10, 2``  
**LIMIT x, x**➔  Retrieves 2 pieces of data starting at ID 3. This is 0 indexed.

``SELECT name FROM customers ORDER BY name``  
``SELECT name FROM customers ORDER BY id``
``SELECT name FROM customers ORDER BY state, name``     
**ORDER BY** ➔ Orders results alphabetically or numerically based on column given. Adding a second column allows for duplicates of the first entry to be sorted by the second's criteria.  
``SELECT name FROM customers ORDER BY id DESC``   
**ORDER BY x DESC** ➔ Orders results in descending order or, reverse alphabetical order.  
``SELECT id FROM customers ORDER BY id DESC LIMIT 1``  
**ORDER BY + LIMIT 1** ➔ Orders a list in descending order, but limits to 1 result. In abstract: retrieving the highest value. This would also work with alphabetical entries.  

``SELECT id, name FROM customers WHERE id>10``  
``SELECT id, name FROM customers WHERE id<10``  
``SELECT id, name FROM customers WHERE id<=10``  
``SELECT id, name FROM customers WHERE id>=10``  
``SELECT id, name FROM customers WHERE id!=10``  
``SELECT id, name FROM customers WHERE id=10``  
``SELECT id, name FROM customers WHERE name = 'Charlie Jones'``  
**WHERE** ➔ This allows basic expressions to be used in your query. Non numeric equality statements must be wrapped in quotes. 
``SELECT id, name FROM customers WHERE id BETWEEN 10 AND 20``  
**WHERE + BETWEEN** ➔ Allows you to define a range between two numbers.  
``SELECT id, city, state, name FROM customers WHERE state='MA' AND city='Boston'``  
**WHERE + AND** ➔ Equivalent to '&&' syntax.  
``SELECT id, city, state, name FROM customers WHERE state='MA' OR state='DC'``  
**WHERE + OR** ➔ Equivalent to '||' syntax.  
``SELECT id, city, name FROM customers WHERE (id=1 OR id=50) AND city='Rayleigh'``  
**WHERE + ()** ➔ For parsing your WHERE statements correctly.  

	SELECT name, city FROM customers WHERE city IN  ('San Diego', 'San Francisco', 'New York')
**IN** ➔ Instead of using a multitude of OR statements, we can use an IN statement.  

	SELECT name, city FROM customers WHERE city NOT IN  ('San Diego', 'San Francisco', 'New York')
**NOT IN** ➔ Works inversely to the IN statement.   

``SELECT name FROM items WHERE name LIKE 'new%'``  
``SELECT city FROM customers WHERE city LIKE 'h%d'``  
**LIKE + %** ➔ Returns all names that start with new%. '%' is a wildcard in this case. This statement is not case-sensitive.  
``SELECT state FROM customers WHERE state LIKE '_L'``   
**LIKE + \_** ➔ The '\_' wildcard specifies a single character wildcard.   


``SELECT name FROM items WHERE name REGEXP 'new'``  
**REGEXP** ➔ Allows for a regular expression to be used.  


``SELECT CONCAT(city, ', ', state) AS address FROM customers``  
**CONCAT()** ➔ Creates a new collumn called 'address' with the pattern ''city, state".

``SELECT name, cost, cost-1 AS discount_price FROM items``  
**SELECT + MATH** ➔ Allows you to create a new column called discount_price that has all the values in cost but with 1 subtracted.  

``UPPER(name)``   
➔ Uppercase function.   
``SQRT(cost) AS square_root``  
➔ Sqrt() gets the square root.  
``SELECT AVG(cost) AS average_cost FROM items``   
➔ Avg() gets the average.   
``SELECT SUM(bids) AS bids FROM items``  
➔ Sum() adds all numbers in a column.  
``SELECT COUNT(name) FROM items WHERE seller_id = 6``  
➔ Counts how many items seller6 is selling.  
``SELECT COUNT(*) AS item_count,
MAX(cost) AS max
FROM items WHERE seller_id = 12``  
➔ How to use multiple aggregate functions, and MAX()/MIN() which return the highest/lowest number, respectively. 
**FUNCTIONS**  

``SELECT seller_id, COUNT(*) AS item_count FROM items GROUP BY seller_id``  
**GROUP BY** ➔ Similar to a WHERE statement but it covers all the values. The above use-case retrieves all the seller_ids and shows their item_count.  

	SELECT seller_id, COUNT(*) AS item_count FROM items GROUP BY seller_id HAVING item_count>2 ORDER BY item_count DESC  
**HAVING** ➔ HAVING is similar to WHERE, but for GROUPS.  

	SELECT name, cost FROM items WHERE cost>(	
		SELECT AVG(cost) FROM items
	) ORDER BY cost DESC  
**Subqueries** ➔ Wrap a query within a query in brackets. The above example retrieves all the items that cost more than the average price (and then orders them in DESC).  


	SELECT name, MIN(cost) FROM items WHERE name LIKE '%boxes' AND seller_id IN (
		SELECT seller_id FROM items WHERE name LIKE '%boxes'
	)
**Subqueries 2** ➔ A more useful example that incorporates the IN operator to limit our search to only those sellers that are actually selling boxes.

	SELECT customers.id, customers.name, items.name, customers.state 
	FROM customers, items
	WHERE customers.id=seller_id
	ORDER BY customers.id
**Join tables** ➔ Joining two tables together in a query output. The third line is important because it shows how the two tables are related (in this case it is their key values).   

	SELECT customers.name, items.name FROM customers
	LEFT OUTER JOIN items ON customers.id=seller_id
**LEFT/RIGHT OUTER JOIN** ➔ Takes the table left of the word 'LEFT' or 'RIGHT' (in this case customers) and joins it regardless of whether it has any values or not. So the above statement shows all users/customers, even if they aren't selling anything.  

	SELECT name, cost, bids FROM items WHERE bids >100
	UNION
	SELECT name, cost, bids FROM items WHERE cost >200  
**UNION** ➔ This simple keyword joins a two queries' results into one data set. If you did the above without union, the query would effectively be run twice and give you two datasets. Useful for complex filtering. *NOTE:* When using unions, your columns must be the **same** for both queries.  

	SELECT name, cost, bids FROM items WHERE bids >100
	UNION ALL
	SELECT name, cost, bids FROM items WHERE cost >200
**UNION ALL** ➔ Allows you to 

	ALTER TABLE items ADD FULLTEXT(name)
**ADD FULLTEXT()** ➔ Enables full text searching on a table column. 

	SELECT name, cost FROM items WHERE Match(name) Against("car")
**Fulltext search** ➔ Faster than other search queries. 'Search engine' like behaviour. (faster than LIKE and REGEXP).  


	SELECT name, cost FROM items WHERE Match(name) Against("-car +box" IN BOOLEAN MODE)
**IN BOOLEAN MODE** ➔ Enables google dork like operators to the search statement your matching Against().   

	INSERT INTO items VALUES('101','WD HD','300','1','0')
**INSERT INTO** ➔ Finally, what you've been waiting for. A way of inputting data to the database. 

	INSERT INTO items(id,name,cost,seller_id, bids) VALUES(101,'WD22','10','1','0')
**Specifying input order** ➔ By using items(x,x,x,x) we have specified the order of the data that we will be inputting using VALUES. Despite any changes to the table's order, this will still function properly.  

***Default** value for **numbers** is **0***   
***Default** value for **strings** is **'null'***  

	INSERT INTO items(id,name,cost,seller_id, bids) VALUES (101,'WD22','10','1','0'),
	(102,'WD21','12','1','0'),
	(103,'WD23','10','1','0')
**Multiple INSERTs** ➔ How to input mutiple VALUES using brackits and commas. 

	INSERT INTO items(id, name, cost, seller_id, bids) SELECT id, name, cost, seller_id, bids FROM anothertable 
**INSERT INTO + SELECT** ➔ If you wanted to merge two tables - that had the same structure - together.

	UPDATE items set name='cardboard box' WHERE name='box'
**UPDATE .. WHERE** ➔ Edits the value of a column based on a WHERE statement. 

	UPDATE items SET name='red box', bids='2' WHERE id=10 
**UPDATE multiple columns in same row** ➔ Self explanatory... Just separate the SET expressions with commas. 

	DELETE FROM items WHERE name='cardboard box'
**DELETE** ➔ Allows you to delete rows. 

	CREATE TABLE users(
	id int, 
	username varchar(30),
	password varchar(60),
	PRIMARY KEY(id)
	)
**CREATE TABLE** ➔ Create a freaking table! PRIMARY KEY(x) specifies which column is the primary key. 

	CREATE TABLE users(
	id int NOT NULL AUTO_INCREMENT, 
	username varchar(30) NOT NULL,
	PRIMARY KEY(id)
	)
**NOT NULL** ➔ Specifies that your table column cannot be empty (aka NULL).   
**AUTO_INCREMENT** ➔ Automatically increases by 1 every time a new row is made. 


	ALTER TABLE users ADD email varchar(60)
**ALTER TABLE + ADD** ➔ Add a column to your table.

	ALTER TABLE users DROP COLUMN email 
**DROP COLUMN** ➔ Delete a column from your table

	DROP TABLE users
**DROP TABLE** ➔ Deletes a table. 

	RENAME TABLE customers TO old_customers
**RENAME TABLE x TO y** ➔ Rename a table. 

	CREATE VIEW mostbids AS
	SELECT id, name, bids FROM items ORDER BY bids DESC LIMIT 10
**CREATE VIEW** ➔ A view is basically like a saved search, but appears to be a table of data. 

	SELECT name, bids FROM mostbids
**Query VIEW** ➔ Views can be queried just like tables. 

	CREATE VIEW addresses AS
	SELECT Concat(city, ' ', state) AS address FROM customers
**CREATE VIEW** ➔ Another example. 

