	SELECT customers.id, customers.name, items.name, customers.state 
	FROM customers, items
	WHERE customers.id=seller_id
	ORDER BY customers.id
**Join tables** ➔ Joining two tables together in a query output. The third line is important because it shows how the two tables are related (in this case it is their key values).   

	SELECT customers.name, items.name FROM customers
	LEFT OUTER JOIN items ON customers.id=seller_id
**LEFT/RIGHT OUTER JOIN** ➔ Takes the table left of the word 'LEFT' or 'RIGHT' (in this case customers) and joins it regardless of whether it has any values or not. So the above statement shows all users/customers, even if they aren't selling anything.  
