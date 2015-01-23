	SELECT DISTINCT state FROM customers    
**DISTINCT** ➔ Removes all duplicate results from query  

	SELECT name, id FROM customers LIMIT 5   
**LIMIT** ➔ Limits the result to only first 5 IDs

	SELECT name, id FROM customers LIMIT 10, 2    
**LIMIT x, x**➔  Retrieves 2 pieces of data starting at ID 3. This is 0 indexed.
