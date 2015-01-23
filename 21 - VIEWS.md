	CREATE VIEW mostbids AS
	SELECT id, name, bids FROM items ORDER BY bids DESC LIMIT 10
**CREATE VIEW** ➔ A view is basically like a saved search, but appears to be a table of data. 

	SELECT name, bids FROM mostbids
**Query VIEW** ➔ Views can be queried just like tables. 

	CREATE VIEW addresses AS
	SELECT Concat(city, ' ', state) AS address FROM customers
**CREATE VIEW** ➔ Another example. 

