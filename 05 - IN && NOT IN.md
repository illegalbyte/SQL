	SELECT name, city FROM customers WHERE city IN  ('San Diego', 'San Francisco', 'New York')
**IN** ➔ Instead of using a multitude of OR statements, we can use an IN statement.  

	SELECT name, city FROM customers WHERE city NOT IN  ('San Diego', 'San Francisco', 'New York')
**NOT IN** ➔ Works inversely to the IN statement.   